---
title: "QT4 and Ubuntu??"
date: 2010-12-13
forum: General Help
---

### Post by sirkeith on 2010-12-13
Not sure how to title this. It seems that any program on my system {10.10 Maverick} that is designed in QT4 including packages like QT4 Settings do not show text in Tooltips. I first noticed the problem in Scribus 1.3.8. I have tried Scribus 1.3.9 and Scribus 1.5.0 with the same problem.

Scribus people say it is not there problem and I agree, I thought maybe a QT4 thing, but getting help in that neighborhood is beyond me. I m not a programmer.

Any thoughts??

thanks, keith

---

### Post by sirkeith on 2010-12-13
or even suggestion where to post this??

thanks

---

### Post by Vaphell on 2010-12-13
do you have some particular qt4 theme set in qt4 settings?
on my 10.04 box system theme (default) shows white-text-on-black-background tooltips, but when i switch qt4 to cleanlooks, tooltips get a yellow background and i barely notice that there is a actually a white text there. Yes, i agree - that's an annoying oversight.

[http://ubuntuforums.org/showthread.php?t=1580266](http://ubuntuforums.org/showthread.php?t=1580266)

---

### Post by sirkeith on 2010-12-14
Hi Vaphell, I installed the QT4 program in the hope that the problem was fixable by using it. I got some awfully gross interfaces using it but never managed to affect any change to the tooltips. ;) I am stoicly resisting the pull of kword.

---

### Post by Vaphell on 2010-12-14
So you say that none of these themes gets the tooltips right? do you use KDE or gnome?

---

### Post by sirkeith on 2010-12-14
Vaphell, there was no help from theme changes. According to something I found on a QT site, the text in the tooltips is drawn from the inactive palette in the QT4 configure program. So I tried using it.

I have uninstalled all QT4 related software I could find on my machine, I have downloaded source for Scribus 1.3.9, latest "stable" build and have compiled and installed it. 

I installed an older version of Scribus that was built with QT3 and tooltips work in that build. Thanks for your help, it is much appreciated.

---

### Post by sirkeith on 2010-12-15
I have managed to fix this problem. Thewre is a correlation to the tooltips in the panel on the desktop. 

thanks

---

