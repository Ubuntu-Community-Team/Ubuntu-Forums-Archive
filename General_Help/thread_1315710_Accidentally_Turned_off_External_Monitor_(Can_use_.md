---
title: "Accidentally Turned off External Monitor (Can use command line) Turning it back On?"
date: 2009-11-05
forum: General Help
---

### Post by cowcow1212 on 2009-11-05
Hello guys, I have a problem with my setup. I posted this in the laptop forum, but I am hoping it will get more of a response here.

When I first upgraded, everything worked fine with the monitor, it stopped working because I switched the external (working) monitor to off. How can I turn it back on? This was in the systems settings window in Ubuntu. 

I can open up a terminal (alt+ctrl F1 to F6), and there the external monitor works.

The main screen, the original flip-down LCD screen, display 0 is broken. 
  
Ilooked over the log files in /var/log folders, and it seems that the screen is registering (which I see when it is booting up), but when it gets to kdm welcome screen it shuts it off. 

The log file var/log/Xorg.1.log states event 11 was detected, and does nothing more. This does not happen in the non-working monitor, 0, which seems to continue past that point because it does not encounter event 11. This makes me think that this event is the source of the problem. 

I have tried xrandr --output VGA-0 which then states DISPLAY=0.1 cannot be opened. 

I have also tried shutting down kdm (sudo /etc/init.d/kdm stop), then tried reconfiguring xorg by, sudo dpkg-reconfigure -phigh xorg; and then tried to restart kdm by sudo /etc/init.d/kdm start . 

xfix does not work either. 

When I have tried to initiate my drivers on xorg, using aticonfig --initiate -v, I get an error stating a segmentation fault had occurred.

Does anyone know how to force the monitor to view the login screen of the X7 server? 

I know it has something to do with the Default Screen, but changing xorg manually at the level of even /etc/X11/xorg.conf does not change this monitor from being off! According to xorg's manual, this is the highest level xorg works from, and since it is being found and initialized prior to kdm starting; therefore, I think this is an issue of kdm. 

Any ideas? Thanks for your time and help guys!

PS Please note I can boot two different live CDs (KNOPPIX and Ubuntu 9.10 install CDs), please see below post.

---

### Post by P4man on 2009-11-05
Did you try control alt F8 and F9 ?
TBH it would somewhat surprise me if that was the actual solution but hey its easy to try and not so much typing for me :p

---

### Post by kyuubi777 on 2009-11-05
my key setup is Fn + F7  to set alternative display... there should be something like that for you

---

### Post by cowcow1212 on 2009-11-05
> **kyuubi777 said:**
> my key setup is Fn + F7  to set alternative display... there should be something like that for you
When I try to get in to F7, it has the monitor being off. When I enter, say F9 or F10, all I see is the start up iniinitializing, but I do not see the log in screen. F8 has the screen as being off, too.

---

### Post by cowcow1212 on 2009-11-05
I can boot a couple of live CDs.

I have a Ubuntu 9.10 install CD (with the Try it now option), but it does NOT show any mountable drives in the /../mnt/ folder, nor does it let me mount any drives. 

And I have KNOPPIX live CD which CAN mount these drives. 

Are there any files that I could replace to make the monitor work using a GUI program with the KNOPPIX cd? (Or get the Ubuntu CD to mount the drives... and do that same task.)

---

### Post by cowcow1212 on 2009-11-05
bump

---

