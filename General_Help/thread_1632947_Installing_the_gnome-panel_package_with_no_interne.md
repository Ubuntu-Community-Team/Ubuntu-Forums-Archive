---
title: "Installing the gnome-panel package with no internet"
date: 2010-11-28
forum: General Help
---

### Post by kolo-01 on 2010-11-28
so i restarted my computer to find that gnome-panel package is gone- dont know how this happened, i use docky which still works and have all my main applications on there so i can run terminal, package manager etc, but the only way i know of connecting to the internet is through notification/indicator applet on gnome-panel and so cant install that package until i get internets, can i sort out an internet connection through terminal or some other way? searching this problem- it doesnt happen as much as i thought it would..

---

### Post by Frogs Hair on 2010-11-28
Try right clicking the top of the screen and select new panel , then right click the panel and select add to panel. Add the notification area and other missing applets. If you haven't removed the panel from installed programs this should restore it.

---

### Post by WorMzy on 2010-11-28
Are you sure it's gone, and not just not running? What does ```
dpkg-query -l gnome-panel
``` show?

If it says something like
```
ii  gnome-panel    1:2.30.2-0ubun launcher and docking facility for GNOME

```
Then according to dpkg it's still installed. In this case, what does running "gnome-panel" in a terminal yield as output (if anything)

---

### Post by kolo-01 on 2010-11-28
im sure that the package has been removed somehow, in package manager gnome-panel is empty and lack of internet is preventing me from installing it, a right click on the desktop has no add panel option. i dont think its important but i was unable to run the dpkg-query, giving me 'unknown option -1' when i tried it..
thanks for the replies, im 99% sure the package has somehow been removed so do you know where i should go from there?

---

### Post by WorMzy on 2010-11-28
It's a lower case L, not a one.

If you have the disk that you used to install Ubuntu, you can install gnome-panel from that.

---

### Post by kolo-01 on 2010-11-28
> **WorMzy said:**
> It's a lower case L, not a one.

If you have the disk that you used to install Ubuntu, you can install gnome-panel from that.

with the l, it comes up with:

status=not/inst/conf-files/unpacked/hal F-conf/Half - inst/trig- aWait/Trig- pend

/ Err?=( none)/Rei nst - required (Status, Err: uppercase=bad)

then below it says version and description..


so i might be wrong and the package is there somewhere, do you know how i could get it going again?

---

### Post by WorMzy on 2010-11-28
You didn't include the important part, the last line. :P

If it says "_ii_ gnome-panel blah blah version info blah", then your system still thinks that it's installed.

Does ```
which gnome-panel
``` return anything? "/usr/bin/gnome-panel" means that you still have the gnome-panel binary. If that's the case, then definitely try running "gnome-panel" in a terminal (you didn't say whether you already tried this).

---

### Post by kolo-01 on 2010-11-28
just running gnome-panel in terminal returns 'the program is not installed' then gives me the apt-get, that is the thing that gave me the best clue that the package isnt there, the binary is not there in usr/bin..

but in the dpkg its is coming up as '1:2. 30.2- 1ubuntu3' under the version column.

it doesnt seem there to me, so not sure why its giving me a version, do you think getting it off of an ubunut cd or connecting to the net (im on a someone else's laptop now) would be the easiest way of reinstalling?

---

### Post by WorMzy on 2010-11-28
It'll sometimes say the version whether it's installed or not. The **_ii_** means that it's installed (or at least, dpkg *thinks* that it's installed). If it says **_un_**, then it's uninstalled.

If you put the CD that you used to install Ubuntu into the CD drive, then run
```
sudo apt-get update
sudo apt-get install gnome-panel
```
It should install the gnome-panel available on the disk.

---

### Post by kolo-01 on 2010-11-28
i know that gnome-panel was on my 9.1 cd when i installed ubuntu from it, but a sudo apt-get update/install gnome panel is still trying to fetch it from the online repositories and doesnt want to look at the cd, is there a code that i need to use to tell it to look on the cd?

---

### Post by WorMzy on 2010-11-28
It was my understanding that it'd automatically detect it, but this doesn't seem to be the case. Try putting the CD in the disk drive then running
```
sudo apt-cdrom add
```
Then
```
sudo apt-get update
```
and finally
```
sudo apt-get install gnome-panel=1:2.28.0-0ubuntu6
```

I *think* that will attempt to install the version on the disk, but I'm not 100% sure.

---

### Post by kolo-01 on 2010-11-29
my problem has recently got worse, i removed all of the evolution packages and have discovered that this is the reason i now cant log in at all, so i am trying to log in so i can recover some things on my system.. thanks a lot for your replies

---

### Post by WorMzy on 2010-11-29
Yes, uninstalling evolution will uninstall most of Ubuntu's other packages too. It should tell you this when you try to uninstall evolution, but if you used the Ubuntu Software Centre (Applications -> Ubuntu Software Centre) then, due to a bug, it won't tell you this. If you can get Ubuntu to install from the disk, then reinstall ubuntu-desktop package, and all the other dependencies should be dragged in too.

---

