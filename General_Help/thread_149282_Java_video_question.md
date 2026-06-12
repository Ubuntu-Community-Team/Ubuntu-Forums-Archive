---
title: "Java video question"
date: 2006-03-23
forum: General Help
---

### Post by cab1024 on 2006-03-23
Can anyone see this webcam with Firefox on Ubuntu?
[http://www.mavsurfer.com/main_page/](http://www.mavsurfer.com/main_page/)

I've tried installing the Java 1.5 / 5.0 Update 6. It appears to be installed since if I try to install it again it says it is the latest version. I also did the wiki's instructions for upgrading Firefox to 1.5.0.1, which I believe is the only Firefox on my system. I removed 1.0.7.

Is there something I have to do additionally to get Firefox to see the Java update?

Or is this webcam just too advanced for Linux?

(BTW, don't get too excited. The waves are nonexistent today.)

---

### Post by arnieboy on 2006-03-23
I can see the live streaming webcam.
use automatix on a  fresh install of breezy to install java and other useful stuff.

---

### Post by cab1024 on 2006-03-23
[QUOTE=arnieboy]I can see the live streaming webcam.
use automatix on a  fresh install of breezy to install java and other useful stuff.[/QUOTE]
I just did a fresh install of Breezy and used EasyBreezy instead of Automatix. I've also installed quite a bit of other stuff in the last couple of days. I'd rather not have to reinstall everything every time I want to install one thing. 

And that install followed another fresh install where Easy Ubuntu would not work.

So for the most recent install. I did this:
1- Install Breezy
2- Run Easy Ubuntu. It failed.
3- Install Breezy updates.
4- Try Easy Ubuntu again. It failed
5- Run EasyBreezy. Got some NULL errors but things seemed like they installed.
6- Upgrade Firefox to 1.5 then 1.5.0.1. Remove 1.0.7.
7- Install Java according to How-to or wiki, not sure. Did it a couple of times until it said everything was current.

On the fresh install before that I reversed the order of Easy Ubuntu and the Ubuntu updates, but EasyUbuntu failed then too.

Is there a way to know whether Firefox knows about the Java update? Is it using an older Java? Is there anything I can do without reinstalling everything again?

---

### Post by arnieboy on 2006-03-23
--

---

### Post by arnieboy on 2006-03-23
since Easy Ubuntu broke your system, you should post this in the Easy ubuntu forum and see if they can help you:
[http://ubuntuforums.org/forumdisplay.php?f=86](http://ubuntuforums.org/forumdisplay.php?f=86)

---

### Post by cab1024 on 2006-03-23
[QUOTE=arnieboy]since Easy Ubuntu broke your system, you should post this in the Easy ubuntu forum and see if they can help you:
[http://ubuntuforums.org/forumdisplay.php?f=86](http://ubuntuforums.org/forumdisplay.php?f=86)[/QUOTE]
OK. I did. But there doesn't look like much activity over there.

In your opinion, what would likely happen if I used Automatix now without reinstalling? I wouldn't say my system is broke. It seems like the only thing that doesn't work is Firefox together with Java

But more importantly, when do I make the upgrade to Firefox 1.5? After running Automatix? Will the new Firefox have all of the plug-ins the old one did?

Thanks for the help.

---

### Post by arnieboy on 2006-03-23
[QUOTE=cab1024]OK. I did. But there doesn't look like much activity over there.

In your opinion, what would likely happen if I used Automatix now without reinstalling? I wouldn't say my system is broke. It seems like the only thing that doesn't work is Firefox together with Java

But more importantly, when do I make the upgrade to Firefox 1.5? After running Automatix? Will the new Firefox have all of the plug-ins the old one did?

Thanks for the help.[/QUOTE]
try running the latest version of automatix now and just choose the "firefox 1.5" option. that will install firefox 1.5 and all the major plugins including java. It should overwrite all the mistakes that Easy Ubuntu did.

---

### Post by cab1024 on 2006-03-23
Thanks, arnieboy.

Having just read quite a bit of Automatix/Easy Ubuntu backstory in the Community forum, I now understand your shortness with dealing with anything Easy Ubuntu related.

If it doesn't fix it, I'll reinstall a fresh Breezy and start with Automatix. Last question, should I do the Automatix or the Breezy updates first?

And again, thanks for your hard work on this project.

---

### Post by robotgeek on 2006-03-23
What did you try to install using EasyUbuntu (which version?). What platform are you on? (x86/powerpc/amd64)

---

### Post by cab1024 on 2006-03-23
[QUOTE=robotgeek]What did you try to install using EasyUbuntu (which version?). What platform are you on? (x86/powerpc/amd64)[/QUOTE]
I tried to install everything that looked useful in the web and sound & video categories. I'd like my internet experience to be transparent compared to Mac or a PC.

I've got a PIII/667MHz. I followed the instructions [here]("http://easyubuntu.freecontrib.org/get.html") with a nightly build from a couple of days ago.

Downloaded the build and did this
```
cd; mkdir easyubuntu; cd easyubuntu
wget http://easyubuntu.freecontrib.org/EasyUbuntu-latest.tar.bz2
tar -jxvf EasyUbuntu-latest.tar.bz2
gksudo ./easyubuntu.py
```
But like I said, it never worked, so what IS installed came from EasyBreezy. Unless EasyUbuntu did screw something up while not installing anything when I ran it as the 2nd step of my installation.

---

### Post by robotgeek on 2006-03-23
I think there is a issue with the nightly image not being updated, can you get it from svn while we try to fix the issue?

---

### Post by cab1024 on 2006-03-23
[QUOTE=robotgeek]I think there is a issue with the nightly image not being updated, can you get it from svn while we try to fix the issue?[/QUOTE]
That would explain why it didn't look like the new version.

I also tried the "Bleeding Edge" method at some point that night, which *did* produce the new look, but still no luck with anything getting installed.

What is svn?

---

### Post by robotgeek on 2006-03-23
[QUOTE=cab1024]That would explain why it didn't look like the new version.

I also tried the "Bleeding Edge" method at some point that night, which *did* produce the new look, but still no luck with anything getting installed.

What is svn?[/QUOTE]
svn stands for subversion. You already have it installed if you followed the  "bleeding edge" directions.

---

### Post by cab1024 on 2006-03-24
It's been said before, and it'll be said again. Arnieboy, you are the man.

Automatix reinstalled Firefox 1.5 with a functioning java so that my internet/linux experience is complete -- without reinstalling a fresh Breezy. But next time I DO install a fresh OS, it will be followd by an Automatix installation.

Thank you!

---

### Post by tOpEzz on 2006-03-28
normally i refer from [http://easylinux.info](http://easylinux.info) for update by Breezy, it's working.. all it sudo apt-get, hehehehhe... sometime it's look hard.. ahaks, good luck cab1024.

---

### Post by cab1024 on 2006-03-30
[QUOTE=tOpEzz]normally i refer from [http://easylinux.info](http://easylinux.info) for update by Breezy, it's working.. all it sudo apt-get, hehehehhe... sometime it's look hard.. ahaks, good luck cab1024.[/QUOTE]
I'm no quite sure what you mean.

---

