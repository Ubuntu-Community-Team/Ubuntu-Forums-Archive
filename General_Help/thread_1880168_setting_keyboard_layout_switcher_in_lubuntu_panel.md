---
title: "setting keyboard layout switcher in lubuntu panel"
date: 2011-11-13
forum: General Help
---

### Post by techvish81 on 2011-11-13
hello everyone, my question is to amjawad,
i tried lubuntu, xubuntu,ubuntu everything in my netbook, the most snappier i found was lubuntu, my main pc (desktop) is quite stable with ubuntu and i have no plans to change anything in it,it is my work computer and i cant experience anything, so i use my netbook to experience various distros, lubuntu is by far the best i would suggest to anybody but there is only one problem for which ,still i have not found any solution, i want to use libreoffice and chromium and nothing else in it, my problem is that even if i put a keyboard layout switcher in the panel i was unable to install more languages, i installed ibus tried everything in the threads but nothing happens, the option in the input method menu remains greyed and it doesnt allow me to add more languages to my system language which is english (us).

in xubuntu, just a plugin install can do it, in ubuntu it works out of the box. 

any straight forward way would be highly appreciated, 


cheers!!
____

---

### Post by Rodney9 on 2011-11-13
LXKeymap is an application that allows you to easily switch between keyboard layouts.
It contains an easy mode showing the keyboard layouts and an expert mode to switch to more complex layouts, it is under preferences on the menu.

You can add it to the panel also, though I don't know if you can use keyboard shortcuts with it.

Rodney

---

### Post by amjjawad on 2011-11-14
> **techvish81 said:**
> hello everyone, my question is to amjawad,
i tried lubuntu, xubuntu,ubuntu everything in my netbook, the most snappier i found was lubuntu, my main pc (desktop) is quite stable with ubuntu and i have no plans to change anything in it,it is my work computer and i cant experience anything, so i use my netbook to experience various distros, lubuntu is by far the best i would suggest to anybody but there is only one problem for which ,still i have not found any solution, i want to use libreoffice and chromium and nothing else in it, my problem is that even if i put a keyboard layout switcher in the panel i was unable to install more languages, i installed ibus tried everything in the threads but nothing happens, the option in the input method menu remains greyed and it doesnt allow me to add more languages to my system language which is english (us).

in xubuntu, just a plugin install can do it, in ubuntu it works out of the box. 

any straight forward way would be highly appreciated, 


cheers!!
____

Hi,

I do remember this question and I'm sure I have replied it but can't remember where and when? Perhaps LXDE Forum? please remind me. Thanks!

---

### Post by hederzsolti on 2011-11-17
Hey guys,

I've got the same problem so I've been looking for some solution on the web. I found this video, was really excited, tried it, but unfortunately it doesn't work for me (Lubuntu 11.10, Vostro 1015)... Donno why. Give it a try, maybe it will work for some of you. Or just set you on the right path to find the solution.
[http://www.youtube.com/watch?v=gzYqREENVVY](http://www.youtube.com/watch?v=gzYqREENVVY)
Let know if you find out something. I love Lubuntu, but I really miss this feature.

Zsolti

---

### Post by RabbitWho on 2011-11-27
Hi! I have the very same problem, I've gotten to the point where my computer won't work well on regular gnome anymore so I'd be so so happy and so will my poor slow computer if someone could answer this as I have to plough ahead with gnome in the meantime. hee hee

 I'm using lucid, there's a default keyboard switcher which you can add to the panel but I can't seem to add any other languages to it. 
[CENTER][COLOR=#000000]
Okay I've used this code: [/COLOR]>  echo '@setxkbmap -option grp:alt_shift_toggle "uk,es,ru"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart and so far it's working okay, i don't know what letters are for the Irish keyboard layout so I had to go with the UK ones. My ancestors are spinning in their graves I'm sure heh

[COLOR=#000000] Btw for some reason every time i post here it posts a list of languages and I don't know why, sorry if it shows up. [/COLOR][/CENTER]
[LEFT][COLOR=#FFFFFF][FONT=Trebuchet MS][/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[LEFT]Detectar idioma » English[/LEFT]


[/COLOR][/CENTER]

---

### Post by techvish81 on 2011-11-29
great list!!!:lolflag:

---

