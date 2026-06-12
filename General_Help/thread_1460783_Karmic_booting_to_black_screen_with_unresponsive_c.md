---
title: "Karmic booting to black screen with unresponsive cursor flashing"
date: 2010-04-23
forum: General Help
---

### Post by carn1x on 2010-04-23
As the topic says. I'm having problem after problem, everytime I figure out a way to take a step forward, my PC has pre-emptively taken a step back.

I'm unable to boot to X or (recovery mode).

I did try booting to a LiveUSB in order to run update-grub, but then it occured I have no idea how to do this from a LiveUSB that will affect the internal HDD installation?

So I'm currently trying to reboot from Live USB, but that just seems to have locked up the PC on the white ubuntu logo. I'm afraid to hard reset it (been doing too much of that lately). How long should a Live USB take to shutdown? (been about 10 minutes so far :|). It's not a persistent LiveUSB as far as I know, and I basically just booted to the desktop and then start the reboot cycle as soon as I realised I didn't know what I wanted to do :S

Someone please help me, I'm starting to miss Windows!

EDIT: Just realised I'm really not posting much useful info, but I guess I don't know where to start. Is there some useful readout I can use to help anyone diagnose my issues?

Thanks

---

### Post by carn1x on 2010-04-23
OK here's the last lines output from trying to boot to recovery mode:

> 
fsck from util-linux-ng 2.16
/dev/sda5: Superblock last mount time is in the future. (by less than a day, proably due to bad system clock last boot) FIXED.
<!--above line repeated-->
/dev/sda5: clean, 177585/960992 files, 1184882/3839527 blocks


After this there's a white flashing cursor on a newline. It accepts keyboard input, but doesn't appear to react. Ctrl Alt Del does reboot however. 

Ctrl Alt F2-5 go to a full black screen with white cursor, yet there appears to be no keyboard response. Ctrl Alt F1 brings back to the original screen with boot readout.

Any ideas?

Thanks for any help!

---

### Post by carn1x on 2010-04-23
Just tried booting with an external drive attached, as I usually do. Read somewhere this can influence things sometimes. This hasn't made any difference. The superblock error is now gone, I'm guessing it's a result of hard resetting from the botched Live USB shutdown.

Still stuck at the same point :(

---

### Post by carn1x on 2010-04-23
Ok thought I'd try invoking the 10 mount fsck check and it then announces after the same as every other failed boot:

> 
Filesystem checks are in progress (ESC to Cancel):
/dev/sda5 xxx/xxx fiels (0.2% non-contiguous), xxx/xxx blocks
init: ureadahead-other main process (1860) terminated with status 4


and once again stops dead at a white cursor that accepts keyboard input, but does nothing with it except CTRL ALT F1-6 / CTRL ALT DEL. If a reinstall is my only hope then I guess I'll resort to it, however I decided to go to linux to learn, and reinstalling feels a bit like running away from my problems!

Thanks again for any help with this

---

### Post by carn1x on 2010-04-23
Not sure if this is relevant in the slightest, but the memtest86 completes a pass with no errors, and windows 7 still boots fine from the GRUB menu. I'm 99% sure none of this affects my problem, but I'm desperate to see something work on this PC!

One thing I'm wondering is, is my booting up actually stalling somewhere? Or is the line of text that it's spitting out the last line of text that should be expected?

---

### Post by carn1x on 2010-04-23
I have been making the /dev/sda5 change everytime in the Grub Menu Edit as it's been failing using UUID. 

In fact, the problem of this thread started just in time to prevent me running update-grub. 

I decided I couldn't be bothered any more with the GRUB edit, and let it run using UUID but it still only boots to the same point. Not sure if this is useful info? Also, the last time I booted successfully I installed the package build-essential as I read I would need it for installing downloaded nvidia drivers, could this be screwing things up?

---

### Post by carn1x on 2010-04-23
Well, I've gone to bed and woken up, nobody has any ideas, I guess I'll give in and reinstall ;_;. Thanks to anyone who tried to think of something!

---

### Post by klemes on 2010-04-24
I am so sorry no one stepped in for any advice but I am also afraid from what you describe this is not a so easy problem to solve especially from distance....
On your problem now and granted that you still want to experiment a little on this and that you have not reinstalled already,which is I think the most proper outcome of this endeavour....;) here is a link to a useful post regarding your situation:
[http://ubuntuforums.org/showpost.php?p=9159924&postcount=10](http://ubuntuforums.org/showpost.php?p=9159924&postcount=10)
Copy & Paste this script into a terminal after having booted from a Live CD or USB and post the results here
in order for someone being perhaps able to help you based on the above.
Also in the last 2 or three days there were numerous threads in this forum about Karmic not fully booting or freezing so I suggest reading those in order to gain more knowledge about the nature of your problem .
From what I understand it is not a grub problem but your system gets stuck just after the system file- checking routine during boot.Maybe perform a search with the above criteria and see what you get.

---

### Post by carn1x on 2010-04-24
Oooooooooooh I just got back to my desktop from a clean install! Still, I'm sure it won't be long before I screw things up again, so thanks for the soon to be useful advice :)

---

