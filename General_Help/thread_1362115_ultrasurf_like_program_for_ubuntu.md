---
title: "ultrasurf like program for ubuntu?"
date: 2009-12-22
forum: General Help
---

### Post by Mirrorboy on 2009-12-22
i installed Ubuntu 9.10 on my computer at school, but i forgot to look up ultrasurf like programs beforehand. i kinda live off it since my schools web blocks are like the great wall of china. so is there anything i can install that will act like ultrasurf?

---

### Post by audiomick on 2009-12-22
I have no experience with anything like that, but I found this. Might help..

[http://thoughtyblog.wordpress.com/tag/ultrasurf/](http://thoughtyblog.wordpress.com/tag/ultrasurf/)

---

### Post by Mirrorboy on 2009-12-22
i tried running ultrasurf in wine and it didn't work, though. wouldn't even start. i noticed that the tutorial is using arch linux. does Wine work differently from distro to distro?

---

### Post by thoughtcrime@arch64 on 2010-01-02
I am the author of a piece of software I call [ghostship.]("http://ghostship.sf.net") It allows to execute Ultrasurf just like an Unix daemon. However, it is not really ported to Ubuntu yet, but since at least you show interest in Ultrasurf and Ubuntu, I'm going to do that now.

Until then you can install Ultrasurf just like any wine application. As with most of those, you will find a [good howto in their appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18248") (scroll down to see it). Follow it step by step and Ultrasurf will work on Ubuntu (this guide is not limited to any distribution).

regards, thoughtcrime

---

### Post by Mirrorboy on 2010-01-02
i tried running ultrasurf through wine, but it wouldn't open for some reason. i think i tried ghostship but it didn't work on ubuntu since it's made for archlinux. if you can port it like you said, that'd be great. but would i still need to run ultrasurf? or does ghostship take the place of ultrasurf?

---

### Post by thoughtcrime@arch64 on 2010-01-02
Ghostship takes care of installing and updating Ultrasurf. So you would just need to install ghostship. I can't say for sure, but I should get the port done the next few days (if not today) :D

---

### Post by Mirrorboy on 2010-01-02
awesome! thanks a bunch :)

---

### Post by thoughtcrime@arch64 on 2010-01-03
Alright, I am kinda busy now, so I'll keep it short.

[http://sourceforge.net/projects/ghostship/files/ghostship_0.5-1_all.deb/download](http://sourceforge.net/projects/ghostship/files/ghostship_0.5-1_all.deb/download)

There's the release, download and install it. I couldn't test it 100%, because wine is slow as hell in virtualbox, but it should work. If it does not, please report bugs and I'll fix it.

After you install it, start ghostship with
sudo /etc/init.d/ghostship start

and open up
file:///var/lib/ghostship/status/ubuntu.html
in firefox. click the more... button there and it will show you the logfile (in realtime), so you'll see what's going on. If something strange happens, run
sudo /etc/init.d/ghostship stop
and everything ghostship related (ghostship will have its own user) will be killed immediatelly.

Please tell me, how good it works, report bugs and feature requests, thanks :)

PS: You will also want to tweak /etc/ghostship/ghostship.conf if Ultrasurf gets restarted too often or something.

PPS: I'll blog about this later, that's why there are no news yet on the project homepage.

Enjoy :)

Bugs and Feature Requests:
[http://sourceforge.net/tracker/?group_id=283605&atid=1202565](http://sourceforge.net/tracker/?group_id=283605&atid=1202565)

---

### Post by Mirrorboy on 2010-01-04
it gives me an error saying Error: Dependency is not satisfiable: wine1.2 (>= 1.1.32). i really have no idea what that means, but i also can't get Ultrasurf to open. i have the U96 file on my desktop and nothing happens when i open it.

---

### Post by thoughtcrime@arch64 on 2010-01-04
First try updating your system. If it does not work (I am not sure which wine version is in Ubuntu's repositories), then follow the steps on the following website one by one to get the newest version of wine:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Mirrorboy on 2010-01-05
my system is up to date and i have the latest wine. no idea why it isn't opening. plus i'm still getting that Error: Dependency is not satisfiable: wine1.2 (>= 1.1.32). any help?


EDIT: got it. had to do a wine update that wasn't coming up in the update manager. had to go through synaptics. got everything installed now. thanks for the port :)

---

### Post by thoughtcrime@arch64 on 2010-01-05
You obviously do not have the lastest wine version, or else the dependency would not fail. Please follow what this website says to get the lastest wine version:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

EDIT: Ah cool, you've solved it. Just report when you run into bugs or something :)

---

### Post by luzy on 2010-03-01
Thanks a lot! This works great!

Unfortunately, hulu.com notices though that I am anonymizing my IP address...
Well, I guess you just can't have everything...

Thanks again!

---

### Post by .Ix on 2011-01-05
I get this when I try to run ghostship with the command in the previous page:


rm: cannot remove `/var/lib/ghostship/.wine/dosdevices/z:': No such file or directory
ln: creating symbolic link `/var/lib/ghostship/wine': File exists
mv: cannot move `u1005.exe' to `../.wine/drive_c/ultrasurf.exe': No such file or directory


The ghostship status page also says that ultrasurf is offline. I've previously tried to install Ultrasurf with wine, but it didn't work. It gave me an error that said UltraSurf needed to exit. Could that be the problem?

---

### Post by Zipdaman12 on 2011-09-12
I am having a similar issue here is what I am getting:

rm: cannot remove `/var/lib/ghostship/.wine/dosdevices/z:': No such file or directory
ln: creating symbolic link `/var/lib/ghostship/wine': File exists

anyone help?

Zip

---

