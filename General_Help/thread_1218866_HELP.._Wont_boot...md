---
title: "HELP.. Wont boot.."
date: 2009-07-21
forum: General Help
---

### Post by juliankossmann on 2009-07-21
hello

this post will be a little long...

a few weeks ago my Asus EeePC 900 (Eeebuntu intrepid) began not resuming from some suspend modes, which I use often. I would then have to hit and hold the button, and restart manually. I took note of the problem, and noticed a pattern (Suspend on DC, will not wake up on AC power) but took no immediate action.

Yesterday, I made the mistake of suspending on DC and then attempting to resume on AC, and as usual it gave me a blank screen, however when I restarted it proceeded to run an FSCK during the boot and then instead of loading up my login screen, said that there was an inconsistency and I sould run FSCK manually. So I did. 

About 20 errors came up and I just said fix to them all, when I was done it said FILESYSTEM MODIFIED or something and REBOOT. So I rebooted. During the Grub loading stage 1.5 it hung on Grub Error: 17... :o

Then I tried booting on DC power and it worked fine... So I quickly backed up everything to my EXT HDD and shut down my computer. About a half an hour later I tried booting on DC and on AC and it got stuck on Grub Error: 25 .... :o no FSCK, nothing. Just Asus EeePC BIOS Splash Screen and Error: 25.

Is there any way of fixing this that doesnt involve formatting and reinstalling ubuntu.. 

Any help would be greatly appreciated,
I'm kinda stuck in a black hole here...

---

### Post by bjdodo on 2009-07-21
Hi

Try what is suggested in this thread:

[http://ubuntuforums.org/showthread.php?t=117271&highlight=grub+error+25](http://ubuntuforums.org/showthread.php?t=117271&highlight=grub+error+25)

Jozsi

---

