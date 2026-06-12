---
title: "Android ADB-Fastboot on 10.04"
date: 2011-05-30
forum: General Help
---

### Post by LanternsLight456 on 2011-05-30
Hello, I searched the forum for an answer and I've looked on XDA-Developers as well, along with googling the question and can't find anything that's worked for me.

What I'm wanting to do is set up ADB/Fastboot on my Ubuntu 10.04 computer. I JUST installed Ubuntu, and it's my first real go round with Linux (I briefly attempted Kubuntu, but KDE gave my old computer fits)

I'm on Ubuntu 10.04 downloaded from the Ubuntu site.

PLEASE keep in mind to be really clear, because I'm so new to Linux.

What I want to be able to do is set up my computer where I can run Android ADB/Fastboot commands from terminal.

I tried the guide here
[URL="http://forum.xda-developers.com/showthread.php?t=537508"]
http://forum.xda-developers.com/showthread.php?t=537508[/URL]

And I tried a variant of that a friend of mine recommended.

I still get nothing. :confused: terminal won't recognize adb as a command and doesn't recognize fastboot as a command.

This is getting kind of frustrating for me, but I know the answer has got to be out there. If someone could sorta baby step me through this, i'd appreciate it.

Something which concerns me is, is it possible that my .bashrc is screwed up at this point from making changes to it? I hope not. Due to the install being so fresh, i can start from scratch if needs be, but would rather not.

Thanks a ton!

---

### Post by translunary on 2011-07-27
Download the fatsboot and adb from the website (in you directory of Download)
then do the rest:
cd Download
sudo cp fastboot adb //bin/
enter your password
cd //bin/
sudo chmod +x fastboot adb

done!

---

### Post by translunary on 2011-07-27
for more details see it here
[http://wiki.cyanogenmod.com/wiki/ADB](http://wiki.cyanogenmod.com/wiki/ADB)

---

