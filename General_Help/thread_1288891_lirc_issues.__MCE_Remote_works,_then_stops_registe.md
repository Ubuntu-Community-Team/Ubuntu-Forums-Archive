---
title: "lirc issues.  MCE Remote works, then stops registering with lirc."
date: 2009-10-11
forum: General Help
---

### Post by JedTheHead on 2009-10-11
Ubuntu 9.04
ASUS M3N motherboard
Tried two models of current MCE remotes - one is the Hauppage edition, the other model 1039.
Dedicated media center PC, only USB hardware attached is the remote receiver.  Tried two of those (each remote came with one) and the results are the same:

lirc starts and works as expected, then randomly (sometimes after 50 button pushes, sometimes after 5) the remote stops working.  The receiver LED continues to light as it is receiving response from the remote, but irw shows nothing being registered after it enters this state.  The only solution is to reboot.  This exact setup has worked without a change (other than system updates) for over two years.  No log entries or dmesg output that indicates what stopped things from working.  I will be glad to supply other information if someone can tell me where to look.

At first I thought this was an XBMC issue as it seems to stop working more quickly in XBMC, but rebooting without XBMC and just watching irw produces the same result.

Anyone else see this?

Thanks!!!!
Jed

---

### Post by shoeman22 on 2009-11-17
I've had similar problems with my MCE remote and receiver on Karmic.  I know it's a hack, but I just added a cron job to restart lirc every minute.  It's probably over kill restarting it that often, but it's worked pretty well for me.

To add the cron job:
```
sudo crontab -e
```
then in the cron editor, add this line
```
* * * * * /etc/init.d/lirc restart
```
then save and exit (ESC then SHIFT+ZZ if you're in vi)

---

### Post by GoofYas007 on 2010-04-03
Also posted in a similar thread...

 Re: MCE Remote Randomly Stops Working and a strange USB drive issue

I also posted this in the bugs section:

I solved my problem by buying a new main-board. (with AMD chip-set)
Strangely enough I only had this problem on a NVIDIA chip-set.

For what it's worth my experience is (2 mb's with NVIDIA chip-sets) that it's due to the NVIDIA thing.

I can now again use the remote continuously without fear of it stopping randomly after a couple of key presses...

---

### Post by Lepy on 2010-04-20
Same problem on NVIDIA based chipset (ASRock K10N78) under 9.10 and 10.04. Nothing shows up in logs except in dmesg, which always spits out multiple complaints after the device stop responding like: 
INFO: task *whatevertask* blocked for more than 120 seconds. These errors also show up on another board (Asus P5k Deluxe) but not sure if they cause usb devices to stop functioning.

IR receiver will blink, but nothing registers when running irw. Restarting lirc service does not fix this, only a reboot. The device usually works for long periods of time (can last for a few days) but seems to stop randomly. 

I think this is definitely a usb issue as other devices (usb HDD and usb printer) also stop responding (won't mount or CUPs will not forward jobs). lsusb hangs as well.

---

### Post by Arnoud30 on 2010-05-07
I had the same problem but found a fix for my system.
 
Hauppauge MCE2 remote. ASUS M3N NVIDIA motherboard, mythbuntu 9.04, mythtv 0.22 fixes. 
No messages in Dmesg and only able to recover remote after reboot.
 
In the beginning the remote was working without problems, but got worse and worse.
Particularry when enabling IR transmissions it would fail within minutes.
I saw mentioned in some other forum that the lirc_mce driver could not restart the usb, so was wondering if the mce itself had a problem.
After some experimenting I (finally) managed to find a solution. This is fully stable. Never had a single problem afterwards.
 
What I did:
1) Replaced the orignal long thin USB cable by a short thick cable. The thick ones have normally better shielding and thicker conductors.

2) Opened the MCE housing, and soldered a 100uf capacitor (in my case a tantalium, but any cap will do) between the +5v and ground of the USB 
interface connector. Watch the polarity of the cap.
 
I did both changes at the same time, so don't know you will need both changes to fix the problem.
 
Success.

---

