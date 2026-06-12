---
title: "how download,play games,watch movies in ubuntu?"
date: 2012-03-17
forum: General Help
---

### Post by infinity2012 on 2012-03-17
i just downloaded ubuntu and i donot know any thing in this version

can any body teach me how to enjoy it??

please i cannot play games ,download files,open EXE files or rar

---

### Post by goldshirt9 on 2012-03-17
what version are you using ??

Games are available from the Ubuntu software center 
[http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre](http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre)

7 Zip is also available from the Ubuntu software center for rar files.
In fact anything you need is almost available from the above center .

to play music and movies you must install  
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

most music players / movie players are available from the software center also.

to learn more visit sites like
unixmen / omgubuntu / web up8 / noobs on ubuntu .
I nearly forgot youtube is excellent for tutorials 
just google for them.

visit this site a lot.
enjoy

---

### Post by woxuxow on 2012-03-17
just explore this forum that is what you realy need it

---

### Post by infinity2012 on 2012-03-17
iam on version 11.10

i cannot open my games and any program with extension EXE

what should i do fast???

and thanks in advanced

---

### Post by Karlchen on 2012-03-17
Hello, infinity2012.
> **infinity2012 said:**
> iam on version 11.10 Fine. This is the current release version.

> i cannot open my games and any program with extension EXEUbuntu is a Linux edition based on Debian Linux, it is not MS Windows. Therefore MS Windows executable files do not mean anything to Ubuntu.

You may, however, go to the Ubuntu software centre, look for [**Wine**](http://www.winehq.org/) and install [**Wine**](http://www.winehq.org/). [**Wine**](http://www.winehq.org/) will allow you to install and run Windows programmes on Linux.
Beware:
Wine will not turn Linux into another MS Windows. You may wish to check on the [**Wine**](http://www.winehq.org/) site whether Wine really supports the games and programmes which you wish to use.

In case you have installed Ubuntu solely for the purpose of running Windows games, then you have definitely chosen the wrong operting system.  **[*Linux is NOT Windows*]("http://www.google.de/url?sa=t&rct=j&q=linux%20%20is%20not%20windows&source=web&cd=1&ved=0CDAQFjAA&url=http%3A%2F%2Flinux.oneandoneis2.org%2FLNW.htm&ei=81BkT628F4XZtAb2g53RBQ&usg=AFQjCNHu7sA8IamWTBmBNoiWZmvAihRwRg&cad=rja")**

Kind regards,
Karl

---

### Post by infinity2012 on 2012-03-17
i installed wine 

when i tried to open agame with this program .this message had appeared

> The file '/media/0E30BF8630BF7377/games/VC2/Vc2.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.


[IMG]http://oi43.tinypic.com/34h6g7r.jpg[/IMG]

can u tell me why??

---

### Post by chipbuster on 2012-03-17
EDIT: Already mentioned and already mentioned. I should really watch my posts when it's this late at night :< Thanks  Karlchen.

[This is an excellent read for anyone switching off of Windows to Linux]("http://linux.oneandoneis2.org/LNW.htm")

As for Wine, I'd suggest being careful with it, because it's not exactly magical fairy powder. Some programs work better than they would on Windows, some don't even install correctly.

---

### Post by Karlchen on 2012-03-17
> **chipbuster said:**
> [This is an excellent read for anyone switching off of Windows to Linux]("http://linux.oneandoneis2.org/LNW.htm") 2 posts above yours, someone had already linked to this article. :wink:

---

### Post by 3rdalbum on 2012-03-17
Wine is not flawless. You can only run maybe 20% of Windows programs in it. If you want to use Linux, then you must use Linux programs wherever possible. If you want to only use Windows programs, then you must use Windows.

Linux has an additional security feature called the "executable bit" or the "execute permission". You generally need to change the permissions of a program so it has execute permission, before you can run it. You obviously haven't done this for your Windows program.

There is a way of working without it for Windows programs. Go into the terminal (you can hit Control-Alt-T to open the terminal).

Type "wine " without the quotes, and make sure you've put a spacebar afterwards. Drag the .exe program into the terminal. Click on the terminal to bring it to the front again, and press Enter.

Good luck.

You need to use Linux programs for most things, don't forget. Wine is a last-resort.

As for videos, you should install the 'ubuntu-restricted-extras' package from Ubuntu Software Center. For DVDs, take a look at [www.medibuntu.org](www.medibuntu.org).

---

### Post by Karlchen on 2012-03-17
Hellom inifinity2012.
> **infinity2012 said:**
> i installed wine 
when i tried to open agame with this program .this message had appeared [... screenshot omitted ... ] can u tell me why??
Please, have a look at this recent thread: [**Allow executing file as program.......**]("http://ubuntuforums.org/showthread.php?t=1736080") It covers exactly this problem when running a Windows executable through Wine by double-clicking the filename in Nautilus:
You will have to right click the Windows programme file first and tick the option "Allow executing file as programme".
Having done so, double-clicking a Windows EXE file inside Nautilus should launch Wine and pass the the Windows EXE file to Wine for execution.

Kind regards,
Karl

---

