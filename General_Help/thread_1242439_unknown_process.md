---
title: "unknown process"
date: 2009-08-17
forum: General Help
---

### Post by SlickRick on 2009-08-17
The system monitor is displaying an unnamed process that's not using any memory or CPU and changes it's PID at regular intervals. Occasionally, another process appears with an ID one digit less than the first one and quickly disappears again. It appears when I boot up and it's quite worrying, not knowing what it does and how it got there. Anyone have any ideas what could cause this?

---

### Post by BOBSta on 2009-08-20
I've just noticed exactly the same problem!

I've been unable to Stop, End or Kill this process via the right-click menu in System Monitor.

The Process ID is changing very quickly - initially I had process refresh set to every 3 seconds, but decreasing this to 1 sec is showing PID change every second!

Process is unnamed (Null), running as Root, Status is Sleeping, memory usage is N/A and CPU% is 0.  Process doesn't seem to show up in gnome-terminal when using:   ps -eflu root | grep " S root " | grep -v grep

System is a Dell Optiplex GX520, 2.8 GHz iP4HT, 1 GB Ram, running Ubuntu 9.04 (32 bit) in Gnome.  System is fully up to date as of this morning.

Can anyone help?  Is this a normal process, or a virus?

Rob.

---

### Post by BOBSta on 2009-08-24
Further to this issue, when I try to log out of my Gnome session, I get a pop-up dialog telling me that Unknown is not responding (see attached).

---

### Post by P4man on 2009-08-24
Odd. I found this thread:

[http://ubuntuforums.org/showthread.php?p=7743575](http://ubuntuforums.org/showthread.php?p=7743575)

For that person apparently it was related to enabling remote desktop.

I got no clue though

---

### Post by BOBSta on 2009-08-24
Thanks @P4Man - interesting reading.

After my earlier post today and before your reply, I was doing a little digging around with   **[COLOR="Red"]ps -efl -u root[/COLOR]**  and looking up things on the web, and I spotted that I had a process called "hddtemp" running:

1 S root      2858     1  0  80   0 -   519 select 09:12 ?        00:00:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sg1 /dev/sda

I killed that and uninstalled it via Synaptic.  I seem to recall installing it as part of a failed attempt to get some Dell BIOS update working under Linux.

Then I also spotted the following 3 lines:

0 S root      3117  3050  0  80   0 -   832 poll   09:12 ?        00:00:00 hald-runner
0 S root      3146  3117  0  80   0 -  1294 poll   09:12 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event4
0 S root      3182  3117  0  80   0 -  1295 poll   09:12 ?        00:00:01 hald-addon-storage: polling /dev/sr0 (every 2 sec)

Hmm, polling every 2 seconds... So, I did a little reading and there seems to be a lot of complaints about HALD using a lot of CPU.  Sure enough, both cores/threads on my CPU were consistently running at over 60%!

Issuing a  **[COLOR="Red"]kill -9 3182[/COLOR]**  to stop the hald-addon-storage, made the CPU usage drop to around 3% on each core/thread!  I then checked System Monitor and the unnamed process had disappeared!!! :)

I restarted the PC and sure enough, the unnamed process was back again :( So was the hald-addon-storage and CPU usage is back above 60%.  I killed the hald-addon-storage again, but CPU usage is still same and unnamed process is still there!

I have KDE 4.2 installed as well, so I logged out of Gnome and into KDE and the unnamed process is not running there.  CPU is still high, but this is because of Plasma.

Can anyone help further?

---

### Post by BOBSta on 2009-08-24
Doh! I forgot to test that Remote Desktop issue.  Yes, I do have Remote Desktop running under Gnome (and KDE for that matter).

I've now switched off Remote Desktop (System > Preferences > Remote Desktop > Allow other users to view your desktop = No).

Low and behold! The unnamed process has gone from System Monitor process list and the CPU usage has dropped to between 3% and 30%!  Thanks @P4man!! :)

---

### Post by P4man on 2009-08-24
vinoserver, which is used for remote desktop is so incredibly crappy :s
Its slower than cold molasses running up a hill even on a  100Mbit lan.
And now it seems to eat more cpu cycles than Quake3 - even when its not running. About time canonical ditch it for something better like xvnc or freenx.

anyway, your problem solved, but credits go to "rjlm" and google :)

---

### Post by SlickRick on 2009-08-24
> **BOBSta said:**
> I've now switched off Remote Desktop (System > Preferences > Remote Desktop > Allow other users to view your desktop = No).

+1

thx for the help :)

---

### Post by VeskoJl on 2009-08-25
I've encountered the same problem. Examining .xsession-errors led me to the same solution about RD, but i noticed that problem came up when tried to enable System->Preferences-> Startup Applications->"Remember running applications when logging out"

---

### Post by BOBSta on 2009-08-27
Thanks all! :)

---

