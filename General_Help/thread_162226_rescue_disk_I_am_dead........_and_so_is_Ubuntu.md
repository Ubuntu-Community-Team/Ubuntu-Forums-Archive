---
title: "rescue disk? I am dead........ and so is Ubuntu"
date: 2006-04-18
forum: General Help
---

### Post by engineering.concepts on 2006-04-18
Please help...
Ubuntu will not boot into a GUI and I get LOTS of errors.... Here is a detailed list of the mess that I made..... can it be fixed?

I tried to install XFCE to speed up Ubuntu - I found this on [http://www.psychocats.net/ubuntu/xubuntu.php](http://www.psychocats.net/ubuntu/xubuntu.php)

username@ubuntu:~$

4b. Once at that prompt, type sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list

4c. You'll then be editing the sources.list file using the text editor called Nano.

5. Delete the # signs (also called comments) in front of anything that looks like a web address. # signs basically tell Ubuntu "Ignore this line--it doesn't exist."

6. Then save (Control-X), confirm (y), and exit (Enter). Now you have more online repositories to draw from--the ones you need to install Xubuntu.

7. Next type sudo apt-get update
sudo apt-get install xubuntu-desktop

8a. At this point, you can type startx to get into XFCE.

8b. If you want a graphical login screen you may also want to run this command: sudo apt-get install gdm

After it has finished installing, type sudo /etc/init.d/gdm restart to get the login screen started. 

Once I did this my computer reboot and it said that XFCE could not start.
I entered startx, but just more errors.

Being very smart ](*,)  I decided to perform a command: sudo apt-get remove gdm
because I realized (too late ) that I was not supposed to do step 8 above.

I then renamed a file (something like initine.ini.old to initine.ini) because screwed up again and I thought this was the sources.list_backup file ](*,) 

Oh Boy.......
I messed things up bad.................
Is this fixable? Or should I just bite the bullet and format? How can I get the info off my machine? I still have access to a WinXP laptop?
Thanks](*,)

---

### Post by engineering.concepts on 2006-04-18
I tried :

Issue this command to setup the X Windows Server from the command line
Code:

sudo dpkg-reconfigure xserver-xorg

as listed in the forums - but I get: /bin/sh: sudo: not found

so I try :
dpkg-reconfigure xserver-xorg
and I get
 /bin/sh: dpkg-reconfigure: not found

ohhhhh boyyyyy - it's gonna be a long night....](*,)

---

### Post by OffHand on 2006-04-18
You can probably rescue your data with a live cd (ubuntu or knoppix for instance). So you might want to start download one. 
I have the feeling it can be fixed though, just don't ask me how.

---

### Post by engineering.concepts on 2006-04-18
I'll give the live CD a try - I have both the live and full install version. Would the full install give me a repair option?

---

### Post by engineering.concepts on 2006-04-18
I am currently using the live cd, but I cant find any of my files. Any thoughts?

I think the file I messed up - initrd.img.old and changed it to initrd.img

---

### Post by slackern on 2006-04-18
Just a quick thought, can you access /var/log/auth.log ?
In that case maybe you can see what you did if you used sudo since it logs the commands you run and maybe that will help you trace the change you did.

Mine shows as an example:

Apr 19 00:32:27 localhost sudo: username : TTY=pts/0 ; PWD=/etc/apt ; USER=root ; COMMAND=/usr/bin/apt-get upgrade

after i do a "sudo apt-get update"

---

### Post by engineering.concepts on 2006-04-18
Thanks for the help Slackern, but I can not get into that dir. once I get into var my only option is a folder called lock.

Yay!!! I'm doomed!!!](*,)

---

### Post by audax321 on 2006-04-19
[QUOTE=engineering.concepts]Thanks for the help Slackern, but I can not get into that dir. once I get into var my only option is a folder called lock.

Yay!!! I'm doomed!!!](*,)[/QUOTE]

Are you sure your not looking at the LiveCD's filesystem? If you are using the Ubuntu LiveCD you will have to manually mount all of the partitions on your hard drives to access the data. Depending on how your computer is setup, this could be quite tedious. If you can, try getting a Knoppix LiveCD from [www.knoppix.org](www.knoppix.org)

It should automatically detect all your partitions so you can just click the icons on the desktop and transfer the files to your laptop using Samba or FTP or something. The Ubuntu LiveCD is good for previewing Ubuntu, but it's not really that great for fixing things, Knoppix is much more convenient in that regard.

Good Luck.

---

### Post by handy on 2006-04-19
It's true, once you mount your partitions, you will be able to access your data.

So, don't loose heart, or patience :KS

Knoppix will save you a lot of work in this regard.

---

### Post by engineering.concepts on 2006-04-19
Thanks for the help everyone  - :) 

I currently reinstalling Ubuntu (on another Laptop HD) and I am going to try to use an USB-IDE-laptopHD converter to read the data once it is installed. I will also start downloading Knoppix - just incase

---

### Post by handy on 2006-04-21
Let us know how you went, it helps with the knowledge base?

Thanks!:KS

---

### Post by vavoem on 2006-04-21
Why dont'you just try run
Before you go on formatting you're drive because i don't think you're lost at all.

sudo apt-get install --reinstall xubuntu-desktop

That'll probably fix things.

---

### Post by engineering.concepts on 2006-06-04
Update - I am back :) 
Knoppix was not able to mount the drives, so I tried to reinstall ubuntu over the old partitions hoping that I could recover some of the data, I gave up 1/2 way through b/c I was just messing up the partitions further. 

The only solution i could get to work - was posted on ubuntu forums - a program called "Kernel for Linux" Linux Data recovery software - [http://www.nucleustechnologies.com/Linux-Data-Recovery-Software.html](http://www.nucleustechnologies.com/Linux-Data-Recovery-Software.html)

A free version of this software lets you see what it can and cant recover - they you have to pay $55 for the software....not bad I guess - it was a bigger blow to my ego having to use a WinXp system to save my Linux. Recovered all my information, using winxp and setting up my laptop (ubuntu ) Hard drive with a USB to IDE connector - then using an IDE to laptop hard drive converter. 

Thanks for everyone's help on the forum - If I would have looked here sooner I would have saved myself hours and hours of trouble and $55:p

---

### Post by dmizer on 2006-06-04
advice for the future: if you run into trouble and things aren't working right DON'T PANIC.  even if you're without your computer for several days while you hunt down the problem, it's a small price to pay for data recovery.

---

