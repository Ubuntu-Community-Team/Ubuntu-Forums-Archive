---
title: "Unable to boot 9.10 without a screen attached"
date: 2010-02-21
forum: General Help
---

### Post by houldsworth1 on 2010-02-21
I have a desktop version of Ubuntu 9.10 installed on a machine that generally I only want to access remotely (using TightVNC).  That is because the machine is under my wife's desk and she is getting a little ticked off that there is a screen right by her foot.

The problem is that if I remove the screen then the system gives me a startup error and will not boot.  I then have to reattach the screen and select normal startup.

Can someone tell me what I need to do for the system to boot without the screen attached?  

Thanks!

---

### Post by spiky001 on 2010-02-21
do you mean it wont boot past bios?

---

### Post by houldsworth1 on 2010-02-21
> **spiky001 said:**
> do you mean it wont boot past bios?
 
Correct.

---

### Post by spiky001 on 2010-02-21
In he ios there is an option to boot ignoring dissconnected screen  etc see if that works

---

### Post by houldsworth1 on 2010-02-21
My apologies - it would seem I was not clear. When I boot withou the screen attached the system does not start normally. If I then attach a screen the following options are presented to me and, if I select the first one, then the system starts normally.
 
I would like this selection to not be presented and, instead, for the system to start up as though a screen is attached so that I can then use TightVNC to connect to this machine from my main PC.
 
Thanks

---

### Post by spiky001 on 2010-02-21
ok i see that but if you leave it dose it not start by itself

---

### Post by spiky001 on 2010-02-21
ok have googled this 

[http://old.nabble.com/booting-ubuntu-without-a-monitor-td23289389.html](http://old.nabble.com/booting-ubuntu-without-a-monitor-td23289389.html)
i,ll look some more

---

### Post by spiky001 on 2010-02-21
This looks better

[http://blog.olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/](http://blog.olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/)

let me know how you get on

---

### Post by houldsworth1 on 2010-02-21
Thanks!  But...no dice.
 
I tried the second option of creating the xorg.conf file (since that looked easier).  Afterwards I rebooted and...the system didn't start.  I reconnected the monitor and still couldn't get anything to show up.  After manually shutting down and starting again the system came up but I had the spinning cursor in the middle of the screen for a long time.  I removed the file xorg.conf file created and the system went back to booting quickly and no spinning cursor.
 
I then decided to try the other option but received a message stating that sysvconfig could not be found.  
 
I tried to find an option on the BIOS to ignore the monitor but there isn't one as far as I can see.  The only options are the monitor type AG? (can't remember the last character) and PCI.  AG? is currently selected.
 
Any other suggestions?
 
Thanks!

---

### Post by houldsworth1 on 2010-02-21
OK...trying not to give up. I found out that sysvconfig is no longer part of ubuntu 9.10 - there is a new utility called sysv-rc-conf. In installed that but it would appear that gdp isn't running anyway. See attached:
 
That said...when I type in sudo service gdm stop my connection to the machine is lost through TightVNC and I can't reconnect so it was obviously doing something...
 
I can then log in direclty on the machine but can't remotely access it again and...once I reboot...I am back where I started.
 
Seems like this is much harder than it needs to be :)

---

### Post by houldsworth1 on 2010-03-07
Anyone have any advice?  I'm totally stuck here and will have to revert to Windows if I can't get this solved as I need the screen attached to that box for something else.
 
Thanks!

---

### Post by houldsworth1 on 2010-03-17
*** Solution ***
 
OK - following the advice in another thread I have changed the value for GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub to an empty string and changed /etc/X11/default-display-manager to be empty. I then ran 'sudo update-grub' to update things and the machine will now boot without a screen attached. 

The machine now starts without the GUI and drops to a login prompt instead and, after logging on, I can access the machine through the CLI.
 
I then installed SSH using 'sudo apt-get install ssh' and can now access the machine using putty from my windows box.
 
Thanks to everyone for their help.

---

### Post by houldsworth1 on 2010-03-26
Additional update.  After the above solution I discovered that the machine would boot but would then hang after about 10 minutes.

I finally tracked it down to the following solution and this seems to solve all issues.
[COLOR="Red"]Alright, found it...

First, resist the temptation to modify /boot/grub/grub.cfg ... it'll get overwritten someday soon.

First, In /etc/default/grub, Change this line (sudoedit or whatever you like) :
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
for
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
then run
Code:
sudo update-grub[/COLOR]

---

