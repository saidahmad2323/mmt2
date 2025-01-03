<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Вопросы и ответы</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f3f4f6;
            color: #333;
        }
        #main-screen {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            height: auto;
        }
        #search-input {
            padding: 15px;
            font-size: 16px;
            border: 1px solid #ccc;
            border-radius: 8px;
            width: calc(100% - 40px);
            max-width: 400px;
            margin-bottom: 20px;
        }
        #qa-container {
            margin: 20px;
            max-width: 600px;
            width: 100%;
            max-height: calc(100vh - 200px);
            overflow-y: auto;
            padding: 10px;
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .question {
            font-weight: bold;
            font-size: 18px;
            margin-top: 20px;
            padding-left: 10px;
            color: #007bff;
        }
        .answers {
            margin-left: 15px;
            list-style-type: disc;
            color: #555;
        }
    </style>
</head>
<body>
    <div id="main-screen">
        <h1>English</h1>
        <input type="text" id="search-input" placeholder="Введите текст для поиска...">
        <div id="qa-container"></div>
    </div>

    <script>
        // JSON-данные
        const data = [
        {
    "question": "This is … computer.",
    "answers": [
      "a"
    ]
  },
  {
    "question": "Shuhrat is … student of telecommunication faculty",
    "answers": [
      "a"
    ]
  },
  {
    "question": "magazine is interesting",
    "answers": [
      "The"
    ]
  },
  {
    "question": "Many people have … opportunity to use computers.",
    "answers": [
      "an"
    ]
  },
  {
    "question": "I buy … laptop for my mother.",
    "answers": [
      "a"
    ]
  },
  {
    "question": "am a programist.",
    "answers": [
      "I"
    ]
  },
  {
    "question": "Dostonjon and Dilshodjon are … students.",
    "answers": [
      "-"
    ]
  },
  {
    "question": "It’s a pity we do not have … camera.",
    "answers": [
      "a"
    ]
  },
  {
    "question": "His brother is … dentist.",
    "answers": [
      "a"
    ]
  },
  {
    "question": "Farhod and Shirin … fellow students.",
    "answers": [
      "are"
    ]
  },
  {
    "question": "Vegetables and fruits ... healthy foods.",
    "answers": [
      "are"
    ]
  },
  {
    "question": "His mother … kind.",
    "answers": [
      "is"
    ]
  },
  {
    "question": "The students ... not at the University today.",
    "answers": [
      "are"
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷумларо ёбед: Ин барнома аст. Найдите правильный перевод предложения: Это программа.",
    "answers": [
      "This is a program."
    ]
  },
  {
    "question": "is an aim.",
    "answers": [
      "That"
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷумларо ёбед: Онҳо донишҷӯён мебошанд. Найдите правильный перевод предложения: Те студенты.",
    "answers": [
      "Those are students."
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷумларо ёбед: Онҳо чароғҳо нестанд. Найдите правильный перевод предложения: Те не лампы.",
    "answers": [
      "Those are not lamps."
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷумларо ёбед: Ин китоби дарсӣ аст. Найдите правильный перевод предложения: Это учебник.",
    "answers": [
      "This is a text book."
    ]
  },
  {
    "question": "Шакли ҷамъи исмро ёбед: Найдите существительное во множественном числе: \"shelf\"",
    "answers": [
      "shelves"
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷумларо ёбед: Ин асбоб аст. Найдите правильный перевод предложения: Это оборудование.",
    "answers": [
      "This is a tool."
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷумларо ёбед: Онҳо кӯдакон мебошанд. Найдите правильный перевод предложения: Те дети.",
    "answers": [
      "Those are babies."
    ]
  },
  {
    "question": "Is….a phone?",
    "answers": [
      "this"
    ]
  },
  {
    "question": "Шакли ҷамъи исмро ёбед: Найдите существительное во множественном числе: \"bookcase\"",
    "answers": [
      "bookcases"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"барномасоз\" - ро ёбед. Найдите правильный вариант слова \"програмист\".",
    "answers": [
      "a programist"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"лоиҳа\" - ро ёбед. Найдите правильный вариант слова \"дизайн\".",
    "answers": [
      "design"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаро ёбед. Найдите правильный перевод слова “space”",
    "answers": [
      "фазо – космос"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"таҷҳизот\" - ро ёбед. Найдите правильный вариант слова \"аппаратура\".",
    "answers": [
      "equipment"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"нишондиҳандаи раъду барқ\" -ро ёбед. Найдите правильный вариант слова \"индикатор\"",
    "answers": [
      "storm indicator"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"шабака\" -ро ёбед. Найдите правильный вариант слова \"сеть\".",
    "answers": [
      "network"
    ]
  },
  {
    "question": "Саволи махсусро муайян намоед. Определите специальный вопрос.",
    "answers": [
      "What is your favorite book?"
    ]
  },
  {
    "question": "Саволи умумиро муайян кунед. – Определите правильный вариант общего вопроса.",
    "answers": [
      "Do they have an English lesson today?"
    ]
  },
  {
    "question": "Is your mother a programist or a waitress?",
    "answers": [
      "интихобӣ – альтернативный"
    ]
  },
  {
    "question": "Cаволи махсусро интихоб кунед. – Выберите специальный вопрос.",
    "answers": [
      "What is your father?"
    ]
  },
  {
    "question": "Саволи махсусро муайян кунед. – Определите специальный вопрос.",
    "answers": [
      "How many students are there in your group?"
    ]
  },
  {
    "question": "Саволи интихобиро муайян созед. Выберите альтернативный вопрос.",
    "answers": [
      "Has your sister many or few English books?"
    ]
  },
  {
    "question": "Ҷавоби дурустро интихоб кунед. Выберите правильный ответ на данный вопрос: Where do you live?",
    "answers": [
      "I live in Dushanbe."
    ]
  },
  {
    "question": "Is he an engineer?",
    "answers": [
      "Yes, he is."
    ]
  },
  {
    "question": "Do you like mobile phone or laptop?",
    "answers": [
      "I like mobile phone."
    ]
  },
  {
    "question": "How do you go to the University?",
    "answers": [
      "махсус - специальный"
    ]
  },
  {
    "question": "She … an opportunity how to prepare programs.",
    "answers": [
      "has"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"компютерикунонӣ\" -ро ёбед. Найдите правильный вариант слова \"компютеризация\".",
    "answers": [
      "computerization"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"ташаккулёбӣ\"-ро ёбед. Найдите правильный вариант слово \"развития\".",
    "answers": [
      "developing"
    ]
  },
  {
    "question": "There is … milk in the bottle.",
    "answers": [
      "little"
    ]
  },
  {
    "question": "Every student … a good dictionary.",
    "answers": [
      "has"
    ]
  },
  {
    "question": "He has … English books at home.",
    "answers": [
      "few"
    ]
  },
  {
    "question": "We have very … time, hurry up!",
    "answers": [
      "little"
    ]
  },
  {
    "question": "Davron … his phone with him.",
    "answers": [
      "has"
    ]
  },
  {
    "question": "Davron … his phone with him.",
    "answers": [
      "has"
    ]
  },
  {
    "question": "She received … letters from her granny.",
    "answers": [
      "some"
    ]
  },
  {
    "question": "Give me … water, please.",
    "answers": [
      "a little"
    ]
  },
  {
    "question": "There are … channels in various spheres.",
    "answers": [
      "a lot of"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаро ёбед. Найдите правильный перевод слова: “plant”",
    "answers": [
      "завод – завод"
    ]
  },
  {
    "question": "Put … lemons in your basket.",
    "answers": [
      "few"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"истифодабарӣ\" -ро ёбед. Найдите правильный вариант слова \"применение\".",
    "answers": [
      "application"
    ]
  },
  {
    "question": "I have … homework for today.",
    "answers": [
      "much"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"васоити ахбори омма\" -ро ёбед. Найдите правильный вариант слова \"средства массовой информации\".",
    "answers": [
      "mass media"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"маълумот\" - ро ёбед. Найдите правильный вариант перевода слово «информация”.",
    "answers": [
      "information"
    ]
  },
  {
    "question": "Тарҷумаи ибораи \"системаи оператсионӣ\" -ро ёбед. Найдите правильный вариант фраза \"операционная система\".",
    "answers": [
      "operating system"
    ]
  },
  {
    "question": "Шакли дурусти қолаби “there is/there are”-ро гузоред. Вставьте правильный вариант структуры “there is/there are”:… not many colored pictures in the hall.",
    "answers": [
      "There are"
    ]
  },
  {
    "question": "Варианти дурусти қолаби “there is/there are”-ро гузоред. Вставьте правильный вариант структуры “there is/there are”:… many red pens in the box?",
    "answers": [
      "Are there"
    ]
  },
  {
    "question": "Шакли дурусти қолаби “there is/there are”-ро гузоред. Вставьте правильный вариант структуры “there is/there are”: … no nice pictures on the shelf.",
    "answers": [
      "There is"
    ]
  },
  {
    "question": "Шакли дурусти қолаби “there is/there are”-ро гузоред. Вставьте правильный вариант структуры “there is/there are”: … a lot of people in the computer centre.",
    "answers": [
      "There are"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаро ёбед. Найдите правильный перевод слова. “concept”",
    "answers": [
      "фаҳмиш - понятие"
    ]
  },
  {
    "question": "Ҷавоби дурустро интихоб кунед: Выберите правильный ответ:",
    "answers": [
      "We are having lunch now."
    ]
  },
  {
    "question": "Mary … (to travel) in Dushanbe at the moment.",
    "answers": [
      "is travelling"
    ]
  },
  {
    "question": "He … (not to visit) Asht at the moment.",
    "answers": [
      "is not visiting"
    ]
  },
  {
    "question": "The children … (to have) a good time.",
    "answers": [
      "are having"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"вазифаи бузург\" -ро ёбед. Найдите правильный вариант слова \"гигантская задача\".",
    "answers": [
      "gigantic task"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"иловакунӣ\" -ро ёбед. Найдите правильный вариант слова \"сложения\".",
    "answers": [
      "adding"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"дастрас\"-ро ёбед. Найдите правильный вариант слово \"доступный\".",
    "answers": [
      "available"
    ]
  },
  {
    "question": "My mother ………. working at half past seven.",
    "answers": [
      "starts"
    ]
  },
  {
    "question": "What do they ... in the evening?",
    "answers": [
      "do"
    ]
  },
  {
    "question": "How ... you spell that in English?",
    "answers": [
      "do"
    ]
  },
  {
    "question": "She … (not to stay) in the USA at the moment.",
    "answers": [
      "is not staying"
    ]
  },
  {
    "question": "Ҷумлаи дурустро интихоб кунед: Выберите правильный ответ:",
    "answers": [
      "Your dad is working today."
    ]
  },
  {
    "question": "My team … (not to win) the match.",
    "answers": [
      "is not winning"
    ]
  },
  {
    "question": "Barno ... up at eight o’clock.",
    "answers": [
      "gets"
    ]
  },
  {
    "question": "Where do Kamol and Madina ... ?",
    "answers": [
      "go"
    ]
  },
  {
    "question": "Sabrina ... what to do.",
    "answers": [
      "knows"
    ]
  },
  {
    "question": "Akbar ... to do shopping.",
    "answers": [
      "likes"
    ]
  },
  {
    "question": "My grandfather ... in London.",
    "answers": [
      "lives"
    ]
  },
  {
    "question": "My sisters _________ to school every day.",
    "answers": [
      "walk"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"чоп кардан\"-ро ёбед. Найдите правильный вариант слова \"печатать\".",
    "answers": [
      "print"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"нишона\" -ро ёбед. Найдите правильный вариант слова \"символ\".",
    "answers": [
      "an image"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"мавҷ\" -ро ёбед. Найдите правильный вариант слова \"волна\".",
    "answers": [
      "wave"
    ]
  },
  {
    "question": "You …. play here if you want.",
    "answers": [
      "may"
    ]
  },
  {
    "question": "Dostonjon….. play tennis very well.",
    "answers": [
      "can"
    ]
  },
  {
    "question": "I come in? Yes, you may.",
    "answers": [
      "May"
    ]
  },
  {
    "question": "They must be there ---- eight.",
    "answers": [
      "at"
    ]
  },
  {
    "question": "They both can… Russian well.",
    "answers": [
      "speak"
    ]
  },
  {
    "question": "The police ……. not see us.",
    "answers": [
      "can not"
    ]
  },
  {
    "question": "His father ….. play chess.",
    "answers": [
      "can"
    ]
  },
  {
    "question": "His grandson doesn’t go to school. He…… read.",
    "answers": [
      "cannot"
    ]
  },
  {
    "question": "It is snowing. You …. put your warm clothes.",
    "answers": [
      "must"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"фазо\" -ро ёбед. Найдите правильный вариант слова \"атмосфера\".",
    "answers": [
      "space"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"саводи компютерӣ\" -ро ёбед. Найдите правильный вариант слово \" компютерная грамотность\".",
    "answers": [
      "computer litracy"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"тадқиқот\" -ро ёбед. Найдите правильный вариант слова \"исследование\".",
    "answers": [
      "investigation"
    ]
  },
  {
    "question": "You are ... me.",
    "answers": [
      "older than"
    ]
  },
  {
    "question": "New York is ... Paris.",
    "answers": [
      "dirtier than"
    ]
  },
  {
    "question": "Prague is one of the ... cities in Europe.",
    "answers": [
      "most beautiful"
    ]
  },
  {
    "question": "Trains in London are more crowded _____ in Paris.",
    "answers": [
      "than"
    ]
  },
  {
    "question": "The Khujand State University is one of ... oldest universities in Tajikistan.",
    "answers": [
      "the"
    ]
  },
  {
    "question": "Who is the ... man in the world?",
    "answers": [
      "richest"
    ]
  },
  {
    "question": "My friend’s really .... He always buys presents for everyone.",
    "answers": [
      "generous"
    ]
  },
  {
    "question": "Which is the hardest of these three substances ...?",
    "answers": [
      "steel"
    ]
  },
  {
    "question": "Зидмаънои калимаро ёбед: Найдите противоположное значение данного прилагательного: big",
    "answers": [
      "small"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"аломат\" -ро ёбед. Найдите правильный перевод слова \"знак\".",
    "answers": [
      "sign"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"дастгоҳи тарҷумакунӣ\" -ро ёбед. Найдите правильный вариант слово \"машинный перевод\".",
    "answers": [
      "Тарҷумаи калимаи \"дастгоҳи тарҷумакунӣ\" -ро ёбед. Найдите правильный вариант слово \"машинный перевод\"."
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"олим\" -ро ёбед. Найдите правильный вариант слова \"учёный\".",
    "answers": [
      "scientist"
    ]
  },
  {
    "question": "We … home yesterday.",
    "answers": [
      "walked"
    ]
  },
  {
    "question": "I … at school a year ago.",
    "answers": [
      "studied"
    ]
  },
  {
    "question": "Замони гузаштаи феъли номуайянро интихоб кунед. Выберите глагол в прошедшем неопределённом времени: to solve",
    "answers": [
      "solved"
    ]
  },
  {
    "question": "I … up at 7 o’clock yesterday.",
    "answers": [
      "got"
    ]
  },
  {
    "question": "Зарфи замони гузаштаи номуйянро ёбед. Найдите наречие прошедшей неопределённой времени:",
    "answers": [
      "last year"
    ]
  },
  {
    "question": "My brother … a pupil last year.",
    "answers": [
      "was"
    ]
  },
  {
    "question": "Замони гузаштаи феъли номуайянро интихоб кунед Выберите неопределённое прошедшее время глагола: to direct",
    "answers": [
      "directed"
    ]
  },
  {
    "question": "They … at club last week.",
    "answers": [
      "went"
    ]
  },
  {
    "question": "We … in America last year.",
    "answers": [
      "lived"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"таҷриба\" - ро ёбед. Найдите правильный вариант слова \"эксперимент\".",
    "answers": [
      "experiment"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"ихтироъ\" -ро ёбед. Найдите правильный вариант слова \"изобретение\".",
    "answers": [
      "invention"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"хотира\" -ро ёбед. Найдите правильный вариант слова \"память\".",
    "answers": [
      "memory"
    ]
  },
  {
    "question": "Will you go to the concert this evening?",
    "answers": [
      "Yes, I shall"
    ]
  },
  {
    "question": "Will they discuss your plan at the meeting?",
    "answers": [
      "Yes, they shall."
    ]
  },
  {
    "question": "Will you go there by bus or by train?",
    "answers": [
      "I shall go there by bus."
    ]
  },
  {
    "question": "Will he be a student next year?",
    "answers": [
      "Yes, he will."
    ]
  },
  {
    "question": "Shall we go there in the morning or in the afternoon?",
    "answers": [
      "We shall go there in the morning."
    ]
  },
  {
    "question": "When will you visit your friend?",
    "answers": [
      "I shall visit my friend next week."
    ]
  },
  {
    "question": "What will you do tomorrow?",
    "answers": [
      "I shall make my report tomorrow."
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"захиракунӣ\" - ро ёбед. Найдите правильный вариант слова \"запасать\".",
    "answers": [
      "storing"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"сабаб\" -ро ёбед. Найдите правильный вариант слова \"причина\".",
    "answers": [
      "reason"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"қувва\" -ро ёбед. Найдите правильный вариант слова \"сила\".",
    "answers": [
      "power"
    ]
  },
  {
    "question": "Have you discussed any problem this week?- Yes, I… .",
    "answers": [
      "have."
    ]
  },
  {
    "question": "Has Nekruz ever been to London? -No, he has… been to London.",
    "answers": [
      "never"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"амалиёт\" - ро ёбед. Найдите правильный вариант слова \"операция\".",
    "answers": [
      "operation"
    ]
  },
  {
    "question": "Ҷумлаи дурустро ёбед. Найдите правильное предложение.",
    "answers": [
      "Automation is performing certain tasks, previously done by people."
    ]
  },
  {
    "question": "play an important role as a mass media.",
    "answers": [
      "Radio and TV - set"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"саҳвакалид\" - ро ёбед. Найдите правильный вариант слова \"клавиатура\".",
    "answers": [
      "keyboard"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"хато\" -ро ёбед. Найдите правильный вариант слово \"ошибка\".",
    "answers": [
      "error"
    ]
  },
  {
    "question": "Тарҷумаи калимаи \"телекоммуникатсия\" - ро ёбед. Найдите правильный вариант слова \"телекоммуникация\".",
    "answers": [
      "telecommunication"
    ]
  },
  {
    "question": "Феъли “to be”-ро ёбед: Найдите глагол “to be”:",
    "answers": [
      "am\nis\nare"
    ]
  },
  {
    "question": "Ҷумлаҳои феъли “to be” доштаро ёбед: Найдите предложения с глаголом “to be”",
    "answers": [
      "He is a scientist.\nShe is a programmist.\nWe are engineers."
    ]
  },
  {
    "question": "Ҷонишинҳои шахси сеюми танҳоро нишон диҳед: Укажите местоимения третьего лица:",
    "answers": [
      "he\nshe\nit"
    ]
  },
  {
    "question": "Ҷумлаҳои артикли номуайян доштаро нишон диҳед: Укажите предложения с неопределённым артиклем:",
    "answers": [
      "That is an apricot.\nI see a blackboard."
    ]
  },
  {
    "question": "Ҷумлаҳои артикли муайян доштаро нишон диҳед: Укажите предложения с определённым артиклем:",
    "answers": [
      "The TV - set is on the wall.\nWhere is the computer?\nThe apple is sweet."
    ]
  },
  {
    "question": "Ҷумлаҳои артикли номуайян доштаро нишон диҳед: Укажите предложение с неопределённым артиклем:",
    "answers": [
      "That is a hardware.\nI eat an apple pie.\nI see a radio on the shelf."
    ]
  },
  {
    "question": "Ду ҷумлаи дурустро бо ҷонишинҳои ишоратӣ ёбед: Определите два правильных предложения с указательными местоимениями:",
    "answers": [
      "This is my presentation.\nThat is her design."
    ]
  },
  {
    "question": "Су ҷумлаи дурустро бо ҷонишинҳои ишоратӣ ёбед: Определите три правильных предложения с указательными местоимениями:",
    "answers": [
      "These are important channels.\nThis is an useless thing.\nThat is a magazine."
    ]
  },
  {
    "question": "Ду ҷумларо бо ҷонишинҳои ишоратӣ ёбед: Найдите два предложения c указательными местоимениями:",
    "answers": [
      "That is a benefit of automation.\nThis is an automatic control."
    ]
  },
  {
    "question": "Се ҷумларо бо ҷонишинҳои ишоратӣ ёбед: Найдите три предложения c указательными местоимениями.",
    "answers": [
      "Those are industrial robots.\nThat is a disk.\nThese are disadvantages of mobile phone."
    ]
  },
  {
    "question": "Ду ҷавоби дурусти исмҳоро дар шакли ҷамъ муайян кунед: Определите два правильных существительных во множественном числе:",
    "answers": [
      "universities\nchannels"
    ]
  },
  {
    "question": "Се ҷавоби дурусти исмҳоро дар шакли ҷамъ муайян кунед: Определите три правильных существительных во множественном числе:",
    "answers": [
      "operations\nrobots\nmachines"
    ]
  },
  {
    "question": "Саволҳои умумиро муайян кунед. Определите общие вопросы.",
    "answers": [
      "Are those control systems?\nIs this a plan?\nIs this a book or a copybook?"
    ]
  },
  {
    "question": "Does Sofiya work at the office?",
    "answers": [
      "No, she does not.\nYes, she does."
    ]
  },
  {
    "question": "Ҷумлаҳои саволиро интихоб намоед. Выберите вопросительные предложения.",
    "answers": [
      "Does she meet her parents?\nWhat is her name?"
    ]
  },
  {
    "question": "Тарҷумаҳои дурусти ҷумларо муайян намоед: «Ман хуб нестам». Выберите правильные варианты перевода: «Я не чувствую себя хорошо»",
    "answers": [
      "I am not well.\nI am not fine."
    ]
  },
  {
    "question": "Муродифҳои калимаи «оғоз кардан»-ро ёбед. Выберите правильные варианты слова «начинать»",
    "answers": [
      "to begin\nto start"
    ]
  },
  {
    "question": "Тарҷумаҳои дурусти калимаро муайян кунед \"таҷҳизот\". Выберите правильные переводы слова \"обородувание\"",
    "answers": [
      "device\nfacility"
    ]
  },
  {
    "question": "Тарзҳои дурусти истифодаи калимаи “доштан”-ро ёбед: Найдите правильные варианты использования слова “иметь”:",
    "answers": [
      "The man has an idea.\nMufiz has a computer."
    ]
  },
  {
    "question": "Шаклҳои дурусти истифодаи калимаи “бисёр”- ро ёбед: Найдите правильные варианты использования слова “много”:",
    "answers": [
      "many teachers\nmany cabbages"
    ]
  },
  {
    "question": "Шаклҳои дурусти истифодаи калимаи “бисёр”-ро ёбед: Найдите правильные использования слова “много”",
    "answers": [
      "much time\nmuch bread\nmuch coffee"
    ]
  },
  {
    "question": "Ду саволи дурустро интихоб кунед: Выберите два правильных вопроса:",
    "answers": [
      "Have you brothers and sisters?\nHave they mathematical and logical operations?"
    ]
  },
  {
    "question": "Ду ҷумлаи аз ҷиҳати грамматикӣ дурустро интихоб кунед: Выберите два грамматически правильных предложения:",
    "answers": [
      "Mardon has an internet.\nAsila has a printer at home."
    ]
  },
  {
    "question": "Шаклҳои дурусти истифодаи калимаи “кам”-ро интихоб кунед: Выберите правильные варианты перевода слова “мало”:",
    "answers": [
      "few English and Tajik books\nfew tables"
    ]
  },
  {
    "question": "Тарҷумаҳои дурустро интиҳоб намоед. Выберите правильный перевод \"modern\":",
    "answers": [
      "замонавӣ – современный\nмуосир – новый"
    ]
  },
  {
    "question": "There are some computers …",
    "answers": [
      "in the classroom.\nin the library."
    ]
  },
  {
    "question": "There are … hardware pieces in a computer system.",
    "answers": [
      "many\na lot of"
    ]
  },
  {
    "question": "There is … on our teacher`s desk.",
    "answers": [
      "a CD player\na modem"
    ]
  },
  {
    "question": "Is there … on the desk?",
    "answers": [
      "a disk\na TV-set"
    ]
  },
  {
    "question": "Ҷумлаҳои аз ҷиҳати грамматики дурустро ёбед. Найдите грамматически правильные предложения.",
    "answers": [
      "There are five basic operations of data processing systems.\nThere are no five basic operations of data processing systems."
    ]
  },
  {
    "question": "Ҷавобҳои дурустро интихоб кунед: Выберите правильные варианты:",
    "answers": [
      "There are some magazines on the shelf.\nThere are not any newspapers on the table."
    ]
  },
  {
    "question": "Ҷавобҳои дурустро интихоб кунед: Выберите правильные ответы:",
    "answers": [
      "Give me any English books.\nShe has no mobile phone.\nGive me some Tajik books."
    ]
  },
  {
    "question": "Ҷавобҳои дурустро интихоб кунед: Выберите правильные ответы:",
    "answers": [
      "There is no ink in my pen.\nIs there any negative side of the TV - set?"
    ]
  },
  {
    "question": "Ҷавобҳои дурустро интихоб кунед: Выберите правильные ответы:",
    "answers": [
      "Tell us your role.\nGive me your plan."
    ]
  },
  {
    "question": "Ҷавобҳои дурустро интихоб кунед: Выберите правильные ответы:",
    "answers": [
      "I can help her.\nRukhshona can help me."
    ]
  },
  {
    "question": "Ҷавобҳои дурустро интихоб кунед: Выберите правильные ответы:",
    "answers": [
      "Do you know him?\nOne of them is my instruction."
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи \"instruction\"-ро ёбед. Найдите правильный ответ слова \"instruction\"",
    "answers": [
      "дастур\nнишондод"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи \"таҷҳизот\"-ро муайян кунед. Определите правильный вариант слова \"аппарат\".",
    "answers": [
      "facility\ndevice\nhardware"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи \"рӯз\"-ро ёбед. Найдите правильный вариант слова \"день\".",
    "answers": [
      "day"
    ]
  },
  {
    "question": "Ҷумлаҳоро дар замони ҳозираи давомдор интихоб кунед: Выберите предложения в настоящем продолженном времени:",
    "answers": [
      "Life is becoming more and more difficult.\nWe are quickly becoming an information society.\nMr.Brown is going to the computer center."
    ]
  },
  {
    "question": "Ҷумлаҳоро дар замони ҳозираи давомдор интихоб кунед: Выберите предложения в настоящем продолженном времени:",
    "answers": [
      "Mardon and Salima are showing their presentation.\nRahim is staying at home."
    ]
  },
  {
    "question": "Ҷумлаҳоро дар замони ҳозираи давомдор муайян кунед: Определите предложения в настоящем продолженном времени:",
    "answers": [
      "Sanobar is not singing.\nSamad is working at his project."
    ]
  },
  {
    "question": "Ҷумлаҳои замони ҳозираи давомдорро интихоб кунед: Выберите предложения в настоящем продолженном времени:",
    "answers": [
      "The students are wearing a uniform.\nHe is copying from other students."
    ]
  },
  {
    "question": "Ҷумлаҳоро дар замони ҳозираи давомдор интихоб кунед: Выберите предложения в настоящем продолженном времени:",
    "answers": [
      "A little boy is playing inside.\nThe computers are becoming expensive."
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи \" чанд қадар\"-ро ёбед. Найдите правильный вариант слова \"сколько\".",
    "answers": [
      "How many\nHow much"
    ]
  },
  {
    "question": "Ду ҷумлаҳои дурусти ба замони ҳозираи номуайян тааллуқдоштаро ёбед: Найдите два правильных ответа соответствующих настоящему неопределённому времени:",
    "answers": [
      "This computer works well.\nHe speaks English."
    ]
  },
  {
    "question": "Ду ҷумлаҳои замони ҳозираи номуайянро ёбед: Найдите два предложение соответствующих настоящему неопределённому времени:",
    "answers": [
      "One can use internet for recreational purposes.\nMillions of people around the world use the internet."
    ]
  },
  {
    "question": "Ду ҷумлаҳои замони ҳозираи номуайянро ёбед: Найдите два предложение соответствующих настоящему неопределённому времени:",
    "answers": [
      "Muhammadjon likes mobile phone.\nUsually we go to the University by car."
    ]
  },
  {
    "question": "Ду ҷумлаҳои дурусти ба замони ҳозираи номуайян тааллуқдоштаро ёбед: Найдите два правильных предложение соответствующих настоящему неопределённому времени:",
    "answers": [
      "She usually comes home at 4 o’clock.\nEach browser provides a graphical interface.\nYesterday the window was broken by someone."
    ]
  },
  {
    "question": "Се ҷумлаҳои замони ҳозираи номуайянро ёбед: Найдите три предложение соответствующих настоящему неопределённому времени:",
    "answers": [
      "They choose a new data.\nMy sister looks through the files.\nMillions of people watch this programme."
    ]
  },
  {
    "question": "Се ҷумлаҳои дурусти ба замони ҳозираи номуайян тааллуқдоштаро ёбед: Найдите три предложение соответствующих настоящему неопределённому времени:",
    "answers": [
      "The machine has a dictionary.\nThe translating machines are very useful to scientists.\nHis friend plays with you."
    ]
  },
  {
    "question": "I help her?",
    "answers": [
      "Can\nMay"
    ]
  },
  {
    "question": "Ҷумлаҳое, ки феълҳои модалӣ доранд интихоб кунед. Выберите предложения в котором имеются модальные глаголы.",
    "answers": [
      "I must go there.\nI can solve this problem."
    ]
  },
  {
    "question": "Саволҳое, ки феълҳои модалӣ доранд интихоб кунед. Выберите вопросы в котором имеются модальные глаголы.",
    "answers": [
      "Can you play tennis?\nMay I take your book?"
    ]
  },
  {
    "question": "Саволҳое, ки феълҳои модалӣ доранд интихоб кунед. Выберите вопросы в котором имеются модальные глаголы.",
    "answers": [
      "May I go home early today?\nCan I help you?"
    ]
  },
  {
    "question": "Ҷумлаҳое, ки феълҳои модалӣ доранд интихоб кунед. Выберите предложения в котором имеются модальные глаголы.",
    "answers": [
      "You must answer her questions.\nI cannot teach you Uzbek."
    ]
  },
  {
    "question": "Ҷумлаҳое, ки феълҳои модалӣ доранд интихоб кунед. Выберите предложения в котором имеются модальные глаголы.",
    "answers": [
      "I can continue my speech.\nYou may take my dictionary."
    ]
  },
  {
    "question": "Се тарҷумаҳои калимаи “машҳур”- ро ёбед: Выберите три правильных перевода слова «знаменитый»:",
    "answers": [
      "outstanding\nwell-known\npopular"
    ]
  },
  {
    "question": "Аз калимаҳои зерин ду сифатҳоро интихоб кунед: Найдите два прилагательных из следующих слов:",
    "answers": [
      "necessary\nuseful"
    ]
  },
  {
    "question": "Аз калимаҳои зерин се сифатҳоро интихоб кунед: Найдите три прилагательных из следующих слов:",
    "answers": [
      "expensive\nwonderful\nwell"
    ]
  },
  {
    "question": "Ду ибораҳои дурусти ба сифат тааллуқдоштаро ёбед: Найдите два правильных словосочетания с прилагательным:",
    "answers": [
      "a negative side\nan important role"
    ]
  },
  {
    "question": "Ду тарҷумаҳои калимаи “аломат, нишона”-ро ёбед: Найдите два правильных перевода слова «символ»:",
    "answers": [
      "symbol\nsign"
    ]
  },
  {
    "question": "Зидмаънои “душвор”- ро ёбед: Найдите антоним слова «трудный»:",
    "answers": [
      "simple\neasy"
    ]
  },
  {
    "question": "Ҷумлаҳои замони гузаштаи номуайянро интихоб кунед. Выберите правильный вариант предложений в прошедшем времени.",
    "answers": [
      "I wrote an interesting article last month.\nThey went to the park last week.\nWe discussed many questions yesterday."
    ]
  },
  {
    "question": "Ҷумлаҳои замони гузаштаи номуайянро интихоб кунед. Выберите правильный вариант предрожений в прошедшем времени.",
    "answers": [
      "We spoke about the types of computers.\nThe ancient Egyptions recorded the ebb."
    ]
  },
  {
    "question": "Ҷумлаҳои замони гузаштаи номуайянро интихоб кунед. Выберите правильный вариант предложений в прошедшем времени.",
    "answers": [
      "It was my mistake.\nShe smiled when she saw me.\nWe were there last week."
    ]
  },
  {
    "question": "Ҷумлаҳои замони гузаштаи номуайянро интихоб кунед. Выберите правильный вариант предрожений в прошедшем времени.",
    "answers": [
      "We were at home two days ago.\nI watched a good film yesterday."
    ]
  },
  {
    "question": "Ҷумлаҳои замони гузаштаи номуайянро интихоб кунед. Выберите правильный вариант предложений в прошедшем времени.",
    "answers": [
      "I opened the door.\nHe met her at the station."
    ]
  },
  {
    "question": "Ҷумлаҳои замони гузаштаи номуайянро интихоб кунед. Выберите правильный вариант предл ожений в прошедшем времени.",
    "answers": [
      "The teachers went to the conference last week.\nI wrote a message yesterday."
    ]
  },
  {
    "question": "Who will answer this question?",
    "answers": [
      "I shall\nHe will"
    ]
  },
  {
    "question": "Who will go there with you?",
    "answers": [
      "They will.\nMy friend will."
    ]
  },
  {
    "question": "shall prepare laboratory tests.",
    "answers": [
      "We\nI"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаро интихоб намоед \"деҳа\". Выберите правильный перевод слова \" село\":",
    "answers": [
      "village"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаро номбар кунед \"гирифтан\". Выберите правильный перевод слово \"получать\":",
    "answers": [
      "to receive\nto get"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаро ёбед. Выберите правильный перевод слова \"power\":",
    "answers": [
      "қувва – сила\nҳокимият – власть"
    ]
  },
  {
    "question": "Замони ҳозираи мутлақро муайян кунед: Определите настоящее совершенное время:",
    "answers": [
      "We have looked at the picture.\nShe has worked hard."
    ]
  },
  {
    "question": "Замони ҳозираи мутлақро муайян кунед: Определите настоящее совершенное время:",
    "answers": [
      "The children have played outside.\nThe child has shown a picture."
    ]
  },
  {
    "question": "Замони ҳозираи мутлақро муайян кунед: Определите настоящее совершенное время:",
    "answers": [
      "Anisa and Asila have stayed at home.\nShe has spoken quickly."
    ]
  },
  {
    "question": "Замони ҳозираи мутлақро муайян кунед: Определите настоящее совершенное время:",
    "answers": [
      "She has eaten.\nI have visited."
    ]
  },
  {
    "question": "Замони ҳозираи мутлақро муайян кунед: Определите настоящее совершенное время:",
    "answers": [
      "She has talked to his friends.\nWe have finished the exercise.\nThey have translated the text."
    ]
  },
  {
    "question": "Замони ҳозираи мутлақро муайян кунед: Определите настоящее совершенное время:",
    "answers": [
      "Sanobar has invited her friends.\nWe have described the picture.\nShe has missed the lesson."
    ]
  },
  {
    "question": "There are ... of TV - set.",
    "answers": [
      "disadvantages\nadvantages"
    ]
  },
  {
    "question": "Ду ҷавоби дурустро интихоб намоед: \"bank\". Выберите два правильных ответа: \"bank\"",
    "answers": [
      "соҳил- берег\nбонк- банк"
    ]
  },
  {
    "question": "Ду ҷавоби дурустро интихоб намоед \"мақсад\". Выберите два правильных ответа \"цель\"",
    "answers": [
      "aim\npurpose\ngoal"
    ]
  },
  {
    "question": "Ду ҷавоби дурустро интихоб намоед \"glass\". Выберите два правильных ответа \"glass\":",
    "answers": [
      "зарф - стакан\nшиша - стекло"
    ]
  },
  {
    "question": "Ду ҷавоби дурустро интихоб намоед \"баъзан\". Выберите два правильных ответа \"иногда\":",
    "answers": [
      "sometimes\nseldom"
    ]
  },
  {
    "question": "Ду ҷавоби дурустро интихоб намоед \"study\". Выберите два правильных ответа \"study\":",
    "answers": [
      "омӯхтан- обучать\nилм - наука"
    ]
  },
  {
    "question": "Тарҷумаҳои калимаи” ҷиҳати манфӣ”-ро ёбед. Переводите слово “недостаток”:",
    "answers": [
      "disadvantage\nnegative side"
    ]
  },
  {
    "question": "Тарҷумаҳои калимаи ”ҳозир набудан ”- ро ёбед. Переводите слово “отсутствовать”:",
    "answers": [
      "to be absent\nto miss"
    ]
  },
  {
    "question": "Тарҷумаҳои калимаи” маълумот”-ро ёбед. Переводите слово “информация”:",
    "answers": [
      "data\ninformation"
    ]
  },
  {
    "question": "Муродифҳои калимаи “омӯзиш”- ро ба забони англисӣ ёбед: Определите синонимы слова ”изучать”:",
    "answers": [
      "to study\nto read"
    ]
  },
  {
    "question": "Watching television has two sides: not only … but also…",
    "answers": [
      "advantages\ndisadvantages"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи “кофтуков кардан” – ро интихоб кунед. Выбирети правильный перевод слова “искать”:",
    "answers": [
      "to look for\nto search for"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи “to succeed” – ро интихоб кунед. Выберите правильный перевод слова “to succeed”.",
    "answers": [
      "муваффақ шудан- соответствовать\nба мақсад расидан – достижения цели"
    ]
  },
  {
    "question": "What is mobile phone?",
    "answers": [
      "Mobile phone is an electronic device.\nMobile phone is a very useful device.\nMobile phone is the means of communication."
    ]
  },
  {
    "question": "Do you know the types of computers? Yes, I do. They are…",
    "answers": [
      "analog\ndigital"
    ]
  },
  {
    "question": "We can not deny the role of … in our life.",
    "answers": [
      "internet\ntelecommunications"
    ]
  },
  {
    "question": "Тарҷумаҳои дурусти калимаи “ҳаракатро” – ро ёбед. Найдите правильные переводы слова “движения”.",
    "answers": [
      "movement\nmotion"
    ]
  },
  {
    "question": "We live in information ….",
    "answers": [
      "era.\ntime."
    ]
  },
  {
    "question": "Ду тарҷумаи дурусти калимаи “барномасоз” – ро ба забони англисӣ ёбед. Выбирайте два правильного варианта слово “програмист”:",
    "answers": [
      "a programmist\na programmer"
    ]
  },
  {
    "question": "Муродифи калимаи “майда” – ро ёбед. Определите правильный перевод “маленький”:",
    "answers": [
      "little\nsmall"
    ]
  },
  {
    "question": "Ду ҷавоби дурусти калимаи “хотира” – ро нишон диҳед. Укажите два правильного варианта слово “память”:",
    "answers": [
      "memory\nstorage"
    ]
  },
  {
    "question": "Саволи махсусро нишон диҳед. Укажите специальный вопрос.",
    "answers": [
      "What do operating systems control?"
    ]
  },
  {
    "question": "Ҷумларо пурра кунед: Computers provide ….Вместо точек вставьте правильное слово: Computers provide ….",
    "answers": [
      "security of process\nsafety of process"
    ]
  },
  {
    "question": "Намудҳои компютерро нишон диҳед. Укажите виды компютера.",
    "answers": [
      "digital\nanalog\nmobile\nhybrid"
    ]
  },
  {
    "question": "Се тарҷумаҳои калимаи “idea” – ро муайян кунед. Выбирайте три правильного варианта слово “idea”.",
    "answers": [
      "фикр\nғоя\nақида"
    ]
  },
  {
    "question": "Калимаҳои “маъруф, шинохта ” – ро ишора намоед. Укажите правильный перевод “знаменитый”.",
    "answers": [
      "outstanding\nfamous"
    ]
  },
  {
    "question": "Ҷумлаҳое, ки бо феъл бандаки “to be” сохта шудаанд интихоб кунед. Выбирайте предложения с глаголам “to be”.",
    "answers": [
      "Inputting, storing, processing, outputting and controlling are the basic operations.\nThe main aim of radio is to give information."
    ]
  },
  {
    "question": "What role do radio and TV play in our life?",
    "answers": [
      "An important role.\nThe main role."
    ]
  },
  {
    "question": "Popov demonstrated his storm indicator.",
    "answers": [
      "Popov did not demonstrate his storm indicator.\nDid Popov demonstrate his storm indicator?"
    ]
  },
  {
    "question": "Ду ҷавоби дурусти калимаи “number” –ро интихоб кунед. Выбирайте два правильного перевода слово “number”.",
    "answers": [
      "шумора (число)\nрақам (номер)"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи “равшанӣ”—ро интихоб намоед. Выбирайте правильный перевод слово “освещение”",
    "answers": [
      "brightness;\nlight;"
    ]
  },
  {
    "question": "A. Popov was a Russian…",
    "answers": [
      "physicist.\nscientist."
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи “дастрас” – ро интихоб кунед. Выбирайте правильный перевод слово “доступный”",
    "answers": [
      "available;"
    ]
  },
  {
    "question": "Вариантҳои дурусти ифодаи математикиро интихоб намоед; Выбирайте правильный вариант арифметической задачи: 14:7= 2",
    "answers": [
      "Fourteen divided by seven equals to two;\nFourteen divided by seven is two;"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи “ҳисоб кардан”-ро интихоб кунед; Выбирайте правильный перевод слово “вычислять”",
    "answers": [
      "to calculate;"
    ]
  },
  {
    "question": "Варианти дурусти ифодаи математикиро интихоб кунед; Выбирайте правильный вариант арифметической задачи: 3 X 5= 15",
    "answers": [
      "three multiplied by five is fifteen;\nthree times five is fifteen;"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи “шабака” – ро интихоб намоед; Выбирайте правильный перевод слово “сеть”.",
    "answers": [
      "network"
    ]
  },
  {
    "question": "Варианти дурусти ифодаи математикиро интихоб намоед; Выбирайте правильный вариант арифметической задачи: 74+ 12 =86",
    "answers": [
      "seventy four plus twelve equals to eighty-six;\nseventy four and twelve is eighty- six;"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаи “ to perform” – ро интихоб кунед. Выбирайте правильный перевод слово “ to perform ”.",
    "answers": [
      "иҷро кардан (выполнять)"
    ]
  },
  {
    "question": "Се ҷавоби дурусти калимаи \"individual\"- ро ёбед: Найдите три правилных ответа слово \"individual\":",
    "answers": [
      "шахс (личность)\nфард (особа)\nинфиродият (индивидуальность)"
    ]
  },
  {
    "question": "Се ҷавоби дурусти калимаи \"intellectual\"- ро интихоб кунед: Найдите три правильных ответа слово \"intellectual\":",
    "answers": [
      "хирадманд (разумный)\nзиёи (интиллегентция)\nравшанфикр (просвещённый)"
    ]
  },
  {
    "question": "Ду ҷавоби калимаи \"таҷриба\"- ро ёбед: Найдите два правильных ответа слово \"эксперимент\":",
    "answers": [
      "practice\nexperiment"
    ]
  },
  {
    "question": "Ду ҷавоби калимаи \"achievement\"- ро ёбед: Найдите два варианта ответа слово \"achievement\":",
    "answers": [
      "дастовард (успех)\nмуваффақият (достижение)"
    ]
  },
  {
    "question": "Се ҷавоби калимаи \"асосӣ\"- ро ёбед: Найдите три правильных ответа слово \"основной\":",
    "answers": [
      "main\nfundamental\nbasic"
    ]
  },
  {
    "question": "Се саволҳои умумиро муайян кунед. Определите три общих вопроса.",
    "answers": [
      "Is this a laptop?\nAre those phones?\nIs this a map or a picture?"
    ]
  },
  {
    "question": "Does he speak English well?",
    "answers": [
      "Yes, he does.\nNo, he does not."
    ]
  },
  {
    "question": "Do they play football every week?",
    "answers": [
      "Yes, they do.\nNo, they do not."
    ]
  },
  {
    "question": "Ҷумлаҳоро дар замони ҳозираи номуайян интихоб намоед. Выберите предложения в настоящем неопределенном времени.",
    "answers": [
      "She speaks English well.\nWe go to the University every day."
    ]
  },
  {
    "question": "Ҷумлаҳоро дар замони ҳозираи номуайн интихоб кунед. Выберите предложения в настоящем неопределенном времени.",
    "answers": [
      "My father works in the hospital.\nShe writes a letter every week."
    ]
  },
  {
    "question": "Муродифҳои калимаи «гирифтан»- ро ёбед. – Выберите правильные варианты слова «получать»",
    "answers": [
      "to receive\nto get"
    ]
  },
  {
    "question": "Муродифҳои калимаи «ҳал кардан»-ро ёбед. – Выберите правильные варианты слова «решать»",
    "answers": [
      "to solve\nto decide"
    ]
  },
  {
    "question": "Муродифҳои калимаи «дарс»-ро ёбед. – Выберите правильные варианты слова «занятие»",
    "answers": [
      "class\nlesson"
    ]
  },
  {
    "question": "Ду ҷавоби калимаи \"алоқа\"- ро ёбед: Найдите два правилных ответа слово \"контакт\":",
    "answers": [
      "relationship\ncontact"
    ]
  },
  {
    "question": "Processing is a … that convert inputs into outputs.",
    "answers": [
      "a series of actions\na series of operations"
    ]
  },
  {
    "question": "Storing is the process of saving … or ...",
    "answers": [
      "information\ndata"
    ]
  },
  {
    "question": "Instructions direct the operation of a computer.",
    "answers": [
      "What do instructions do?\nInstructions don`t direct the operation of a computer."
    ]
  },
  {
    "question": "What are the motions of machines controlled by?",
    "answers": [
      "magnetic tapes\nthe use of feedback"
    ]
  },
  {
    "question": "Ду ҷавоби дурусти калимаи “лента” – ро нишон диҳед. Укажите два правильного варианта слово “лента”.",
    "answers": [
      "tape\nribbon"
    ]
  },
  {
    "question": "Ҷумларо пурра кунед. TV - set helps us ….Вместо точек вставьте правильное слово: TV - set helps us….",
    "answers": [
      "to forget worries and problems\nto relax"
    ]
  },
  {
    "question": "Ҷумлаҳоро ба охир расонед: Дополните предложения:",
    "answers": [
      "She has a … DDDD\tA)\tclever.\nHe is … AAAA\tB)\tlaptop.\nThey learn … CCCC\tC)\tsecurity.\nComputers provide … BBBB\tD)\tcomputer."
    ]
  },
  {
    "question": "Ҷумлаҳоро ба пурра кунед: Дополните предложения:",
    "answers": [
      "Many people have a high degree of … CCCC\tA)\tpicture.\nComputer is an … FFFF\tB)\tuniversity.\nThe test is not too … CCCC\tC)\tcomputer literacy.\nChildren like to play computer... EEEE\tD)\tdifficult.\n\tE)\tgames.\n\tF)\telectronic device."
    ]
  },
  {
    "question": "Ҷумлаҳоро ба охир расонед: Дополните предложения:",
    "answers": [
      "I am ... DDDD\tA)\tin a week.\nI learn... BBBB\tB)\tEnglish and Russian.\nHe works six days … AAAA\tC)\triver.\nTeachers use computer during their… EEEE\tD)\ta programmer.\n\tE)\tlessons."
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаҳоро ёбед: Найдите правильный перевод слов:",
    "answers": [
      "маълумот-дата BBBB\tA)\tdigital\nрақамӣ - цифровой AAAA\tB)\tdata\nбарномаҳо- программное обеспечение  DDDD\tC)\tprocessing\nкоркардкунӣ– обработка CCCC\tD)\tsoftware"
    ]
  },
  {
    "question": "Тарҷумаҳоро мувофиқат кунонед: Соответсвуйте перевод слов:",
    "answers": [
      "саҳвакалид -клавиатура AAAA\tA)\tkeyboard\nтугмачаҳо калид - клавиша BBBB\tB)\tletter keys\nнуқтагузорӣ – пунктуация DDDD\tC)\tstorage\nмақсад – цель EEEE\tD)\tpunctuation\n\tE)\tpurpose"
    ]
  },
  {
    "question": "Калимаҳои партофташударо ҷо ба ҷо гузоред: Вставьте правильно пропущенные слова:",
    "answers": [
      "The … are in the hospital. \nBBBB\tA)\tteachers\nThe … are at school. AAAA\tB)\tdoctors\nThe … are in the plant. DDDD\tC)\tcars\nThe … is in the garage. CCCC\tD)\tworkers"
    ]
  },
  {
    "question": "Калимаҳоро дар шакли ҷамъ мувофиқат кунонед: Подберите слова во множественном числе:",
    "answers": [
      "plant DDDD\tA)\tshelves\ndevice BBBB\tB)\tdevices\nshelf AAAA\tC)\tpies\ntooth EEEE\tD)\tplants\n\tE)\tteeth"
    ]
  },
  {
    "question": "Калимаҳоро дар шакли ҷамъ мувофиқат кунонед: Подберите слова во множественном числе:",
    "answers": [
      "house DDDD\tA)\tstories\nfactory BBBB\tB)\tfactories\nstory AAAA\tC)\thistories\ntablet EEEE\tD)\thouses\n\tE)\ttablets"
    ]
  },
  {
    "question": "Калимаҳоро дар шакли ҷамъ мувофиқат кунонед: Подберите слова во множественном числе:",
    "answers": [
      "examination. CCCC\tA)\tprogrammers\nradio FFFF\tB)\texams\nmatch DDDD\tC)\texaminations\nprogram EEEE\tD)\tmatches\n\tE)\tprograms"
    ]
  },
  {
    "question": "Тарҷумаи ҷумлаҳоро мувофиқат кунонед: Сопоставьте перевод предложений:",
    "answers": [
      "This is a box. FFFF\tA)\tОн мард аст. Тот мужчина.\nThis is a man. BBBB\tB)\tИн мард аст. Это мужчина.\nThat is a pencilcase. DDDD\tC)\tИн бача аст. Это ребёнок.\nThat is a child. EEEE\tD)\tВай қаламдон аст. Тот пенал.\n\tE)\tВай бача аст. Тот ребёнок.\n\tF)\tИн қуттӣ аст. Это коробка."
    ]
  },
  {
    "question": "Тарҷумаи ҷумлаҳоро мувофиқат кунонед: Сопоставьте перевод предложений:",
    "answers": [
      "Ин матн аст. Это текст.  BBBB\tA)\tThat is a lesson.\nОн дарс аст. Тот урок. AAAA\tB)\tThis is a text.\nОнҳо матнҳо мебошанд. Те тексты. DDDD\tC)\tThese are lessons.\nИнҳо дарсҳо мебошанд. Эти уроки. CCCC\tD)\tThose are texts."
    ]
  },
  {
    "question": "Тарҷумаи ҷумлаҳоро мувофиқат кунонед: Сопоставьте перевод предложений:",
    "answers": [
      "Those are cats. DDDD\tA)\tОн себ аст. Тот яблоко.\nThis is a bag. BBBB\tB)\tИн ҷузвдон аст. Это сумка.\nThat is an apple. AAAA\tC)\tИн нақша аст. Это план.\nThese are dogs. EEEE\tD)\tОнҳо гурбаҳо мебошанд. Те кошки.\n\tE)\tИнҳо сагҳо мебошанд. Эти собаки."
    ]
  },
  {
    "question": "Cаволҳоро бо ҷавобҳо мувофиқат кунонед. Соответствуйте данные вопросы с ответами.",
    "answers": [
      "What is this? FFFF\tA)\tThey are teachers.\nAre they at home? BBBB\tB)\tNo, they are not.\nDo you see this picture? DDDD\tC)\tI like it.\nAre you at work or at home? EEEE\tD)\tNo, I do not.\n\tE)\tI am at home.\n\tF)\tThis is an industrial robot."
    ]
  },
  {
    "question": "Саволҳоро бо ҷавобҳо мувофиқат кунонед. Соответствуйте вопросы с ответами.",
    "answers": [
      "Do you live in a big city? BBBB\tA)\tNo, she does not.\nDoes Anisa study English? FFFF\tB)\tNo, I don`t.\nHave they nice flat? DDDD\tC)\tYes, she did.\nDid she work at the factory? CCCC\tD)\tYes, they have.\n\tE)\tI like a big city.\n\tF)\tShe studies French."
    ]
  },
  {
    "question": "Қисми дуюми саволҳои ҳамраъиро мувофиқат намоед. Соответствуйте вторую часть разделительных вопросов.",
    "answers": [
      "We are right, CCCC\tA)\tis not she?\nThey study English, FFFF\tB)\tsshall not I?hall not they?\nYou live in a hostel, DDDD\tC)\tare not we?\nShuhrat is not a student, EEEE\tD)\tdon`t you?\n\tE)\tis he?\n\tF)\tdo not they?"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳоро мувофиқат кунонед. Соответствуйте перевод данных слов.",
    "answers": [
      "to be absent BBBB\tA)\tминнатдор шудан – благодарить\nto thank AAAA\tB)\tғоиб будан – отсутствовать\nto transfer DDDD\tC)\tтайёр кардан– приготовить\nto prepare CCCC\tD)\tинтиқол кардан – передача"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳоро мувофиқат намоед. Соответствуйте перевод данных слов.",
    "answers": [
      "ҷадвал - таблица BBBB\tA)\ta bill\nҳисоб - счет AAAA\tB)\tshedule\nмаълумот -данные DDDD\tC)\tnumber\nрақам - номер CCCC\tD)\tdata"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳоро мувофиқат кунонед. Соответствуйте перевод данных слов.",
    "answers": [
      "page BBBB\tA)\tдарс - урок\nlesson AAAA\tB)\tсаҳифа - страница\nresources DDDD\tC)\tкиштии кайҳонӣ – космический корабль\nspaceship CCCC\tD)\tзахираҳо – ресурсы"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ кунед: Найдите соответствие следующих слов:",
    "answers": [
      "radio BBBB\tA)\tauthority\nlocal AAAA\tB)\tengineering\nTV- DDDD\tC)\tindicator\nstorm CCCC\tD)\tcenters"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ кунед: Найдите соответствие следующих слов:",
    "answers": [
      "ташкилот-организация\nAAAA\tA)\torganization\nназорат-контроль BBBB\tB)\tcontrol\nсистемаи оператсионӣ-еперационная система \nDDDD\tC)\tlicence\nдастур- инструкция дастур- инструкция EEEE\tD)\toperating system\n\tE)\tinstruction"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ кунед: Определите соответствие следующих слов:",
    "answers": [
      "доно-умный AAAA\tA)\tsmart\nдастур-инструкция BBBB\tB)\tinstuction\nшакли кутоҳкардашуда -ихтисорот DDDD\tC)\tequils\nфармоишот- команда EEEE\tD)\tabbrviation\n\tE)\tcommand"
    ]
  },
  {
    "question": "Ибораҳои зеринро бо ҳам мувофиқ кунед: Определите соответствие следующих словосочетаний:",
    "answers": [
      "enormous implication FFFF\tA)\tмураккаб -сложный\nprominent part BBBB\tB)\tнақши муҳим-важная роль\ncapabilities DDDD\tC)\tворидкунӣ -ввод\nlocal authorities EEEE\tD)\tимкониятҳо- возможности\n\tE)\tҳокимияти маҳаллӣ-местная власть\n\tF)\tпешомадҳои бузург-значительные последствия"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ кунед: Определите соответствие следующих слов:",
    "answers": [
      "to deny CCCC\tA)\tпардохт кардан- платить\nto develop FFFF\tB)\tхона-дом\nto consider DDDD\tC)\tрад кардан- отрицать\nto provide EEEE\tD)\tҳисобидан- пологать\n\tE)\tтаъмин кардан- обепечивать"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ кунед: Определите соответствие следующих слов:",
    "answers": [
      "to кееp up BBBB\tA)\tғанӣ гардонидан- обогащать\nto enrich AAAA\tB)\tдастгирӣ кардан -поддерживать\nto relax DDDD\tC)\tдар бар гирифтан-включать\nto comprise CCCC\tD)\tистироҳат кардан-отдыхать"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "in front of BBBB\tA)\tдар даруни – внутри\nin AAAA\tB)\tдар рӯ ба рӯи – напротив\non DDDD\tC)\tдар назди – у,\nat CCCC\tD)\tдар болои – на"
    ]
  },
  {
    "question": "Пешояндҳоро мувофиқат кунонед: Найдите соответствие следующих предлогов:",
    "answers": [
      "ба – к CCCC\tA)\tunder\nаз – от, из FFFF\tB)\tat\nаз байни – через DDDD\tC)\tto\nба даруни - в EEEE\tD)\tthrough\n\tE)\tinto\n\tF)\tfrom"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "between FFFF\tA)\tдар қафои – зади\nafter BBBB\tB)\tбаъди – после\namong DDDD\tC)\tдар болои – на\nduring EEEE\tD)\tдар байни – среди\n\tE)\tдар вақти – во время\n\tF)\tдар байни – между"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "harmful FFFF\tA)\tбаланд – высокий\nuseful BBBB\tB)\tфоиданок – полезный\ncartoon DDDD\tC)\tнақша – план\nfeature film EEEE\tD)\tфилми тасвирӣ – мультфилм\n\tE)\tфилми бадеӣ – художественный фильм\n\tF)\tзараовар – вредный"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "opportunity CCCC\tA)\tзамонавӣ – современный\ndimension FFFF\tB)\tқулай – удобный\nachievement DDDD\tC)\tимконият – возможность\ncomputing EEEE\tD)\tдастовард - достижение\n\tE)\tҳисобкунӣ-вычисление\n\tF)\tтағйирёбӣ – размеры"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "дар болои миз – на столе\nDDDD\tA)\tin front of the table\nдар зери миз – под столом\nBBBB\tB)\tunder the table\nдар рӯ ба рӯи миз – перед столом AAAA\tC)\tfor the text\nдар қафои миз – за столом\nEEEE\tD)\ton the table\n\tE)\tbehind the table"
    ]
  },
  {
    "question": "Ҷонишинҳоро дар падежи объектӣ мувофиқат кунед: Сопоставьте местоимения в объектном падеже:",
    "answers": [
      "I AAAA\tA)\tme\nshe BBBB\tB)\ther\nhe DDDD\tC)\tit\nthey EEEE\tD)\thim\n\tE)\tthem"
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷонишинҳоро дар падежи объектӣ мувофиқат кунед: Сопоставьте правильный перевод местоимений в объектном падеже:",
    "answers": [
      "me AAAA\tA)\tба ман (мне)\nus BBBB\tB)\tба мо (нам)\nyou DDDD\tC)\tба ӯ (ей)\nhim EEEE\tD)\tба ту (тебе)\n\tE)\tба вай (ему)"
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷонишинҳоро дар падежи объектӣ мувофиқат кунед: Сопоставьте правильный перевод местоимений в объектном падеже:",
    "answers": [
      "Give her AAAA\tA)\tБа ӯ деҳ (дай ей)\nTell us BBBB\tB)\tБа мо гӯй (расскажи нам)\nGive them DDDD\tC)\tБа ман деҳ (дай мне)\nShow him EEEE\tD)\tБа онҳо деҳ (дай им)\n\tE)\tБа ӯ нишон деҳ (покажи ему)"
    ]
  },
  {
    "question": "Ҷумлаҳоро ба охир расонед: Дополните предложения:",
    "answers": [
      "There are some apples DDDD\tA)\tin the bottle?\nThere are some workers BBBB\tB)\tin the factory.\nIs there any water AAAA\tC)\tin the sky.\nThere are some pictures EEEE\tD)\ton the plate.\n\tE)\ton the wall."
    ]
  },
  {
    "question": "Ҷумлаҳоро ба охир расонед: Дополните предложения:",
    "answers": [
      "Ask him DDDD\tA)\tyour article.\nWe can BBBB\tB)\tspeak English.\nShow him CCCC\tC)\the dress.\nDo not tell EEEE\tD)\tsome questions.\n\tE)\tthem."
    ]
  },
  {
    "question": "Ҷумлаҳоро ба охир расонед: Дополните предложения:",
    "answers": [
      "He learns CCCC\tA)\tshe address.\nTell me FFFF\tB)\the pencil.\nBring her DDDD\tC)\tit at home.\nWrite him EEEE\tD)\tsome water.\n\tE)\ta letter.\n\tF)\tyour address."
    ]
  },
  {
    "question": "Ҷавоби дурустро мувофиқат кунонед. Сопоставьте правильный вариант ответа:",
    "answers": [
      "the twenty first DDDD\tA)\tthe 107th\nthe ninety eighth BBBB\tB)\tthe 98th\nthe hundred seventh AAAA\tC)\tthe 120th\nthe fourth EEEE\tD)\tthe 21st\n\tE)\tthe 4th"
    ]
  },
  {
    "question": "Ҷавоби дурустро интихоб кунед: Определите правильный вариант ответа:",
    "answers": [
      "Якшанбеи гузашта– прошлое воскресенье BBBB\tA)\tlast Monday\nДушанбеи гузашта - прошлый понедельник AAAA\tB)\tlast Sunday\nСешанбеи гузашта-прошлый вторник DDDD\tC)\tlast Wednesday\nЧоршанбеи гузашта –прошлая среда CCCC\tD)\tlast Tuesday"
    ]
  },
  {
    "question": "Ҷавоби дурустро интихоб кунед: Определите правильный вариант ответа:",
    "answers": [
      "Чоршанбе-Среда BBBB\tA)\tFriday\nҶумъа- Пятница AAAA\tB)\tWednesday\nПанҷшанбе- Четверг DDDD\tC)\tMonday\nДушанбе - Понедельник CCCC\tD)\tThursday"
    ]
  },
  {
    "question": "Ҷавоби дурустро интихоб кунед. Определите правильный вариант ответа.",
    "answers": [
      "Spring months are: AAAA\tA)\tMarch, April, May.\nSummer months are: BBBB\tB)\tJune, July, August.\nAutumn months are: DDDD\tC)\tMarch, April, October.\nWinter months are: EEEE\tD)\tSeptember, October, November.\n\tE)\tDecember, January, February."
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаро ёбед. Найдите правильный вариант слова.",
    "answers": [
      "today BBBB\tA)\tпагоҳ (завтра)\ntomorrow AAAA\tB)\tимрӯз (сегодня)\nalways DDDD\tC)\tдина (вчера)\nyesterday CCCC\tD)\tҳамеша (всегда)"
    ]
  },
  {
    "question": "Солро мувофиқат кунонед. Сопаставьте года.",
    "answers": [
      "2012 AAAA\tA)\ttwenty twelve\n1754 BBBB\tB)\tseventeen fifty four\n1876 DDDD\tC)\ttwenty twenty\n1987 EEEE\tD)\teighteen seventy six\n\tE)\tnineteen eighty seven"
    ]
  },
  {
    "question": "Феълҳоро дар замони ҳозираи давомдор гузоред: Вставьте глаголы в настоящей продолженной форме:",
    "answers": [
      "camp DDDD\tA)\ttravelling\nswim BBBB\tB)\tswimming\ntravel AAAA\tC)\tplaying\nwrite EEEE\tD)\tcamping\n\tE)\twriting"
    ]
  },
  {
    "question": "Феълҳоро дар замони ҳозираи давомдор гузоред: Вставьте глаголы в настоящей продолженной форме:",
    "answers": [
      "walk CCCC\tA)\tgoing\nhave FFFF\tB)\tworking\nshop DDDD\tC)\twalking\nsleep EEEE\tD)\tshopping\n\tE)\tsleeping\n\tF)\thaving"
    ]
  },
  {
    "question": "Ҷумлаҳоро пурра кунед: Дополните предложения:",
    "answers": [
      "They are playing … CCCC\tA)\tlamp\nI am listening… FFFF\tB)\tpillow\nHer sister is going … DDDD\tC)\tfootball.\nShahlo is playing … EEEE\tD)\tto England.\n\tE)\ton the computer.\n\tF)\tto the radio."
    ]
  },
  {
    "question": "Тарҷумаи дурусти ҷумлаҳоро ёбед:Найдите правильный перевод предложений:",
    "answers": [
      "My friend is driving a car. BBBB\tA)\tЛола дар кӯча бозӣ карда истодааст.Лола играет на улице.\nLola is playing in the street. AAAA\tB)\tРафиқи ман мошин ронда истодааст.Мой друг водит машину.\nYou are working at our designs. DDDD\tC)\tМан ҳикояи шавқовар хонда истодаам.Я читаю интересный рассказ.\nI am reading an interesting story. CCCC\tD)\tШумо аз болои лоиҳаамон кор бурда истодаед. Вы работаете над нашим проектом."
    ]
  },
  {
    "question": "Ҷумлаҳоро пурра кунед: Дополните предложения:",
    "answers": [
      "I am not doing my... BBBB\tA)\tmagazine.\nMy mum is reading a ... AAAA\tB)\thomework.\nThey are listening to ... DDDD\tC)\tthe phone.\nDilshodjon is talking on ... CCCC\tD)\tthe speaker."
    ]
  },
  {
    "question": "Ҷумлаҳоро пурра кунед: Дополните предложения:",
    "answers": [
      "We are not writing ... BBBB\tA)\tdinner.\nShe is not cooking ... AAAA\tB)\ta dictation.\nNick is not playing ... DDDD\tC)\ta car.\nThe driver is not driving ... CCCC\tD)\tthe piano."
    ]
  },
  {
    "question": "Ҷумлаҳоро ба ҳам мувофиқ оред: Соответствуйте данные предложения:",
    "answers": [
      "His friend goes shopping… AAAA\tA)\twith me.\nThey go to Moscow… BBBB\tB)\tby plane.\nI study at the… DDDD\tC)\ttree.\nWe sometimes use a dictionary…. EEEE\tD)\tUniversity.\n\tE)\tin class."
    ]
  },
  {
    "question": "Ҷумлаҳоро мувофиқат кунонед: Соответствуйте данные предложения:",
    "answers": [
      "Do the students eat… FFFF\tA)\tto collect?\nWhat time does the sun ... BBBB\tB)\trise?\nDoes he go to your party… DDDD\tC)\tto join?\nDoes university finish…. EEEE\tD)\ton Saturday?\n\tE)\tat two o`clock?\n\tF)\tin the canteen?"
    ]
  },
  {
    "question": "Ҷумлаҳои зеринро мувофиқат кунонед: Соответствуйте данные предложения:",
    "answers": [
      "Does your sister… CCCC\tA)\ton Saturday?\nDo you live… FFFF\tB)\this line?\nDoes the teacher… DDDD\tC)\tgo to the university?\nDo the students wear a uniform… AAAA\tD)\tuse a computer?"
    ]
  },
  {
    "question": "Ҷумлаҳоро мувофиқат кунонед: Соответствуйте данные предложения:",
    "answers": [
      "She plays… BBBB\tA)\tin a big office.\nHe works… AAAA\tB)\tbasketball.\nThe earth goes… DDDD\tC)\tto China every year.\nMy friend goes… CCCC\tD)\taround the sun."
    ]
  },
  {
    "question": "Ҷумлаҳои мувофиқро интихоб намоед: Соответствуйте данные предложения:",
    "answers": [
      "Do your friends live… DDDD\tA)\tflat with his parents.\nDoes he like… BBBB\tB)\treading?\nOhunjon lives in a… AAAA\tC)\twatch TV.\nHe has two daughters… EEEE\tD)\tin Khujand?\n\tE)\tand one son."
    ]
  },
  {
    "question": "Ҷумлаҳоро бо ҳам мувофиқат кунонед: Соответствуйте данные предложения:",
    "answers": [
      "I get up at… CCCC\tA)\tto describe.\nYou work … FFFF\tB)\tto understand.\nThe children like… DDDD\tC)\t5 o`clock every morning.\nI study… EEEE\tD)\ta lot of toys.\n\tE)\tFrench."
    ]
  },
  {
    "question": "Ҷумлаҳои зеринро бо ҳам мувофиқат кунонед. Найдите соответствие данных предложений.",
    "answers": [
      "It is raining you must FFFF\tA)\tmay go out.\nSorry, I must go now BBBB\tB)\tI don’t want to be late.\nRuina can DDDD\tC)\tobey orders.\nThe children must EEEE\tD)\tdance well.\n\tE)\tsleep early.\n\tF)\ttake your umbrella."
    ]
  },
  {
    "question": "Ҷумлаҳои зеринро бо ҳам мувофиқат кунонед. Найдите соответствие данных предложений.",
    "answers": [
      "May I open... BBBB\tA)\tto the cinema with you?\nCan I go... AAAA\tB)\tthe door?\nMust I do... DDDD\tC)\tspeak English?\nCan you... CCCC\tD)\tthis home-work?"
    ]
  },
  {
    "question": "Ҷумлаҳои зеринро бо ҳам мувофиқат кунонед. Найдите соответствие данных предложений.",
    "answers": [
      "I cannot read DDDD\tA)\tcan help you.\nI can go to bed BBBB\tB)\tvery early.\nI’m not sure, but I AAAA\tC)\tsports hall.\nI can play EEEE\tD)\tEnglish books.\n\tE)\tthe guitar."
    ]
  },
  {
    "question": "Ҷумлаҳои зеринро бо ҳам мувофиқат кунонед. Найдите соответствие данных предложений.",
    "answers": [
      "Zumrad can... CCCC\tA)\tneed to do every night.\nWe must speak... FFFF\tB)\tmay sleep.\nHe may go... DDDD\tC)\tmake a report.\nThey may make... EEEE\tD)\thome early.\n\tE)\ta lot of mistakes.\n\tF)\tEnglish at the lesson."
    ]
  },
  {
    "question": "Ҷумлаҳои зеринро бо ҳам мувофиқат кунонед. Найдите соответствие данных предложений.",
    "answers": [
      "We must not... CCCC\tA)\tnowadays.\nYou must not go... EEEE\tB)\tmust do this.\nI can not put... DDDD\tC)\tbe in a hurry.\nWe can not go... FFFF\tD)\tthe book here. Sorry.\n\tE)\tto the party.\n\tF)\tto visit your grandmother."
    ]
  },
  {
    "question": "Ҷумлаҳои зеринро бо ҳам мувофиқат кунонед. Найдите соответствие данных предложений.",
    "answers": [
      "She may be... EEEE\tA)\ta new TV.\nHe may take... BBBB\tB)\tthis book.\nYou may buy... AAAA\tC)\tfamous people.\nShe may... DDDD\tD)\tat the lesson.\n\tE)\tcome today."
    ]
  },
  {
    "question": "Сифат ва дараҷаҳои қиёсии онҳоро мувофиқ намоед: Найдите соответствия степеней сравнения прилагательных:",
    "answers": [
      "fast DDDD\tA)\tharder\nsmall BBBB\tB)\tsmaller\nhard AAAA\tC)\tbigger\nsimple EEEE\tD)\tfaster\n\tE)\tsimpler"
    ]
  },
  {
    "question": "Сифат ва дараҷаҳои қиёсии онҳоро мувофиқ намоед: Найдите соответствия степеней сравнения прилагательных:",
    "answers": [
      "large BBBB\tA)\tlighter\nlight AAAA\tB)\tlarger\nold DDDD\tC)\ttaller\ntall CCCC\tD)\tolder"
    ]
  },
  {
    "question": "Сифат ва дараҷаҳои қиёсии онҳоро мувофиқ намоед: Найдите соответствия степеней сравнения прилагательных:",
    "answers": [
      "good AAAA\tA)\tbetter\nbad BBBB\tB)\tworse\nmany DDDD\tC)\tleast\nlittle EEEE\tD)\tmore\n\tE)\tless"
    ]
  },
  {
    "question": "Сифат ва дараҷаҳои олии онҳоро мувофиқ намоед: Найдите соответствия превосходных степеней прилагательных:",
    "answers": [
      "difficult DDDD\tA)\tthe most interesting\nexpensive BBBB\tB)\tthe most expensive\ninteresting AAAA\tC)\tthe best\nimportant EEEE\tD)\tthe most difficult\n\tE)\tthe most important"
    ]
  },
  {
    "question": "Тарҷумаи сифатҳоро муайян кунед: Определите перевод данных прилагательных:",
    "answers": [
      "heavy CCCC\tA)\tдароз (длинный)\ndifficult FFFF\tB)\tбаланд (высокий)\nfamous DDDD\tC)\tвазнин (тяжелый)\nweak EEEE\tD)\tмашҳур (известный)\n\tE)\tсуст (медлинный)\n\tF)\tдушвор (трудный)"
    ]
  },
  {
    "question": "Тарҷумаи сифатҳоро муайян кунед: Определите перевод данных прилагательных:",
    "answers": [
      "тез (быстро) BBBB\tA)\trare\nноёб (редкий) AAAA\tB)\tfast\nбад (плохой) DDDD\tC)\tgood\nхуб (хороший) CCCC\tD)\tbad"
    ]
  },
  {
    "question": "Феълҳоро дар замони гузаштаи номуайян мувофиқат кунонед. Соответствуйте формы глаголов в прошедшем неопределенном времени:",
    "answers": [
      "to begin CCCC\tA)\tblown\nto blow FFFF\tB)\tbegunblown\nto bring DDDD\tC)\tbegan\nto buy EEEE\tD)\tbrought\n\tE)\tbought\n\tF)\tblew"
    ]
  },
  {
    "question": "Шакли феълҳоро дар замони гузашта мувофиқат намоед. – Соответствуйте формы глаголов в прошедшем неопределенном времени.",
    "answers": [
      "to do CCCC\tA)\tis\nto be FFFF\tB)\tplay\nto write DDDD\tC)\tdid\nto go EEEE\tD)\twrote\n\tE)\twent\n\tF)\twas, were"
    ]
  },
  {
    "question": "Шакли феълҳоро дар замони гузаштаи номуайн мувофиқат намоед. Соответствуйте формы глаголов в прошедшем времени.",
    "answers": [
      "to like CCCC\tA)\tloved\nto dress FFFF\tB)\tworking\nto live DDDD\tC)\tliked\nto work EEEE\tD)\tlived\n\tE)\tworked\n\tF)\tdressed"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳоро мувофиқат кунонед. Соответствуйте перевод данных слов.",
    "answers": [
      "to store CCCC\tA)\tхатм кардан – окончить\nto solve FFFF\tB)\tхориҷ кардан – исключать\nto conduct DDDD\tC)\tнигоҳ доштан - сохранить\nto define EEEE\tD)\tидора кардан - руководить\n\tE)\tмуайян кардан - определить\n\tF)\tҳал кардан - решать"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳоро бо ҳам мувофиқат кунонед. – Соответствуйте перевод данных слов.",
    "answers": [
      "demand FFFF\tA)\tроҳи зеризаминӣ – метро\ncomputer BBBB\tB)\tкомпютер - компютер\nradio DDDD\tC)\tкор - работа\nTV- set EEEE\tD)\tрадио – радио\n\tE)\tоинаи нилгун - телевизор\n\tF)\tталаб – требование"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳоро мувофикат кунед. Соответствуйте перевод данных слов.",
    "answers": [
      "ихтисос -профессия DDDD\tA)\telectricity\nаъзо - член BBBB\tB)\tmember\nбарқ - электричество AAAA\tC)\torganize\nташкилот - организация EEE\tD)\tprofession\n\tE)\torganization"
    ]
  },
  {
    "question": "Ибораҳоро мувофиқат намоед. Найдите соответствие данных словосочетаний.",
    "answers": [
      "B. Gafurov is... AAAA\tA)\ta glorious son.\nA.Popov invented BBBB\tB)\tradio.\nB.Gates is ... DDDD\tC)\ttelevision.\nA.Bell invented EEEE\tD)\tthe inventor of Microsoft Windows.\n\tE)\tthe conventional telephone."
    ]
  },
  {
    "question": "Калима ва ибораҳоро бо ҳам мувофиқат намоед. Найдите соответствие данных слов и словосочетаний.",
    "answers": [
      "the great BBBB\tA)\tat the University\nto study AAAA\tB)\tinventor\nlife and DDDD\tC)\tprogramist\nthe first FFFF\tD)\tcreative work\n\tE)\tat work\n\tF)\tpen"
    ]
  },
  {
    "question": "Ибораҳоро мувофиқат намоед. Найдите соответствие данных слов и словосочетаний.",
    "answers": [
      "to bring up FFFF\tA)\tнигоҳубин кардан -присматривать\nto choose BBBB\tB)\tинтихоб намудан - выбирать\nto depict DDDD\tC)\tэҷод кардан - сочинять\nto live EEEE\tD)\tтасвир кардан - описывать\n\tE)\tзиндагӣ намудан - жить\n\tF)\tба воя расонидан - растить"
    ]
  },
  {
    "question": "Калимаҳоро мувофиқат намоед. Найдите соответствие данных слов.",
    "answers": [
      "мақола- статья DDDD\tA)\trole\nбарномасоз- програмист BBBB\tB)\tprogrammist\nнақш - роль AAAA\tC)\twriter\nқувва - сила EEEE\tD)\tarticle\n\tE)\tpower"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқат кунед. Найдите соответствие данных слов.",
    "answers": [
      "thankful AAAA\tA)\tминнатдор - благодарный\ncreative BBBB\tB)\tэҷодӣ - творческий\ndifficult DDDD\tC)\tзебо - красивый\ntalented EEEE\tD)\tдушвор - трудный\n\tE)\tистеъдоднок - талантливый"
    ]
  },
  {
    "question": "Саволҳоро бо ҷавобҳо мувофиқат намоед. Соответствуйте вопросы с ответами.",
    "answers": [
      "What is mobile phone? DDDD\tA)\tYes, I do.\nMay you use your phone during the lesson? BBBB\tB)\tNo, I may not.\nDo you have a phone? AAAA\tC)\tMobile phone is a useless device.\nAre modern mobile phones multi-functions? EEEE\tD)\tMobile phone is a useful device.\n\tE)\tYes, they are."
    ]
  },
  {
    "question": "Калимаҳои мувофиқро ёбед: Найдите соответствующие слова:",
    "answers": [
      "never CCCC\tA)\talways (всегда)\never FFFF\tB)\tusually (обычно)\nalready DDDD\tC)\tҳеҷгоҳ (никогда)\njust EEEE\tD)\tаллакай ( уже )\n\tE)\tҳозиракак (только что)\n\tF)\tягон бор (когда-либо)"
    ]
  },
  {
    "question": "Калимаҳои мувофиқро ёбед: Найдите соответствующие слова:",
    "answers": [
      "анъана (традиция) DDDD\tA)\tcelebration\nид (праздник) BBBB\tB)\tholiday\nҷашнгирӣ (празднование) AAAA\tC)\tchurch\nсолгард (годовщина) EEEE\tD)\ttradition\n\tE)\tanniversary"
    ]
  },
  {
    "question": "Калимаҳои мувофиқро ёбед: Найдите соответствующие слова:",
    "answers": [
      "to go for a walk CCCC\tA)\tдоштан (иметь)\nto enjoy FFFF\tB)\tбудан (иметь)\nto live in a hostel DDDD\tC)\tба сайру гашт рафтан (идти на прогулку)\nto control EEEE\tD)\tдар хобгоҳ зиндагӣ кардан (жить в общежитие)\n\tE)\tназорат кардан (контролировать)\n\tF)\tҳаловат бурдан) (наслаждаться)"
    ]
  },
  {
    "question": "Калимаҳои мувофиқро ёбед: Найдите соответствующие слова:",
    "answers": [
      "to imagine AAAA\tA)\tтасаввур кардан (представить)\nto come back BBBB\tB)\tбаргаштан (возвращаться)\nto be glad DDDD\tC)\tбоварӣ ҳосил кардан (быть уверенным)\nto have an opportunity EEEE\tD)\tхурсанд будан (радоваться)\n\tE)\tимконият доштан (иметь возможность)"
    ]
  },
  {
    "question": "Калимаҳои мувофиқро ёбед: Найдите соответствующие слова:",
    "answers": [
      "to check DDDD\tA)\tҳозир набудан (отсуствовать)\nto master BBBB\tB)\tаз худ намудан (освоить)\nto miss AAAA\tC)\tдоимо (всегда)\nto end EEEE\tD)\tтафтиш кардан (проверять)\n\tE)\tба охир расидан (заканчивать)"
    ]
  },
  {
    "question": "Калимаҳои мувофиқро ёбед: Найдите соответствующие слова:",
    "answers": [
      "табрик кардан (поздравлять)\nCCCC\tA)\tto dress\nташриф овардан (посещать)\nFFFF\tB)\tto get\nистифода бурдан (использовать) DDDD\tC)\tto congratulate\nистироҳат кардан (отдыхать)\nEEEE\tD)\tto use\n\tE)\tto have a rest\n\tF)\tto attend"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ намоед. Найдите перевод слов.",
    "answers": [
      "барнома -программа FFFF\tA)\tcultural\nтаҷҳизот -оборудование BBBB\tB)\tdevice\nмавҷқапак -антенна DDDD\tC)\teducational\nахборот -новости EEEE\tD)\tantenna\n\tE)\tnews\n\tF)\tprogram"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ намоед. Найдите перевод слов.",
    "answers": [
      "to celebrate BBBB\tA)\tсохтан - строить\nto build AAAA\tB)\tҷашн гирифтан - праздновать\nto continue DDDD\tC)\tистеҳсол кардан - производить\nto produce CCCC\tD)\tдавом додан - продолжать"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ намоед. Найдите перевод слов.",
    "answers": [
      "seldom BBBB\tA)\tҳамеша - всегда\nalways AAAA\tB)\tбаъзан - редко\nnever DDDD\tC)\tҳар рӯз - каждый день\nevery day CCCC\tD)\tҳеҷ гоҳ - никогда"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ намоед. Найдите перевод слов.",
    "answers": [
      "фоидаовар - полезный CCCC\tA)\tyoung\nдилгиркунанда - скучный FFFF\tB)\tcage\nасосӣ - основной DDDD\tC)\tuseful\nзараровар- вредный EEEE\tD)\tmain\n\tE)\tharmful\n\tF)\tboredom"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ намоед. Найдите перевод слов.",
    "answers": [
      "пойтахт - столица FFFF\tA)\tvillage\nОсиёи Миёна – Средняя Азия BBBB\tB)\tCentral Asia\nмамлакат - страна DDDD\tC)\tuniversity\nшаҳр - город EEEE\tD)\tcountry\n\tE)\ttown\n\tF)\tcapital"
    ]
  },
  {
    "question": "Калимаҳои зидмаъноро мувофиқат намоед. Найдите антонимы слов.",
    "answers": [
      "leave DDDD\tA)\tstop\nhopeless BBBB\tB)\thopefull\ncontinue AAAA\tC)\tfrequently\nmain EEEE\tD)\tstay\n\tE)\tless important"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "ғоибона -заочный FFFF\tA)\thigher\nрӯзона –дневной BBBB\tB)\tfull-time\nшабона – вечерний DDDD\tC)\tvocational\nҳатмӣ - обязательный EEEE\tD)\tevening -part\n\tE)\tcompulsory\n\tF)\tpart- time"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "дар бар гирифтан -включать\nDDDD\tA)\tto enter\nқабул кардан-принять BBBB\tB)\tto accept\nдохил шудан- поступать AAAA\tC)\tto go\nхатм кардан-окончить EEEE\tD)\tto include\n\tE)\tto graduate"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "dean AAAA\tA)\tдекан - декан\nstudent BBBB\tB)\tдонишҷӯ-студент\nprofessor DDDD\tC)\tроҳбар -руководитель\nteacher EEEE\tD)\tпрофессор -профессор\n\tE)\tомӯзгор -учитель"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "to enter DDDD\tA)\tназорат кардан – контролировать\nto accept BBBB\tB)\tқабул шудан-принять\nto monitor AAAA \tC)\tколлеҷ - колледж\nto carry out EEEE\tD)\tдохил шудан - поступать\n\tE)\tиҷро кардан - делать"
    ]
  },
  {
    "question": "Муродифи тоҷикии калимаҳоро мувофиқат намоед:",
    "answers": [
      "to design DDDD\tA)\tидора кардан\nto transfer BBBB\tB)\tинтиқол кардан\nto manupulate AAAA\tC)\tдоштан\nto convert EEEE\tD)\tпешаки таъин кардан\n\tE)\tтабдил додан"
    ]
  },
  {
    "question": "Муродифи тоҷикии калимаҳоро ёбед:",
    "answers": [
      "to imagine AAAA\tA)\tтасаввур кардан\nto come back BBBB\tB)\tбаргаштан\nto be glad DDDD\tC)\tбоварӣ ҳосил кардан\nto have an opportunity EEEE\tD)\tхурсанд будан\n\tE)\tимконият доштан"
    ]
  },
  {
    "question": "Калимаҳои мувофиқро ёбед: Найдите соответствующие слова:",
    "answers": [
      "to check BBBB\tA)\tаз худ намудан\nto master AAAA\tB)\tтафтиш кардан\nto miss DDDD\tC)\tба охир расидан\nto end CCCC\tD)\tҳозир набудан"
    ]
  },
  {
    "question": "Калимаҳои мувофиқро ёбед: Найдите соответствующие слова:",
    "answers": [
      "табрик кардан AAAA\tA)\tto congratulate\nташриф овардан BBBB\tB)\tto attend\nистифода бурдан DDDD\tC)\tto dress\nистироҳат кардан EEEE\tD)\tto use\n\tE)\tto have a rest"
    ]
  },
  {
    "question": "Калимаҳоро бо ҳам мувофиқ намоед. Найдите перевод слов.",
    "answers": [
      "барнома BBBB\tA)\tdevice\nтаҷҳизот AAAA\tB)\tprogram\nмавҷқапак DDDD\tC)\tnews\nахбор CCCC\tD)\tantenna"
    ]
  },
  {
    "question": "Калимаҳои зеринро мувофиқат кунонед: Найдите соответствие следующих слов:",
    "answers": [
      "вазифа DDDD\tA)\trole\nҳодиса BBBB\tB)\taccident\nнақш AAAA\tC)\ttelltale\nфазо EEEE\tD)\ttask\n\tE)\tspace"
    ]
  },
  {
    "question": "Калимаҳои зеринро ба ҳам мувофиқат кунонед. Соотвествуйте слова.",
    "answers": [
      "late FFFF\tA)\tбодиққат- внимательно\npretty BBBB\tB)\tзебо – красивая\nhard DDDD\tC)\tқариб – почти\nfast EEEE\tD)\tсахт – твёрдый\n\tE)\tтез – быстро\n\tF)\tдер - поздно"
    ]
  },
  {
    "question": "Феълҳоро мутобиқ намоед. Соотвествуйте глаголы.",
    "answers": [
      "to remove FFFF\tA)\tмушоҳида кардан – наблюдать\nto be obliged BBBB\tB)\tмаҷбур шудан – быть принужденный\nto set DDDD\tC)\tмуқоиса кардан – сравнивать\nto devote EEEE\tD)\tгузоштан – положить\n\tE)\tбахшидан – прощать\n\tF)\tбартараф кардан – устранить"
    ]
  },
  {
    "question": "Ба саволҳои зерин ҷавоби дуруст ёбед. Найдите правильные ответы на эти вопросы.",
    "answers": [
      "Are computers getting deeper into our life? CCCC\tA)\tMy computer.\nWhose idea was it to use computers? FFFF\tB)\tNo, they don`t.\nWhat role does computer play in our life? DDDD\tC)\tYes, they are.\nDo you have your own computers at home? EEEE\tD)\tAn important role.\n\tE)\tYes, I do.\n\tF)\tMine."
    ]
  },
  {
    "question": "Тарҷумаи феълҳои сутуни чапро аз сутуни рост ёбед. Найдите перевод глаголов левого столбца из правого столбца.",
    "answers": [
      "to play DDDD\tA)\tкор кардан – работать\nto compare BBBB\tB)\tмуқоиса кардан – сравнивать\nto work AAAA\tC)\tшикор кардан - охотиться\nto lay FFFF\tD)\tбозӣ кардан – играть\n\tE)\tгузоштан- поставить\n\tF)\tмондан – положить"
    ]
  },
  {
    "question": "Тарҷумаи сифатҳои зеринро мувофиқ намоед. Сопоставьте перевод следующих прилогательных.",
    "answers": [
      "намуд – тип FFFF\tA)\tuseful\nгуногуншакл – различный BBBB\tB)\tvarious\nкомил- идеальный DDDD\tC)\timprovement\nбефоида – бесполезный EEEE\tD)\tperfect\n\tE)\tuseless\n\tF)\tkind"
    ]
  },
  {
    "question": "Калимаҳоро мувофиқ намоед. Соответствуйте слова.",
    "answers": [
      "language CCCC\tA)\tасос – основа\ntime FFFF\tB)\tмуҳим – важный\nresource DDDD\tC)\tзабон – язык\namount EEEE\tD)\tзахира – ресурсы\n\tE)\tмиқдор – количество\n\tF)\tвақт – время"
    ]
  },
  {
    "question": "Тарҷумаи дурусти ибораҳоро мувофиқат намоед. Соответствуйте правильные словасочитание.",
    "answers": [
      "амал кардан- действовать DDDD\tA)\tto require\nҳисоб кардан – вычислять BBBB\tB)\tto account\nталаб кардан – требовать AAAA\tC)\tto move\nистифода бурдан – использовать EEEE\tD)\tto act\n\tE)\tto apply"
    ]
  },
  {
    "question": "Ҷумларо пурра кунед. Дополните предложения.",
    "answers": [
      "Charles Babbage, a professor of mathematics… FFFF\tA)\torphaned.\nCharles Babbage invented the first… BBBB\tB)\tcalculating machine in 1812.\nNo man alive can do… DDDD\tC)\ttreatment.\nDoctors feed data on symptoms … EEEE\tD)\t500000 operations in the second.\n\tE)\tin the computer.\n\tF)\tat Cambridge University."
    ]
  },
  {
    "question": "Тарҷумаи калимаҳои сутуни чапро аз сутуни рост ёбед. Найдите перевод слова левого столбца из правого столбца.",
    "answers": [
      "ихтироот – изобретения AAAA\tA)\tinvention\nамалиёт – операция BBBB\tB)\toperation\nмаълумот – информация DDDD\tC)\texhibition\nисбот – доказательство EEEE\tD)\tinformation\n\tE)\tillustration"
    ]
  },
  {
    "question": "Ибораҳои додашударо пурра кунед. Дополните словасочитание.",
    "answers": [
      "great EEEE\tA)\talive\nmodern FFFF\tB)\tbe wonderful\ncomputer CCCC\tC)\timportance\ncorrect DDDD\tD)\tcenters\n\tE)\tdiagnostics\n\tF)\thospitals"
    ]
  },
  {
    "question": "Ибораҳои додашударо пурра кунед. Дополните словасочитание.",
    "answers": [
      "Mass AAAA\tA)\tMedia\nthe great BBBB\tB)\tprogress\nan accurate DDDD\tC)\tpoor\na language EEEE\tD)\tcalculations\n\tE)\ttranslation"
    ]
  },
  {
    "question": "Тарҷумаи дурусти калимаҳоро мувофиқат намоед. Соответствуйте правильный перевод слов.",
    "answers": [
      "умумиҷаҳонӣ – всемирная CCCC\tA)\tmusic\nсайёра – планета FFFF\tB)\tsong\nқувва- сила DDDD\tC)\tuniversal\nфикр - идея EEEE\tD)\tforce\n\tE)\tidea\n\tF)\tplanet"
    ]
  },
  {
    "question": "Калимаҳоро мувофиқ кунед. Соответствуйте слова.",
    "answers": [
      "амалан – на деле BBBB\tA)\tin fact\nдар ҳақиқат – действительно AAAA\tB)\tpractically\nҳамин тавр – таким образом\nDDDD\tC)\tat once\nфавран – немедленно CCCC\tD)\tthus"
    ]
  },
  {
    "question": "Феълҳои додашударо пурра кунед. Дополните данные глаголы.",
    "answers": [
      "таркиб ёфтан – быть сформированнытаркиб ёфтан – быть сформированны BBBB\tA)\tto restate\nаз нав дида баромадан – заново рассмотреть AAAA\tB)\tto consist of\nдарк кардан – познание DDDD\tC)\tto embrace\nфаро гирифтан – охватывать\nCCCC\tD)\tbe aware of"
    ]
  },
  {
    "question": "Ибораҳои додашударо мувофиқат кунед. Соответствуйте данные фразы.",
    "answers": [
      "gigantic DDDD\tA)\tpublication\nexisting CCCC\tB)\tword\nscientific EEEE\tC)\tsuited\nactual AAAA\tD)\ttask\n\tE)\ttutor"
    ]
  },
  {
    "question": "Ҷумлаҳои зеринро бо ҳам мувофиқат кунед. Найдите соответствие данных предложений.",
    "answers": [
      "DOS is the most commonly used PC… CCCC\tA)\tsoftware.\nDOS was developed by a company named… FFFF\tB)\thardware.\nMS-DOS is an abbreviation  for… DDDD\tC)\toperating system.\nPC-DOS and MS-DOS are… EEEE\tD)\t“Microsoft DOS”.\n\tE)\tthe same.\n\tF)\tMicrosoft."
    ]
  },
  {
    "question": "Тарҷумаи калимаҳои зеринро бо ҳам мувофиқат кунед. Сопоставьте перевод данных слов.",
    "answers": [
      "percent AAAA\tA)\tфоиз (процент)\nprocessor BBBB\tB)\tпротсессор (процессор)\nmouse DDDD\tC)\tаломат (знак)\nkeyboard EEEE\tD)\tмушак (мыщь)\n\tE)\tклавиатура (клавиатура)"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳои зеринро бо ҳам мувофиқат кунед. Сопоставьте перевод данных слов.",
    "answers": [
      "to translate BBBB\tA)\tиҷро намудан (делать)\nto perform AAAA\tB)\tтарҷума кардан (переводить)\nto manage DDDD\tC)\tиваз кардан (изменить)\nto change CCCC\tD)\tидора кардан (регулировать)"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳои зеринро бо ҳам мувофиқат кунед. Сопоставьте перевод данных слов.",
    "answers": [
      "problem CCCC\tA)\tбаробар (равный)\ndata FFFF\tB)\tтақсим (деление)\nsystem DDDD\tC)\tмуаммо (проблема)\naction EEEE\tD)\tсистема (система)\n\tE)\tамал (действие)\n\tF)\tмаълумот (информация)"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳои зеринро бо ҳам мувофиқат кунед. Сопоставьте перевод данных слов.",
    "answers": [
      "instruction BBBB\tA)\tарзиш, нарх (цена)\ncost AAAA\tB)\tдастур (инструкция)\ngain DDDD\tC)\tҷамъият (общество)\nsociety CCCC\tD)\tфоида (прибыл)"
    ]
  },
  {
    "question": "Тарҷумаи калимаҳои зеринро бо ҳам мувофиқат кунед. Сопоставьте перевод данных слов.",
    "answers": [
      "formula AAAA\tA)\tформула (формула)\nwave BBBB\tB)\tмавҷ (волна)\nspace DDDD\tC)\tаҷдодон (поколение)\nexistence EEEE\tD)\tфазо (поверхность)\n\tE)\tмавҷудият (существование)"
    ]
  },
  {
    "question": "Ибораҳоро мутобиқ намоед. Поставьте соответсвующие фразы.",
    "answers": [
      "to know about FFFF\tA)\telectronic\nto draw BBBB\tB)\tpictures\nto have DDDD\tC)\ttranslator\nto play EEEE\tD)\tan opportunity\n\tE)\tcomputer games\n\tF)\tthe programs"
    ]
  },
  {
    "question": "Ба саволҳои зерин ҷавоби дуруст ёбед. Выберите правильный ответ к этому вопросу.",
    "answers": [
      "Do the computers prepare laboratory tests? BBBB\tA)\tYes, I can.\nCan you use a computer? AAAA\tB)\tYes, they do.\nDo you need a computer when you visit your doctor? DDDD\tC)\tYes, we are.\nAre we all on the way to become computer literate? CCCC\tD)\tYes, I do."
    ]
  },
  {
    "question": "Тарҷумаи феълҳои сутуни чапро аз сутуни рост ёбед. Найдите правильный перевод глаголов.",
    "answers": [
      "to search AAAA\tA)\tкофтуков кардан\nto retrieve BBBB\tB)\tбаргардонидан, гирифтан\nto exchange DDDD\tC)\tинтиқол кардан\nto browse EEEE\tD)\tиваз кардан\n\tE)\tаз назар гузаронидан"
    ]
  },
  {
    "question": "Ҷавоби дурустро интихоб кунед. Выберите правильный ответ.",
    "answers": [
      "Inputting is the process of… AAAA\tA)\tentering data.\nOutputting is the process of... BBBB\tB)\tproducing useful information.\nStoring is the process of … DDDD\tC)\twriting language symbols.\nControlling is the process of … EEEE\tD)\tsaving data or information.\n\tE)\tdirecting the manner and sequence."
    ]
  },
  {
    "question": "Ҷавоби дурустро мувофиқ намоед. Выберите правильный ответ.",
    "answers": [
      "Radio and television play … AAAA\tA)\tan important role.\nThe main aim of radio is to give information … BBBB\tB)\tconcerning life in our planet.\nMobile phone is a very… DDDD\tC)\tto be bored.\nWe take mobile phone to use it … EEEE\tD)\tuseful device.\n\tE)\teverywhere."
    ]
  },
  {
    "question": "Ба саволҳои зерин ҷавоби дуруст ёбед. Выберите правильный ответ к этому вопросу.",
    "answers": [
      "What do operating systems control and manage? CCCC\tA)\t“OS – DOS”\nWhat is an abbreviation for “Microsoft DOS? FFFF\tB)\tcomputers.\nWhat means of telecommunication do you know? DDDD\tC)\tThe use of hardware devices.\nWhat technology made a great contribution to a long range comminication? EEEE\tD)\tThe internet, phones, telegraph, radio, television.\n\tE)\tWireless technology.\n\tF)\t“MS – DOS”."
    ]
  },
  {
    "question": "Тарҷумаи сифатҳои зеринро мувофиқ намоед. Найдите соответствие следующих прилагательных.",
    "answers": [
      "attractive CCCC\tA)\tмулоим (мягкий)\ncurly FFFF \tB)\tбосалиқа (изысканный)\ndreamy DDDD \tC)\tҷозибанок (привлекательный)\npleasant EEEE\tD)\tандешаманд (мечтательный)\n\tE)\tситорагарм (приятный, милый)\n\tF)\tҷингила (кудрявый)"
    ]
  }
        ];

        const container = document.getElementById('qa-container');
        const searchInput = document.getElementById('search-input');

        // Функция для отображения вопросов и ответов
        function displayQA(filteredData) {
            container.innerHTML = ''; // Очищаем контейнер

            filteredData.forEach(item => {
                const questionElement = document.createElement('div');
                questionElement.className = 'question';
                questionElement.textContent = item.question;

                const answersList = document.createElement('ul');
                answersList.className = 'answers';

                item.answers.forEach(answer => {
                    const answerItem = document.createElement('li');
                    answerItem.textContent = answer;
                    answersList.appendChild(answerItem);
                });

                container.appendChild(questionElement);
                container.appendChild(answersList);
            });
        }

        // Событие для поиска
        searchInput.addEventListener('input', () => {
            const query = searchInput.value.toLowerCase();
            const filteredData = data.filter(item =>
                item.question.toLowerCase().includes(query) ||
                item.answers.some(answer => answer.toLowerCase().includes(query))
            );
            displayQA(filteredData);
        });

        // Отображаем все вопросы при загрузке
        displayQA(data);
    </script>
</body>
</html>
