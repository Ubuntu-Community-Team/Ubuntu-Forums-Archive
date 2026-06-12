---
title: "Ubuntu Will Not Load."
date: 2011-11-15
forum: General Help
---

### Post by JoshuaMiller0 on 2011-11-15
Hi,
 
I have been running perfectly well on 11.10 with no problems. I have not recently downloaded anything that is likely to be a virus.

The last few programs installed were:
[LIST]
[*]Hibernate
[*]Kate (Text Editor)
[*]qshutdown
[*]A failure at installing TeamSpeak3
[/LIST]Last night, I was uploading a video to YouTube and it was getting late. I told my Dad not to turn off the modem or anything else to do with the internet. I left my laptop turned on (low power settings - low brightness) and plugged in. I opened qshutdown and set it to shut down the computer in 3 hours - when the video should be done.
 
I woke up in the morning and checked my laptop, it was off but the flashing light indicated it was plugged in and recieving power. I did not turn the computer on until later. When I turned the computer on I left it booting up. I came back about 20 minutes later to find it was still booting. It had made it to the purple Ubuntu screen with the lights turning on and off. (the four dots beloq the Ubuntu text.) My computer usually only takes about 26 seconds to boot with Ubuntu.

I could not think what to do next so I pulled out the power cord and tried again (my laptop's battery does not work so this turns off the power). This time the exact same thing happened and I pulled out the cord after 60 seconds.
 
The next time I tried to boot the computer, I chose to boot it in "recovery mode" this time as it was booting with pages of script it stopped at the end and said "fixed recursive fault, but reboot is needed!" I was unable to reboot the computer properly so I held the power button down until it turned off (The button suddenly cuts the power after ten seconds of holding it down.)
 
The next time I booted the computer (in recovery mode) it stopped the pages of script and said the following:
(I skipped some of the successful "Begin:" lines before the following)

```
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin Running /scripts/local-premount ... resume: libgcrypt version: 1.5.0
resume: Could not stat the resume device file '/dev/dm-0'
Please type in the full path name to try again or press ENTER to boot the system:
```
 
Pressing Enter did not work. There was no cursor/ random flashing underscore. I could not type and nothing happened whatsoever.
 
I then pressed enter and left my computer for 30 minutes and came back. I came back to find there WAS a cursor/ random but I still oculd not type and enter would not work.

---

### Post by Evil_Cid on 2011-11-16
Had the same problem two minutes ago...I just restarted it and it said "resume: libgcrypt version-1.5.0"
I had the same problem a while ago when I had Ubuntu 11.10 installed on a partition on my second hard drive (GRUB was installed on my primary/main hard drive..) I've since installed Ubuntu 11.10 on a hard drive on its own and hoped the problem would go away...and now its back :(

---

### Post by JoshuaMiller0 on 2011-11-16
> **Evil_Cid said:**
> Had the same problem two minutes ago...I just restarted it and it said "resume: libgcrypt version-1.5.0"
I had the same problem a while ago when I had Ubuntu 11.10 installed on a partition on my second hard drive (GRUB was installed on my primary/main hard drive..) I've since installed Ubuntu 11.10 on a hard drive on its own and hoped the problem would go away...and now its back :(
 
Do you remember installing any specific programs before this error? More specifically, do you have **_ANY_** of the above programs installed?

---

### Post by JoshuaMiller0 on 2011-11-17
I think I found a solution! When you go to start up, select the "Other Linux Versions" button and then chose the second "recovery mode" option down. This should load properly.
 
For me I went into synaptic package manager (ubuntu software centre should do...) and uninstalled all my recently installed programs. I then restarted and loaded up Ubuntu normally and it worked fine!!!

---

### Post by Evil_Cid on 2011-11-18
> **JoshuaMiller0 said:**
> Do you remember installing any specific programs before this error? More specifically, do you have **_ANY_** of the above programs installed?

Now that you mention it, I did indeed install one of the packages you've stated in your list above. It was the hibernation package. I had installed it due to the fact that hibernation (for some reason) did not work on my PC in the first place. Now I can't remember what the package was called :(

On the other hand, I removed the boot-flag from one of my hard-drives and so far so good.

---

