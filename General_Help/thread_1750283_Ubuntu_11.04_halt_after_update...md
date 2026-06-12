---
title: "Ubuntu 11.04 halt after update.."
date: 2011-05-05
forum: General Help
---

### Post by xtro7 on 2011-05-05
Hi, I'm kind of noob in Linux, so, I installed Ubuntu 11.04 in my laptop (HP TM2 touchsmart) and everything was great, install perfect, it recognize every driver, but then it said that there was updates availables, so I installed them, but after that, the system halt at restart, nothing, just a black screen, and if I enter in recovery mode It stops in the line "registering wacom driver" :(
So, what can I do in that case..? Can I restore the previus drivers..? Do I need to reinstall..? How do I avoid that it may happen again..??

Thanks in advance for all your answers.

---

### Post by dino99 on 2011-05-05
reboot in recovery mode and select "repair package"

---

### Post by xtro7 on 2011-05-05
Hi, Thx for such a quick answer.
In recovery mode it freeze when gets to the wacom line, where can I find "repair package"..??

---

### Post by BernieB on 2011-05-08
Hello

I also have a HP TM2. The Problems are the two Graphic-Cards. I switched back to 10.10.

When i boot up 11.04 the radeon-driver gets "stuck". The funny thing is, sometimes it works, mostly it does not. Seems completley random.

One solution is to blacklist the radeon driver. But then i can not turn off the radeon-chip, because vgawitcheroo ist not available anymore. So the radeon-chip runs hot.

The other big problem is, that kernel 2.6.38 has problems with the first intel i915-graphic-card. the vga-out does not work at all. my external screen remains black, when i switch screen-modes, aswell as the primary laptop-screen. but this will be fixed in 2.6.39.

HP TM2 was always a pain, because HP does not allow to disable the radeon-card within the bios. But with 11.04 came these new problems...

I for one skip 11.04 and wait until intel / amd fix these problems.

I know this won't help you with the problems...

---

### Post by matey3 on 2011-05-08
Thanks for the info. Last year I did the auto update (in 10.4, GUI) for the 3rd or 4th time but it crashed my system where Nothing would fix it, I lost all my files and had to do reinstall!
( I could never find a solution and so had to re fdisk and all)?
I hope if this is an ongoing problem that the good people would report it so we know and won't update via update mgr,(or turn off the auto update)!

Doing sudo apt-get update in terminal doesnt crash the system tho?

---

### Post by xtro7 on 2011-05-08
Unfortunately, seems like everyone els its having problems with the TM2 and 11.04, just like BernieB said there is a problem with the ATI Driver, some recommend vgaswitcheroo , but others say that after that vgaswitcheroo start to give problems too.. :S

Im following what [SMOLOVIK]("http://vlad.smolovik.com/en/blog/84-linux/64-hp-tm2-ubuntu-11-04.html") have to said about it, seems like the guy knows a lot about it.. :D

In the meantime, Im installing windows 7 again... :(

---

### Post by at78rpm on 2011-05-08
I too can't get into 11.04 now.  Everything was going okay for three days, then today odd things like drag bars disappearing so I restarted and it told me that there was no /tmp so it wouldn't boot.  

I'm done with experimenting.  As I type this, I'm downloading 10.10.  It worked fine.  This 11.04 is a disaster.

---

### Post by shelbydz on 2011-05-08
So does reinstalling 11.4 from a disk (rather than the auto-update) fix this issue? 

I have the same problem. Worked great for me on my laptop with an Nvidia (with optimus, ugh). I 'halted' from the menu and now I can't get back into Ubuntu. 

Frustrating. 

thx

---

### Post by bijanbina on 2011-05-10
hi i have the same problem its very bad for ubuntu how can we send this bug for theme?

---

### Post by vedovatti on 2011-05-17
Hi there! I have the tm2 with ubuntu 10.10

I haven't tried yet the 11.04 but how you describe it sounds like the same problem I had with 10.10 and 10.04. When you install the distribution it will offer to install the property driver for the ATI. For you own sake NEVER install property drivers in an hybrid graphic card. They are not supported and you will never see your screen (at least it what happened to me with 10.10) and to be honest they are badly supported in windows too (I used it for games and the ATI hybrid driver have many bugs). Just use the default drivers, switch off the ATI card (it will save you a lot of battery) and just use it when is necessary (to play games or to use the HDMI video out).

I hope some day the hardware producer decent driver for their products.

PD. I you want the basic synaptic working on the tm2 install the dkms-synactic package it worked for me, gives you basic two fingers multitouch

---

### Post by android272 on 2011-05-29
so I just installed unity and saw this.  is there nothing that we can do. we cant just go without updateing our systems.  has this problem been fixed or not.

---

### Post by vedovatti on 2011-06-04
OK guys I found the issue and solved the problem. I have HP touchsmart tm2-2105eg with Ubuntu 11.04 64-bit working well (with a few workaround).

I have being experimenting with the new Ubuntu and in fact after updating it freezes randomly. In the beginning I though it was the hybrid graphic card. The problem is the wifi card Broadcom 4313 that has. The new Ubuntu 11.04 comes with an open source driver called bcm80211 (or similar..). So the problem with the driver is that when the wifi is off, it freezes the whole system and if you boot the Ubuntu and the wifi is off it doesn't let it start.

SOLUTION: boot the system with the wifi on. Then open the program additional drivers and activate the property driver. It doesn't work if you install the package with synaptics . It just worked activating through the additional drivers. The open source driver has many bugs and doesnt work with ad-hoc and freezes when the wireless connection is interrupted, and others, so just use the property.

The other issue with the graphic card I managed to turn the discrete card off and save 40% of the battery and turn it on when shutting down the system so it shuts down it does it fast (if the card is off it takes like 20 seconds...)

So the solution is this:
```
sudo gedit /etc/rc.local
```
Add:
> modprobe radeon
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
exit 0
This will turn off the card and your battery will last 6 hours.
Now to turn on the graphic card before shutting down From terminal run
```
sudo gedit /etc/init.d/DisOn
```
Put the following text into that file:
> #!/bin/sh 

echo ON > /sys/kernel/debug/vgaswitcheroo/switch

exit 0
Save and exit.

Back in the terminal, do
```
sudo chmod +x /etc/init.d/DisOn 
sudo ln -s /etc/init.d/DisOn /etc/rc0.d/K10DisOn
sudo ln -s /etc/init.d/DisOn /etc/rc6.d/K10DisOn
```
And the system will be stable. Now the problem with the clickpad (touchpad) you can check the solution on: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/207](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/207)
It works ok, except for the problem I pointed on the next comment.

Hope that helps. I like the new Unity is really good for netbooks!

---

