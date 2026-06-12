---
title: "Can't Install 10.04"
date: 2010-04-29
forum: General Help
---

### Post by msmooth on 2010-04-29
Insert the boot disk into the drive, boot with dvd drive... get a purple screen with keyboard on the bottom then BAM. Input signal out of range(no video). Hanns G 28' 1080p monitor PNY GTX 260./tear

---

### Post by Smart Viking on 2010-04-29
(Just as you know i'm not very skilled)

Have you tried to use an live usb instead? Maybe there is something wrong with the cd.

EDIT:

To make a live usb is not hard, jsut use the iso file with this program: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by P4man on 2010-04-29
> **msmooth said:**
> Insert the boot disk into the drive, boot with dvd drive... get a purple screen with keyboard on the bottom then BAM. Input signal out of range(no video). Hanns G 28' 1080p monitor PNY GTX 260./tear


When you see that keyboard on the screen (congrats on recognizing it as such btw!), press a key. You will get a menu and one of the options should be safe graphics mode. 

edit: waiting as i wrote earlier wont help as you need to select the language in the screen you cant see. Maybe pressing ENTER will proceed to the next step (using english as language) but Im not entirely sure.

---

### Post by msmooth on 2010-04-29
I'll try a USB boot thanks

---

### Post by P4man on 2010-04-29
USB wont help. An out of range error means your PC is sending a signal to your monitor that the monitor cant handle. The pc isnt freezing up or nothing wrong is gonig on except a wrong resolution / color depth / refresh rate. The usb will give the same problem. Try safe graphics (see post above)

---

### Post by kayas80 on 2010-04-29
I have the same problem as the original poster.

---

### Post by P4man on 2010-04-29
> **kayas80 said:**
> I have the same problem as the original poster.

may I suggest the same solution :) ? Or did you try that already?

---

### Post by kayas80 on 2010-04-29
> **P4man said:**
> may I suggest the same solution :) ? Or did you try that already?

I tried, unless I'm blind there is no option for safe graphics mode on the 10.04 boot cd.

---

### Post by msmooth on 2010-04-29
Works with a very old CRT monitor.. they should fix that.

---

### Post by P4man on 2010-04-29
> **kayas80 said:**
> I tried, unless I'm blind there is no option for safe graphics mode on the 10.04 boot cd.

You have to press a key while you see that keyboard logo at the bottom. Press escape or space (think any key works, not sure). Then you will get a menu. And feel free to complain about hiding that menu here:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

---

### Post by msmooth on 2010-04-29
I went thru the options in the menu F4 and F6 did not see any safe graphics mode. the only workaround i've found so far is to use a crt monitor.

---

### Post by P4man on 2010-04-29
OK, I feel like an idiot now. You're right, they removed that in their infinite wisdom.

Found this though:
> 
Safe graphics mode was removed from the F4 menu, as it isn't needed any more. **Press F6 and select nomodset,** is now the preferred way to boot if your graphics card isn't detected properly. Using nomodset solved my boot problem with yesterdays daily build

Sorry for the confusion!

nomodset..  thats rather obvious for human beings isnt it? Gotta problem with the monitor, gotta press a key without anyone telling you, and then select an option called nomodset. I guess thats progress :(

---

### Post by kayas80 on 2010-04-29
> **P4man said:**
> OK, I feel like an idiot now. You're right, they removed that in their infinite wisdom.

Found this though:


Sorry for the confusion!

nomodset..  thats rather obvious for human beings isnt it? Gotta problem with the monitor, gotta press a key without anyone telling you, and then select an option called nomodset. I guess thats progress :(

That worked for me. Problem is once its installed it doesn't load. It hangs before GRUB usually loads and just hangs. I have no other OS on t he system.

---

### Post by msmooth on 2010-04-29
Wow that really sucks. :( I've managed to get it up and running on my normal monitor. but the bar thats ontop is f*d.

---

### Post by P4man on 2010-04-29
May I suggest both of you open new threads, as clearly these are very different issues and otherwise this thread will become a mess. If you dont get a response fast enough, feel free to nudge me and point me to the thread(s)

---

### Post by oldfred on 2010-04-29
With the RC I had to use nomodeset both to get the installer to run and initial boot until I got nvidia installed.

[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

You can also save this setting so that it's applied at every  boot by adding it to your grub config (for GRUB 2: edit /etc/default/grub and add nomodeset  to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset  to the line beginning with # kopt=, then run sudo update-grub).  ([533784]("https://bugs.launchpad.net/bugs/533784"), [541501]("https://bugs.launchpad.net/bugs/541501"))

---

### Post by LostOverThere on 2010-04-30
Getting the same issue, but nomodeset works fine. Perfectly obvious. Start, quickly mash some keys, press F6, and then select some random function to boot with. Linux for Human Beings is here! ;)

Anyway, is there a launchpad thread opened regarding this?

---

