---
title: "GNOME only starts in safe mode"
date: 2010-10-14
forum: General Help
---

### Post by Darac on 2010-10-14
Hi,

I did a clean install of 10.10 on my Asus A6R laptop today. Previously i had 10.04 on it.

After installation and the first reboot my GNOME won't start in normal session. If I select *Ubuntu Desktop Edition (safe mode)* everything works fine, but on the normal *Ubuntu Desktop Edition * session, GNOME just won't start. I have a mouse cursor that i can move around and a normal background. Also i can hear the usual startup sound.

I'm really bugged by this, so I would appreciate any ideas you guys might have for solving this problem.

If you need any logs I'll be more than happy to post them, just tell me which one do you need.

---

### Post by requeth on 2010-10-14
Try updating your video driver, or choosing proprietary/non-prop depending on what's chosen now. Alternately reinstall x11.

---

### Post by Darac on 2010-10-14
One more thing. I tried booting the LiveCD but the same thing happens there. GNOME just won't start, there's only a mouse cursor. :( 

> **requeth said:**
> Try updating your video driver, or choosing proprietary/non-prop depending on what's chosen now. Alternately reinstall x11.

Don't think i can upgrade my graphics driver since it's an old ATI Radeon 200M Xpress chip and ATI discontinued support for those chips. :(

Anything else i can do?

---

### Post by rroques on 2010-10-15
Hi there. 

I just installed ubuntu an hour ago and face the same issue. If you get some info on how to resolve this, I am interested.

Cheers,
Remi

---

### Post by Quackers on 2010-10-15
I wonder if Ubuntu has dropped support for your card in view of the fact that ATI have?

---

### Post by rroques on 2010-10-15
That would be too bad. But in safe-mode it works very fine. What is the particularity of that mode ? I can watch movies without any issue so that graphic card seems to work smoothly.

---

### Post by Quackers on 2010-10-15
I'm only guessing but it may be that safe mode doesn't try to load the proprietary drivers.

---

### Post by rroques on 2010-10-15
I removed the xorg drivers for ati and radeon and it apparently solved the issue. I ll investigate if I can properly watch videos without those drivers.

thanks for the support. 

I am back on ubuntu !!!!

---

### Post by Quackers on 2010-10-16
Oh well, that's a start! I think many people just use the open source Nouveau driver without problems.

---

### Post by iwbcman on 2010-10-19
Darac,

I think I might have a suggestion for you.

Your laptop has the same graphics chipset as my Toshiba laptop does(Toshiba Satellite L25-S121).

I ran into the same problem immediately after upgrading to Maverick,ie. could not get to the desktop after logging in at gdm-after logging in the computer just kind of froze-mouse still moved around, could see the background from the log in, but the desktop never showed.

In fact I encountered this problem during my last upgrade(lucid), but as that upgrade was a while back I had forgotten what I needed to do to get things working.


The key to this problem is that our graphics chipset does not support KMS(Kernel Mode Setting). And Ubuntu has been aggressively pushing KMS support for the past couple of releases. 

The soultion to this problem is actually quite simple:

using your favorite text editor, as root, create a file called: 
radeon-kms.conf

and in this file place the following :
options radeon modeset=0

and save this file, as root, in :
/etc/modprobe.d/

once completed simply reboot your computer and select the default ubuntu session. voila, il marche!


ps. in case you are not familiar with editing/creating files as root, there are many ways to do this. The first and easiest way to do this is:

1)
a) open the applications menu, select Accessories, and click on terminal
b) once the terminal opens type: sudo su
c) enter your password
d) now type(or copy paste) into the terminal:
echo "options radeon modeset=0" > /etc/modprobe.d/radeon-kms.conf

or 2)
a) open the applications menu, select Accessories, and click on terminal
b) once the terminal opens type: 
sudo nano -w /etc/modprobe.d/radeon-kms.conf
c) type your password and then type(or copy paste) into the nano text editor:
options radeon modeset=0
d) now press:ctrl x
e) and when prompted to save the file press: y

or 3)
a) press alt f2
b) type: gksudo gedit and click the "run" button(you will be prompted for password)
c) type (or copy paste) into the new empty text file:
options radeon modeset=0
d) go to the file menu and select "Save As.."
e) name the file: radeon-kms.conf
d) navigate to the /etc/modprobe.d/ directory(starting at "filesystem in the left column, then select "/etc" direcotry, then "modprobe.d" directory)  and press save.


if you already know how to do stuff like this, forgive me for being so verbose ;)

---

### Post by epedersen on 2010-10-22
I found that after I added the new radeon-kms.conf file it helped to run the following:

sudo update-initramfs -u

... from the instructions here [https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting")

---

### Post by OveraverageJoe on 2011-03-12
Thanks so much iwbcman! Saved me a ton of reinstalling stress!

---

### Post by londubh on 2011-03-16
This solution worked for me after installing Ubuntu 10.10. Thanks. I have Toshiba Satellite L25-S126.

> **iwbcman said:**
> 
Your laptop has the same graphics chipset as my Toshiba laptop does(Toshiba Satellite L25-S121).

I ran into the same problem immediately after upgrading to Maverick,ie. could not get to the desktop after logging in at gdm-after logging in the computer just kind of froze-mouse still moved around, could see the background from the log in, but the desktop never showed.

In fact I encountered this problem during my last upgrade(lucid), but as that upgrade was a while back I had forgotten what I needed to do to get things working.


The key to this problem is that our graphics chipset does not support KMS(Kernel Mode Setting). And Ubuntu has been aggressively pushing KMS support for the past couple of releases. 

The soultion to this problem is actually quite simple:

using your favorite text editor, as root, create a file called: 
radeon-kms.conf

and in this file place the following :
options radeon modeset=0

and save this file, as root, in :
/etc/modprobe.d/

once completed simply reboot your computer and select the default ubuntu session. voila, il marche!


---

### Post by pinguoshangu on 2011-08-23
I recently installed 11.04 and run into the same issue. Able to solve the problem by following the instruction! This is so helpful. I think I will stick with Ubuntu. The command and conf seems too difficult for newbie, but I like the fact that you CAN actually know what's going on in the system rather than randomly power off power on and hoping it will work with your finger crossed. And the community is really welcoming. Not sure if the author will look at this post again, but thank you very much.

---

### Post by pinguoshangu on 2011-08-23
Btw, I use ACE AO722, CPU-AMD DUAL-Core Processor c-50. The version is 11.04

---

