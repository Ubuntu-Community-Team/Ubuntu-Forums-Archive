---
title: "lucid power manager not reponding, log out anyway???"
date: 2010-06-22
forum: General Help
---

### Post by sdowney717 on 2010-06-22
every time this boots now, I get that message. If I hit cancel, then the screen locks and the mouse moves but nothing happens.
The only way to get it show the desktop, is to select 'logout anyway'

Plus the boot takes forever at least 4 times longer than karmic.

all of this is in reference to booting up the PC

---

### Post by sdowney717 on 2010-06-22
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862)

at least it affects all these people.

---

### Post by james_fried on 2010-07-07
Hi Sid,

This bug is effecting me - but HARDER than what I've seen other people writing about.

After the "power manager not responding" message:
[LIST]
[*]gnome boots and then freezes (I think that a start-up script is breaking something)
[*]sudo hangs in ALL terminals (alt+ctrl+f2, etc - I can't get a terminal to run in gnome)
[/LIST]

Right now I'm grabbing a startup lucid disk in the hope that I can use it to get sudo back and fix it. Unfortunately, I'm also suffering from the "Bootup/Plymouth" bug.

I've chosen the crying smiley to represent how I feel about this issue.

J

ps. Thanks for reading this - I'm continuing to hack the machine, but with a plastic sheet over my kbd to prevent my salty tears ruining it.

---

### Post by warfacegod on 2010-07-07
Try using Bootup Manager to disable the Power Manager from starting.

```
sudo apt-get install bum
```

I've used it to disable things like bluetooth and got a major improvement in boot speed and in "session" peppiness.

The Startup Applications app found in system> Prefs. does a good job of making sure things start but not so much when you want to *prevent* them from starting.

---

### Post by james_fried on 2010-07-07
Hi warface,

Thanks for the info - I'll try out the bootup manager if I can get sudo to work at all.

I've grabbed a live CD but when it kicks into gnome it also crashes in the same way as my currently installed lucid! Reading this comment [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862/comments/41](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862/comments/41) suggested resetting the CMOS which I've also done, but with no avail.

I'm going to keep trying - maybe some different boot methods will let me get sudo.

J

---

### Post by warfacegod on 2010-07-07
It's also available in Synaptic.

---

### Post by james_fried on 2010-07-07
cheers warface,

I managed to get the machine to boot into gnome again and give me sudo back.

From the logs, I found that the network manager was crashing at boot, both on my install and the live CD. Pulling out the wireless network card and rebooting got the machine working again - the power manager popup gone, sudo working again.

Then I just shutdown, put it back in, and it's back to normal on boot again. Fingers crossed it stays that way.

Thanks for the help,

J

---

### Post by marktheimmortal on 2010-07-18
I had the power manager problem also.

For me though it was a different issue to you and thus a different resolution.

I went through the 'dmesg' output to discover that the integrated webcam (orbicam) on my acer laptop (acer aspire 5680) was playing up. It hasn't worked for years anyway but seems to be causing some problems for Ubuntu (Karmic & Lucid) lately.

The messages output by dmesg were about gspca and vc032x.

To fix that problem (both karmic/lucid):
sudo gedit /etc/modprobe.d/blacklist
add the line "blacklist gspca_vc032x"
reboot

Incidently..... It manifested in lucid as a power manager problem and a  slow boot/login. In karmic there was no power manager dialog just a slow  boot/login time.

Hope that helps anyway who has this specific problem.


Regards,

Mark

---

### Post by martinnut on 2010-09-02
@marktheimmortal

Many thanks for posting this, your fix solved my issue too - I have an Acer 5630 with dodgy camera and this was driving me nuts! Lucid now boots super quick :)

I get a similar problem with CloneZilla, seems it gets a USB -22 error and never loads, have to figure out how to do a blacklist on the grub now :)

Thanks again!

Howard

---

### Post by Golder on 2010-09-17
I have no webcam plugged in, nothing byt my mouse and my keyboard, no cd  in the cd drive and I have *incredible* problems to get the computer to  even boot, even with the failsafex, it works 1/10 of the time. It is  extremely stressing. I've managed to make failsafex work this time, I'm  saving up datas and coming back to XP for the time being :(
I'm using Lucid Lynx, with a 2.53GHz intel core duo, 4GHz ram, intel  5350 with 1Gb and a 1Tb hard drive. I have absolutely no idea what to do  beside going back to windows until this is fixed

---

### Post by sdowney717 on 2010-09-20
old thread, my problem went away after some updates.

You can look at dmesg output for errors
and 
in /var/log dir, look at xorg.0.log file for errors
Might give some clues as to what is going on

---

