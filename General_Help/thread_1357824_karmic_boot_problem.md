---
title: "karmic boot problem"
date: 2009-12-17
forum: General Help
---

### Post by migs73 on 2009-12-17
I am getting an intermittent and annoying problem on boot on my Dell Inspiron 1501 laptop.
Grub seems to load fine and I get the usual 'boot from hd0,0' followed by a hex number. Then I get the ubuntu logo which is then followed by the 'boot from hd0,0 with hex no.' and below this I get 'Ubuntu 9.10 dell-laptop tty1' and below this 'dell-laptop login:'.
This will sit for a couple of minutes and then '*stopping Firestarter firewall...'. This happens even if I put in my login and password (it will then give a terminal prompt but the Stopping Firestarter text still comes up) and then a minute or so later the Ubuntu splash comes up an I get the normal login screen. 

After login in and checking the status of firestarter, it shows that the firewall is disabled (see attachment).  It will not allow me to restart it as it states either et0 or eth1 device is not ready.  Also note the eth1 device is called eth1_rename (you can only see the eth1_r but I found it somewhere else and it had the full name), but this is **only if eth1 is the device that fails**. Once the firewall is restarted this shows no activity but there is on eth0. 
If eth0 fails the names are just eth0 and eth1 but once the firewall is restarted both show identical activity even although eth1 is still shown as not ready. For me to get the firewall to restart I have to run the set up wizard again for the device that is ok.
I have tried uninstalling and reinstalling Firestarter but this made no difference.
Please help.

Migs

---

### Post by migs73 on 2009-12-18
*bump*

---

### Post by migs73 on 2009-12-22
Another bump!!

---

### Post by migs73 on 2010-01-01
Just to add to the confusion, if I let the computer boot up regardless, if i then stop and start my netwoek connection the firestarter restarts and all is okay after that.
Surely someone must have an idea as to what is happening??

---

### Post by Muttley99 on 2010-01-01
> **migs73 said:**
> Just to add to the confusion, if I let the computer boot up regardless, if i then stop and start my netwoek connection the firestarter restarts and all is okay after that.
Surely someone must have an idea as to what is happening??

I had a similar problem, fixed by adding my user to sudoers! This allowed Firestarter to work correctly.
Not sure if it's the same problem but worth a try;

type;

[HTML]visudo[/HTML]

replace 'name' with your user and add it to the end of the file;

[HTML]%name ALL=NOPASSWD: /usr/sbin/firestarter[/HTML]

**by the way; make sure that if you get any errors on logging out of nano, you go straight back in by typing 'e' otherwise you'll have to use a live cd.

---

### Post by migs73 on 2010-01-27
Thanks Muttley99
Sorry for the dealy in reponse I've been busy on other things.
I am a bit of a noob so I assume you mean to put this code in via terminal? I will give this a try, do I have to add all users to be sudoers or does it just look for one?? Remember this is before I login.

---

### Post by Muttley99 on 2010-01-27
Yes, just open a terminal. Just to correct my previous post;

[HTML]sudo visudo[/HTML]

then enter the line I gave you.

---

### Post by migs73 on 2010-01-28
Thanks Muttley99, your code seems to get my firestarter running when I log in without any intervention from me. Of course I would still like to know why my boot pauses half way through asking for my dell-laptop login. I only have to leave it a minute or so till the boot up continues, but it is very annoying.
NB now when the boot stops it not only says 'Stopping Firestarter Firewall' it also says 'nmbd running' and sometimes something about samba daemons starting. I know these have to run, I just thought I would add the info as it might give someone an idea as to when/why the boot pauses.

---

### Post by Muttley99 on 2010-01-28
Maybe setting Samba to run later in the boot process! 
This should be something like this;

[HTML]sudo update-rc.d samba defaults 99[/HTML]

However, There are other people here better qualified to help than me - It's better you get advice from them on this before you try the above! ;)

---

### Post by migs73 on 2010-02-02
Looking at some other posts about boot problems and someone mentioned looking in the log file viewer. I did this and got a very strange result (see below). Anyone got ant ideas about the 'unknown key pressed' problem. As you can see it is constantly showing pressed and unpressed about 3 times a second.
Edit;
Hey after a bit of searching found this [http://ubuntuforums.org/showthread.php?t=1282027](http://ubuntuforums.org/showthread.php?t=1282027) and it seems to have worked as far as the key press problem is concerned. Also I have booted twice in a row now without the pause. It has been a while since that happened. Hopefully this is what I needed. If ok for a while I'll mark as solved.

---

### Post by migs73 on 2010-02-15
Just a final note on this matter. Everything okay after the key press problem workaround mentioned above. It did come back after I upgraded my RAM but after the workaround again all boots have been flawless. That is in excess of 20 boots.

---

### Post by migs73 on 2010-04-30
Did come back with a vengeance for a while about a week or so ago. Recently upgraded to 10.04 and so far no boot hiccups.

---

