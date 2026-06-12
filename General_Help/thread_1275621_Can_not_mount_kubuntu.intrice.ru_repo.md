---
title: "Can not mount kubuntu.intrice.ru repo"
date: 2009-09-26
forum: General Help
---

### Post by ivanhoe75 on 2009-09-26
I've found key file, registered it but look this:
manually site is accessible for brouser


W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/Release.gpg](http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/Release.gpg)  &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; IP &#1072;&#1076;&#1088;&#1077;&#1089; &#1076;&#1083;&#1103; http

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/restricted/i18n/Translation-ru.bz2](http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/restricted/i18n/Translation-ru.bz2)  &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; IP &#1072;&#1076;&#1088;&#1077;&#1089; &#1076;&#1083;&#1103; http

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/main/i18n/Translation-ru.bz2](http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/main/i18n/Translation-ru.bz2)  &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; IP &#1072;&#1076;&#1088;&#1077;&#1089; &#1076;&#1083;&#1103; http

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/multiverse/i18n/Translation-ru.bz2](http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/multiverse/i18n/Translation-ru.bz2)  &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; IP &#1072;&#1076;&#1088;&#1077;&#1089; &#1076;&#1083;&#1103; http

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/universe/i18n/Translation-ru.bz2](http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/universe/i18n/Translation-ru.bz2)  &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; IP &#1072;&#1076;&#1088;&#1077;&#1089; &#1076;&#1083;&#1103; http

W: &#1053;&#1077;&#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1080;&#1085;&#1076;&#1077;&#1082;&#1089;&#1085;&#1099;&#1077; &#1092;&#1072;&#1081;&#1083;&#1099; &#1085;&#1077; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1083;&#1080;&#1089;&#1100;, &#1086;&#1085;&#1080; &#1073;&#1099;&#1083;&#1080; &#1087;&#1088;&#1086;&#1080;&#1075;&#1085;&#1086;&#1088;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1099; &#1080;&#1083;&#1080; &#1074;&#1084;&#1077;&#1089;&#1090;&#1086; &#1085;&#1080;&#1093; &#1073;&#1099;&#1083;&#1080; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1099; &#1089;&#1090;&#1072;&#1088;&#1099;&#1077; &#1074;&#1077;&#1088;&#1089;&#1080;&#1080;

---

### Post by jocko on 2009-09-26
> **ivanhoe75 said:**
> W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; [http://[COLOR=Red]http//[/COLOR]kubuntu.intrice.ru/ubun...ty/Release.gpg]("http://http//kubuntu.intrice.ru/ubuntu/dists/jaunty/Release.gpg")  &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; IP &#1072;&#1076;&#1088;&#1077;&#1089; &#1076;&#1083;&#1103; http
Have a look in your sources. It looks like you have a typo in the address to the repo.
It should be [http://kubuntu]("http://kubuntu.intrice.ru/ubuntu/dists/jaunty/Release.gpg")... not [http://[COLOR=Red]http//[/COLOR]]("http://%3Cfont%20color=%22Red%22%3Ehttp//%3C/font%3E")kubuntu...

---

### Post by ivanhoe75 on 2009-10-03
Bingo! it was such. I edited carefully but how such mistake crauled in?

---

