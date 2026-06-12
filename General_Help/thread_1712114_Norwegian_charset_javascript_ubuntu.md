---
title: "Norwegian charset javascript ubuntu"
date: 2011-03-22
forum: General Help
---

### Post by pandahbear on 2011-03-22
Hi, im an average Linuxuser, and I need some help! 

Basicly, to make a long story short, I've been chatting alittle with a friend of mine trough a javabased chat, but I cant get my local charset to work (Norwegian), hence I can't use the letters "Æ Ø Å".

Anyone have any hints and tips to make this work? 
I've installed the Norwegian languagepack for my Ubuntu, and seached my *** off on google. :p
Also, i've tried both sun java, and icetea

---

### Post by deathadder on 2011-03-22
It's not really something the OS can deal with, it sounds like the person who wrote the chat client didn't set the charset to UTF-8.

---

### Post by pandahbear on 2011-03-22
But this would be an issue that would only relate to ubuntu? 
Since my mate is on a windows (shrugg) computer, and his Norwegian letters works just fine.

---

### Post by deathadder on 2011-03-22
Ah, turns out you do learn something new each day. I had a look through the java.lang package and found that the locale of the OS and the character encoding used provide the default for the JRE. I was almost certain it was determine another way. You can have a look at the [locale conf for Ubuntu]("https://help.ubuntu.com/community/LocaleConf") to see if that helps.

---

### Post by pandahbear on 2011-03-22
running the command locale prints : 
LANG=nb_NO.utf8
LANGUAGE=nb_NO:nb:no_NO:no:nn_NO:nn:en_GB:en
LC_CTYPE="nb_NO.utf8"
LC_NUMERIC="nb_NO.utf8"
LC_TIME="nb_NO.utf8"
LC_COLLATE="nb_NO.utf8"
LC_MONETARY="nb_NO.utf8"
LC_MESSAGES="nb_NO.utf8"
LC_PAPER="nb_NO.utf8"
LC_NAME="nb_NO.utf8"
LC_ADDRESS="nb_NO.utf8"
LC_TELEPHONE="nb_NO.utf8"
LC_MEASUREMENT="nb_NO.utf8"
LC_IDENTIFICATION="nb_NO.utf8"
LC_ALL=

wich should be my prefferd Norwegian (bokmål).

---

### Post by deathadder on 2011-03-22
According to [Orcale]("http://www.oracle.com/technetwork/java/javase/locales-137662.html"), the Norwegian (Bokmål) locale is no_NO. Since at the moment you've got LANGUAGE set to include no_NO can you update the LANG variable to include it also?
```
$ export $LANG=$LANG:no_NO
```
Beyond that I'm not too sure to be honest. You can try setting parameters to the applet but I'm not sure how to do that...

---

