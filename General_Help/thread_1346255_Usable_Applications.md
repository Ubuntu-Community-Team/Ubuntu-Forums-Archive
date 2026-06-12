---
title: "Usable Applications"
date: 2009-12-04
forum: General Help
---

### Post by scuba117 on 2009-12-04
linux cannot run windows programs, correct? and it can also not run .exe's? is there any way for me to run any windows programs or files in ubuntu? ty

---

### Post by Frogging101 on 2009-12-04
There is a compatibility layer called Wine. Install by using this command:

```
sudo apt-get install wine
```

To see what programs are compatible, go to [http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by s3MA00RRNY on 2009-12-04
Use Wine. Install it through Ubuntu Software Center or through the terminal:

$ sudo apt-get install wine

You may also want to get winetricks, which assists with installing things in Wine.

Wine stands for Wine Is Not an Emulator!

EDIT: I'm too slow.

---

### Post by sisco311 on 2009-12-04
sorry

---

### Post by madverb on 2009-12-04
winehq.org

---

### Post by Frogging101 on 2009-12-04
> **sisco311 said:**
> why do you want to run Windows applications in Ubuntu?

I can tell you that people don't appreciate those kind of answers.

---

### Post by sisco311 on 2009-12-04
> **Frogging101 said:**
> I can tell you that people don't appreciate those kind of answers.

Well, it was a question, but I see your point. 

The OP's question is vague too.


@OP

Please try to elaborate your question. Thanks.

---

### Post by scuba117 on 2009-12-04
i have ubuntu version 9.10

i know i was a bit vague, im just trying to see if i can run, for example, world of warcraft or left4dead pc on linux

---

### Post by zaphod777 on 2009-12-04
Guys, guys .... no need to get out of hand it is a perfectly reasonable question for a new linux user. 

In regards to the original posters question wine is an application to allow you to run Windows software on Linux. 

However you can check in the wine website to see which apps are most compatible. However most of the time they just dont work or have frequesnt crashes certain features don't work etc.

there is a commercial version of wine available called crossover office which is a bit better.

I have run MS Office 2003 and 2007 using it.

With that said it is always better to run native Linux software if you let us know what you want to run our what your goals are we can point you in the right direction for a native alternative.

---

### Post by zaphod777 on 2009-12-04
> **scuba117 said:**
> i have ubuntu version 9.10

i know i was a bit vague, im just trying to see if i can run, for example, world of warcraft or left4dead pc on linux

here is a link for getting World of Warcraft working

[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

left for dead info 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592)

[http://ubuntuforums.org/showthread.php?t=991003](http://ubuntuforums.org/showthread.php?t=991003)

[http://www.codeweavers.com/compatibility/browse/group/?app_parent=4100](http://www.codeweavers.com/compatibility/browse/group/?app_parent=4100)

---

### Post by ed-koala on 2009-12-04
World of Warcraft runs fine under Wine, I use it myself.  In fact some folks say it runs FASTER than Windows.  Read up on installing it though, there are a few things to know first.  Including a rather ugly but fixable problem introduced with Wow's last patch to their launcher that makes the file permissions change.

---

### Post by sisco311 on 2009-12-04
> **scuba117 said:**
> i have ubuntu version 9.10

i know i was a bit vague, im just trying to see if i can run, for example, world of warcraft or left4dead pc on linux

I'm not a gamer, but wow works under wine, here is the community documentation: [uhelp]community/WorldofWarcraft[/uhelp]


Also check the [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93") sub-forum.


EDIT: I'm slow... :)

---

### Post by scuba117 on 2009-12-04
thank you very much zaphod, you pretty much nailed my question :)

so does wine basically allow the execution of .exe's? and relevant windows file types

---

### Post by ed-koala on 2009-12-04
Yes, that's what it's supposed to do, but some things work fine, some work so so, some don't work at all.

---

### Post by scuba117 on 2009-12-04
awesome! thank you guys so much! :D

if you feel like helping with my only other issue, id rly appriciate it too :)
[http://ubuntuforums.org/showthread.php?p=8442330#post8442330](http://ubuntuforums.org/showthread.php?p=8442330#post8442330)

---

