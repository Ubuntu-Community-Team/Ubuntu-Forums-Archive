---
title: "Question about usability"
date: 2010-08-03
forum: General Help
---

### Post by davisty on 2010-08-03
Folks, I must admit Im getting extremely frustrated with Ubuntu. Im not a Ubuntu expert. Dont want to be, but:

1. The programs lock up frequently, and consistently. These applications include Firefox (the big one), openoffice, and movie player. They are barely usable. And Ubuntu and Firefox developers are simply unwilling to address these issues.

2. How the heck can I install applications without a PHD from MIT. Im not sure what's harder, running Firefox or installing applications. God help me if I have to download open source applications that are not in your repository. And  java, try to install/update that.:p

People who are TRYING to switch over from Windows just dont stand a chance. How the heck is someone supposed to be able to 
apt-get install sun-java6-jdk sun-java6-jre 

One the command doesnt work. It's asking if we're "root". or 
sudo gedit /etc/environment. WTF?

Somebody just shoot me.

---

### Post by Smart Viking on 2010-08-03
If you are having troubles with the stock programs, you could always install others, you could use chromium instead of firefox, and VLC instead of movie player, both those programs are better in my opinion. :)  (i am also having hard times with firefox, i think it's time for ubuntu to replace it)

:)

---

### Post by cj.surrusco on 2010-08-03
> **davisty said:**
> Folks, I must admit Im getting extremely frustrated with Ubuntu. Im not a Ubuntu expert. Dont want to be, but:

1. The programs lock up frequently, and consistently. These applications include Firefox (the big one), openoffice, and movie player. They are barely usable. And Ubuntu and Firefox developers are simply unwilling to address these issues.

First of all, not many people are having the same problems that you have as far as crashing programs. That means that you must try to fix it yourself. You can't expect the developers to foresee every bug that they might have. You have to file a bug report if you cannot find others that have the same problem.
> **davisty said:**
> 
2. How the heck can I install applications without a PHD from MIT. Im not sure what's harder, running Firefox or installing applications. God help me if I have to download open source applications that are not in your repository. And  java, try to install/update that.:p

People who are TRYING to switch over from Windows just dont stand a chance. How the heck is someone supposed to be able to 
apt-get install sun-java6-jdk sun-java6-jre 

One the command doesnt work. It's asking if we're "root". or 
sudo gedit /etc/environment. WTF?

It's not terribly difficult stuff you are talking about. Entering a command is something that you just have to learn to do. It's not necessarily harder than Windows, just different. You have to ***learn*** an new OS, just as you learned Windows. You have to have a desire to work on your OS. If you aren't comfortable doing this, then maybe it's best if you stick with Windows. 
> **davisty said:**
> 
Somebody just shoot me.

That problem isn't for the Ubuntu Forums.

---

### Post by snowpine on 2010-08-03
Hi Davisty!

> **davisty said:**
> 1. The programs lock up frequently, and consistently. These applications include Firefox (the big one), openoffice, and movie player. They are barely usable. 

Not normal. Not normal at all. A well-configured Linux system is incredibly stable; Linux is widely used in corporate situations where an hour of downtime costs millions. I recommend starting a new thread for each of your problems and patiently working through the solutions; it can be a little frustrating but is worth it!

Not that two wrongs make a right :) but if you think applications never crash in Windows, well then...

> **davisty said:**
> 2. How the heck can I install applications without a PHD from MIT. Im not sure what's harder, running Firefox or installing applications. 

Thousands of stable, tested, and trusted applications can be easily installed by double-clicking on them in the Ubuntu Software Center; not sure it could be any simpler. Certainly better than the "Windows way" of downloading stuff and hoping it works. :)

---

### Post by Mi11z on 2010-08-03
> **Smart Viking said:**
> If you are having troubles with the stock programs, you could always install others, you could use chromium instead of firefox, and VLC instead of movie player, both those programs are better in my opinion. :)  (i am also having hard times with firefox, i think it's time for ubuntu to replace it)

:)

I'm with this guy, and don't worry the thing with linux is you have to try man, then you get to a certain point and most things seem easy and after that you will find it A LOT more enjoyable than Windows or OSX trust, possibilities are endless with linux and there definitely not with mac "Damn you steve jobs"  , anyway yeah you'll get there in the end and of course theres tons of alternatives to the stock apps. :):popcorn:

---

### Post by Zorgoth on 2010-08-03
It is extremely easy to install applications in Ubuntu, and you never have to worry about updating them.  Just go to the Applications menu and open the Ubuntu software Center, and search for whatever kind of program you want.  Searching around on the internet is *NOT* the way to do it, like in Windows.  

In the quite rare event that you cannot find what you need through the Software Center, look for a file with the extension ".deb" on the internet; those are packages, comparable to '.msi's or 'setup.exe's on Windows (and are much smarter about making sure your computer has all the dependencies of the program in question).

As for Firefox, etc., crashing, that is not normal.  My Ubuntu is far more stable than my Windows ever has been.  

If all your programs are crashing, it isn't a problem with the applications themselves; something wrong with your system.  My bet is that it is a graphics card issue, because that is the most common problem in Linux.  Either that, or something in your computer is just not working, or you did something very wrong when installing your OS.  Please make a separate post regarding whatever problems you are having and link to it.

To check if it is a graphics card issue, you could:

a) run the command "metacity --replace" (type Alt-F2 to get a run dialog)
- this will give you a default window manager with no effects that doesn't use the graphics card (but is pretty ugly imo, even for a light system).  See if that makes a difference.  If it does, then it is probably a graphics issue.

If it is a graphics issue, the easiest thing to do would be this:

b) Go to "System > Administration > Hardware Drivers" and see if there are any proprietary drivers you could install for your graphics card. 

You will have open source drivers already on your system by default, but they may not work as well.

And "root" is the name of the administrator or "superuser."  To execute a command as root, precede it with "sudo."  "apt-get install" must always be executed as root, as you wouldn't want just anyone to install software on your computer.  You will then be prompted for your password and the command will run.

So to run your command:

sudo apt-get install sun-java6-jdk sun-java6-jre 

Whoever told you to run that command forgot to put in the "sudo" because after using Ubuntu for a bit anyone knows that apt-get install is preceded by sudo.

---

### Post by David Andersson on 2010-08-03
What you experience is not normal. It is hard to know what is wrong, even to know if it is hardware or software. Here is a bunch of random questions in a feeble attempt to pinpoint the problem.

There is (or was) an issue with firefox that under certain conditions it would regularly hang (sync) the system, but only for a fraction of a second, with your specs.

Do you have these hangs even when firefox is not running?

Does the system monitor report the amount of memory that your computer is supposed to have? Is the harddisk nearly full?

I know that a faulty harddisk can cause a system to occasionally freeze for about 10-30 seconds at a time. Ubuntu 10.04 should detect that and warn about it. Otherwise, the harddisk monitor should be able to show you health-monitoring (SMART-data) from the harddisk.

Have you installed things from other sources than the repositories? Have you made manual changes in /etc?

Have you checked the logs? Do you have sudden crashes? Have you run memtest86 from the boot menu?

If you add another user and login as that user, does he experience the same problem?

---

### Post by lovinglinux on 2010-08-04
> **Smart Viking said:**
> (i am also having hard times with firefox, i think it's time for ubuntu to replace it)

I guess all Chrome users think that, the rest of the world don't. I don't have any problems with Firefox. It works great, is a much better browser and Firefox 4 will be even better. Anyway, we should not start a browser war here. If you want to reply to my post, go to [http://ubuntuforums.org/showthread.php?p=9654833](http://ubuntuforums.org/showthread.php?p=9654833)

---

