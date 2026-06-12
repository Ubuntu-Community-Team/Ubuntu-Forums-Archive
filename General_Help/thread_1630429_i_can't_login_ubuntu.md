---
title: "i can't login ubuntu"
date: 2010-11-25
forum: General Help
---

### Post by hani270 on 2010-11-25
hello !!

i have ubuntu 10.10

yesterday i am installed java jdk and net beans
at this morning i can't login ubuntu with my true username and password

it's big problem !!!
my php files in ubuntu desktop and i can't login it
and my works is stopped after this problem

sorry for bad english .. 

and i waiting your answar
best whashes :)

---

### Post by JustinR on 2010-11-25
> **hani270 said:**
> hello !!

i have ubuntu 10.10

yesterday i am installed java jdk and net beans
at this morning i can't login ubuntu with my true username and password

it's big problem !!!
my php files in ubuntu desktop and i can't login it
and my works is stopped after this problem

sorry for bad english .. 

and i waiting your answar
best whashes :)

What do you mean? Is your password not accepted?

---

### Post by Yougo on 2010-11-25
do you get to the login screen?

what happens when you fill in your username and password?
is the password not accepted, or does something else happen?

can you press CTRL+ALT+F1? you should go to a black screen with text. type your username and password there (no text appears when typing the password, this is normal. just type and press enter). what does it say next?

---

### Post by lmarmisa on 2010-11-25
Start you computer from an Ubuntu Live CD (or pendrive). Then mount your Ubuntu partition and you will have access to your php files. 

Try to copy your files to a USB hard drive or pendrive or transfer them to other computer using Samba.

I think that your login problem is not related to the download of Java packages.

---

### Post by hani270 on 2010-11-25
> What do you mean? Is your password not accepted?

my password is "123"

when i write my user and pass
i see black screen in 1 or 2 seconds then i see login screen

i cant read the words in black screen but i read one word

its "**battery**"

sorry for bad english :) :)

---

### Post by JustinR on 2010-11-25
> **hani270 said:**
> my password is "123"

when i write my user and pass
i see black screen in 1 or 2 seconds then i see login screen

i cant read the words in black screen but i read one word

its "**battery**"

sorry for bad english :) :)

If I'm not mistaking, I don't think you can have a 3 character password, I believe it's at least 5-8 characters.

Are you sure your password wasn't longer?

---

### Post by hani270 on 2010-11-25
i cant understand english :(

---

### Post by Yougo on 2010-11-25
a password can be shorter, you just get a warning during installation, which you can click away and us ethe short one anyway.
the fact that he sees a black screen means the password is accepted, but the session is somehow rejected, pushing him back to the login sreen

@hani270,
when in login screen, press CTRL+ALT+F1 and log in there. what does it say next?

what is your language? if it is Dutch or German, i may help you (a bit) better

---

### Post by hani270 on 2010-11-25
> are you sure your password wasn't longer?

yes ,, i am sure

my password is
" **123 **"

---

### Post by lmarmisa on 2010-11-25
> **hani270 said:**
> my password is "123"

when i write my user and pass
i see black screen in 1 or 2 seconds then i see login screen

i cant read the words in black screen but i read one word

its "**battery**"

sorry for bad english :) :)

Open a text terminal typing Alt + Ctrl + F1 (press the 3 keys at the same time) and check if you can access to your account.

---

### Post by JustinR on 2010-11-25
> **hani270 said:**
> i cant understand english :(

[http://translate.google.com/#](http://translate.google.com/#)
:)

If your sure of it, you can reboot your computer, go into the GRUB Boot Menu (you might have to hold SHIFT during your computer startup to see it), and select 'Recovery Mode'. When a gray dialoge box comes up, select 'Root' with your keyboard arrow keys. Then type in:
```

passwd USERNAME

```
Then type in a new password. Restart your computer ('shutdown -r now') and you should be able to log in with your new password.

---

### Post by hani270 on 2010-11-25
> when in login screen, press CTRL+ALT+F1 and log in there. what does it say next?

i am at windows

i well go to ubuntu and then i well to back here

10 menits please :)

---

### Post by hani270 on 2010-11-25
i pressed cntrl+alt+f1

and write my login data

and this is picture from my mobile (nokia 6300 :))

the picture see "the problem from java"

:)

---

### Post by hani270 on 2010-11-25
> what is your language? if it is Dutch or German, i may help you (a bit) better

i am arabic
but i love germany and bayern munich is my favorite team
and i have some words from german langues (****,dunn,klien,madchen :))
but my english is best than my german

i am arabic

i wish u to see the attashed picture

---

### Post by hani270 on 2010-11-25
where are you ?

---

### Post by s.shawky on 2010-11-25
may be a friend or a brother has change your password as a joke or you have changed it wrongly or forget it and i think you can't make it 123 as it will say your password is very simple (&#1605;&#1605;&#1603;&#1606; &#1610;&#1603;&#1608;&#1606; &#1575;&#1606;&#1578; &#1594;&#1610;&#1585;&#1578;&#1577; &#1594;&#1604;&#1591;&#1577; &#1575;&#1608; &#1581;&#1583; &#1594;&#1585;&#1607; &#1605;&#1606; &#1594;&#1610;&#1585; &#1605;&#1575; &#1610;&#1602;&#1608;&#1604;&#1603; &#1608; &#1576;&#1585;&#1590;&#1607; &#1604;&#1608; &#1580;&#1610;&#1578; &#1578;&#1593;&#1605;&#1604;&#1607; 123 &#1607;&#1610;&#1602;&#1608;&#1604;&#1603; &#1575;&#1604;&#1576;&#1575;&#1587;&#1608;&#1585;&#1583; &#1576;&#1587;&#1610;&#1591; &#1608; &#1605;&#1588; &#1607;&#1610;&#1585;&#1590;&#1577; &#1576;&#1610;&#1607; &#1575;&#1604;&#1581;&#1603;&#1575;&#1610;&#1577; &#1583;&#1610; &#1581;&#1589;&#1604;&#1578; &#1605;&#1593;&#1575;&#1610;&#1575; &#1602;&#1576;&#1604; &#1603;&#1583;&#1577; &#1576;&#1587; &#1604;&#1602;&#1610;&#1578; &#1606;&#1601;&#1587; &#1575;&#1606;&#1575; &#1575;&#1604;&#1604;&#1610; &#1594;&#1604;&#1591;&#1575;&#1606; &#1601; &#1575;&#1604;&#1575;&#1582;&#1585;)

---

### Post by hani270 on 2010-11-25
no no

i am sure
my password is "123" and noboddy changed it

the error in java files
see the picture please

---

### Post by Yougo on 2010-11-25
Salem aleikum, i was out for lunch :-)

i can see your password is accepted, and it seems the java broke something

you could try removing Java JDK by typing
```
sudo apt-get remove sun-java6-jdk 
```
and press enter
it will ask for your password again

you can try to get Java back later, first get ubuntu working again :)

when it is removed, restart the computer by typing
```
sudo reboot
```
and press enter

in the mean time, if you really need your files first, you could put in the installation cd, and choose Try Ubuntu. 
from there you can acces your harddisk and copy your files to a usb stick.

---

### Post by lmarmisa on 2010-11-25
Your user and password are correct.

I can see two errors in the file /etc/profile.d/java.sh in lines 2 and 4.

There is also a warning but I am not able to read the complete text ("Your CPU appears to be lacking..."). Could you repeat the photo capturing the full screen?.

Take a second snapshot showing the contents of file /etc/profile.d/java.sh. Type this command:

```

head /etc/profile.d/java.sh

```

---

### Post by hani270 on 2010-11-25
when i try to remove java-jdk

he told me :
[ E : Unable to locte package sun-java-jdk ]

---

### Post by hani270 on 2010-11-25
in first photo the all text from the error
,,,,
in secon photo the content of /etc/profile.d ....... (the file)

---

### Post by kanishkdudeja on 2010-11-25
the package is sun-java6-jdk not sun-java-jdk

---

### Post by hani270 on 2010-11-25
the all of error in this pic

---

### Post by kanishkdudeja on 2010-11-25
when you try to remove java..

mayb u hav got the spelling wrong..

it is not sun-java-jdk

it is sun-java6-jdk

---

### Post by Yougo on 2010-11-25
try removing Java JDK by typing
```
sudo apt-get remove sun-java6-jdk 
```
and press enter
it will ask for your password

when it is removed, restart the computer by typing
```
sudo reboot
```
and press enter.

---

### Post by lmarmisa on 2010-11-25
I suppose you did not install Java from the Ubuntu repositories. This can be the origin of your problems.

Are you using overclocking in your computer?. This could explain the first warning.

Try to edit the file /etc/profile.d/java.sh

```

sudo nano /etc/profile.d/java.sh

```

and insert this line on the top of file (line #1):

```

#!/bin/bash

```

Save and exit.

Reboot and check if the problem is solved.

---

### Post by hani270 on 2010-11-25
ok :)

i am from ubuntu now

thanks for **ALL**;

---

### Post by kanishkdudeja on 2010-11-25
is it solved?

---

### Post by lmarmisa on 2010-11-25
> **hani270 said:**
> ok :)

i am from ubuntu now

thanks for **ALL**;

Great!!!. :D

Please, mark the thread as SOLVED.

---

