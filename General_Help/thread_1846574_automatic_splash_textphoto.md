---
title: "automatic splash text/photo"
date: 2011-09-19
forum: General Help
---

### Post by hyfanious on 2011-09-19
I wanna create an automatic splash text/photo appear once per hour and prefered to be in transparent style
How could I do this?

---

### Post by hakermania on 2011-09-19
Hey hyfanious, I don't think that there's a simple solution to this.

I would make a program in C++ that can do this (make a splash screen and then exit) and loop it inside a bash script.
A nice library for this is [http://doc.qt.nokia.com/4.7/qsplashscreen.html](http://doc.qt.nokia.com/4.7/qsplashscreen.html)

---

### Post by hyfanious on 2011-09-19
as I concerned Compiz has a fusion splash plugin, is that any way to manipulate it?

---

### Post by hyfanious on 2011-09-19
> **hakermania said:**
> Hey hyfanious, I don't think that there's a simple solution to this.

I would make a program in C++ that can do this (make a splash screen and then exit) and loop it inside a bash script.
A nice library for this is [http://doc.qt.nokia.com/4.7/qsplashscreen.html](http://doc.qt.nokia.com/4.7/qsplashscreen.html)

tnx for ur help
but
I have no experience in QT, is there any good, simple , fast way to learning essential steps for using it?

---

### Post by Bodsda on 2011-09-19
> **hyfanious said:**
> I wanna create an automatic splash text/photo appear once per hour and prefered to be in transparent style
How could I do this?

Screensaver on a 1hour idle time?

Bodsda

---

### Post by hyfanious on 2011-09-19
> **Bodsda said:**
> Screensaver on a 1hour idle time?

Bodsda

in fact I wanna it shows when I am actually in middle of my stuffs,
something likes a reminder
but tnx for ur help :)

---

### Post by hakermania on 2011-09-19
Hm, I just made an example code for you but as it seems it doesn't support transparent background even if the PNG I have selected is transparent:
[http://i.imgur.com/SLzJD.png](http://i.imgur.com/SLzJD.png)

The code is:
main.cpp
```

#include <QApplication>
#include <QPixmap>
#include <QSplashScreen>

int main(int argc, char *argv[])
{
    QApplication app(argc, argv);

    QSplashScreen *splash = new QSplashScreen;
    splash->setPixmap(QPixmap("/home/alex/Qt/splash/splash.png"));
    splash->show();
    sleep(2);

    return 0;
}

```splash.pro
```

QT       += core

QT       += gui

TARGET = splash
CONFIG   += console
CONFIG   -= app_bundle

TEMPLATE = app


SOURCES += main.cpp

```In the code provided, replace the image path with your own and the sleep() delay (in seconds) that matches your needs.
To compile you need the Qt Libraries. Once you have them cd in the directory with the code and do:
```

qmake splash.pro
qmake
make

```Hope this matches your needs.

Just to let you know that similar things can be done with the python-tk package using the python scripting language

EDIT: After the executable is made, you can loop it in a bash script like this:
```

#!/bin/bash
while true; do
   sleep 30m; #<- here set the delay you want between 2 splash screens
   /path/to/the/created/executable/from/the/above/code
done

```

---

### Post by Bodsda on 2011-09-19
> **hyfanious said:**
> in fact I wanna it shows when I am actually in middle of my stuffs,
something likes a reminder
but tnx for ur help :)

Ok, so have you got a way of launching, whatever it is you want to show, from the command line? If so, schedule it with a [cronjob]("https://help.ubuntu.com/community/CronHowto") 

Hope this helps,
Bodsda

---

### Post by hyfanious on 2011-09-19
> **hakermania said:**
> Hm, I just made an example code for you but as it seems it doesn't support transparent background even if the PNG I have selected is transparent:
[]("http://i.imgur.com/SLzJD.png")
Just to let you know that similar things can be done with the python-tk package using the python scripting language


tnx in advance,
I haven't QT library right now
I will get it in day after today

But as u mentioned not showing transparent items, is a bit big problem to me :(
I need something JUST like splash fusion of compiz only with a periodic feature

---

### Post by Bodsda on 2011-09-19
> **hyfanious said:**
> tnx in advance,
I haven't QT library right now
I will get it in day after today

But as u mentioned not showing transparent items, is a bit big problem to me :(
I need something JUST like splash fusion of compiz only with a periodic feature

Ok, heres a thought, set up the [splash plugin with your images. Then set up a keybinding to launch it.]("http://wiki.compiz.org/Plugins/Splash") Then use cron to schedule a simulated keypress of that binding. See [here]("http://ubuntuforums.org/showpost.php?p=4203181&postcount=21") for a possible way of doing that

Hope this helps,
Bodsda

---

### Post by hyfanious on 2011-09-19
> **Bodsda said:**
> Ok, so have you got a way of launching, whatever it is you want to show, from the command line? If so, schedule it with a [cronjob]("https://help.ubuntu.com/community/CronHowto") 

Hope this helps,
Bodsda

I did not follow you
but let me mentioned that I need something Just like splash fusion of compiz
it has two big feature
1.transparency support
2.let one to do his/her stuff while the picture is showing

I just need something that show me a transparent photo/text in a given time and doesn't disrupt my activities while it is showing

---

### Post by Bodsda on 2011-09-19
> **hyfanious said:**
> I did not follow you
but let me mentioned that I need something Just like splash fusion of compiz
it has two big feature
1.transparency support
2.let one to do his/her stuff while the picture is showing

I just need something that show me a transparent photo/text in a given time and doesn't disrupt my activities while it is showing

See my [latest post]("http://ubuntuforums.org/showpost.php?p=11265476&postcount=10")

Bodsda

---

### Post by haqking on 2011-09-19
Does not a sticky note application do it for you, i mean they can be made transparent and with an alarm function depending on the app.

There are a few, like timoby notes, pin em up, xpad etc....not sure if they all support alarms and transparency but i have used some before that do ?

or is this not what you mean ?

---

### Post by hyfanious on 2011-09-19
> **Bodsda said:**
> Ok, heres a thought, set up the [splash plugin with your images. Then set up a keybinding to launch it.]("http://wiki.compiz.org/Plugins/Splash") Then use cron to schedule a simulated keypress of that binding. See [here]("http://ubuntuforums.org/showpost.php?p=4203181&postcount=21") for a possible way of doing that

Hope this helps,
Bodsda

yup
it seems very fine to me
but the related page in ur link has "404 not found" error
can u guide me for ur method more precisely? :)

---

### Post by hyfanious on 2011-09-19
> **haqking said:**
> Does not a sticky note application do it for you, i mean they can be made transparent and with an alarm function depending on the app.

There are a few, like timoby notes, pin em up, xpad etc....not sure if they all support alarms and transparency but i have used some before that do ?

or is this not what you mean ?

something like that
but with TRANSPARENCY feauture and 
I wanna show a pic or text that fills about whole screen size :)

---

### Post by Bodsda on 2011-09-19
> **hyfanious said:**
> yup
it seems very fine to me
but the related page in ur link has "404 not found" error
can u guide me for ur method more precisely? :)

Really, they both work fine for me....
Which one gives the 404?

Bodsda

---

### Post by hyfanious on 2011-09-19
> **Bodsda said:**
> Really, they both work fine for me....
Which one gives the 404?

Bodsda

"following_ these _instructions" one
maybe u can help me by urself
in fact "super+x" is related to splash fusion,
how can I send a command that press virtually this combination, 
so I can use a loop script to run this command

---

### Post by Bodsda on 2011-09-19
> **hyfanious said:**
> "following_ these _instructions" one
maybe u can help me by urself
in fact "super+x" is related to splash fusion,
how can I send a command that press virtually this combination, 
so I can use a loop script to run this command

First ensure that the key combo actually works as expected

Install xmacro if you don't already have it.
Then run this command

```

xmacro > ~/compiz_splash_macro

```Then xmacro should ask for a key to use when you want to stop recording. Use whatever you like (apart from <super> and <x>)

Then press the key combination, follwed by your exit key.

Now, to test, open a terminal and run this
```

xmacro "$DISPLAY" < ~/compiz_splash_macro

```This should activate the splash screen. 

Hope this helps,
Bodsda

---

### Post by hyfanious on 2011-09-19
here is the solution
[HTML]http://ubuntuforums.org/showpost.php?p=9510883&postcount=26[/HTML]
tnx to all
especially to [Bodsda]("http://ubuntuforums.org/member.php?u=448461")
:)

---

### Post by hyfanious on 2011-09-19
Just for sake of others that may come across same problem
here is the code
(I use SUPER+X in compiz settings for spalsh fusion)

```

#!/bin/bash

var0=0
LIMIT=10

while [ "$var0" -lt "$LIMIT" ]
do
    var0=$(($var0+1))                 
    sleep 1800
    xdotool key Super+x
done       
exit 0

```

---

### Post by hakermania on 2011-09-19
Oh, I missed this post, I had 6 hours concurrent lessons but I am happy that a solution was finally found :D Nice!

---

