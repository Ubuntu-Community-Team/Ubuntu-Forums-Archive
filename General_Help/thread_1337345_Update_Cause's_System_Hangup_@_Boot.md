---
title: "Update Cause's System Hangup @ Boot"
date: 2009-11-25
forum: General Help
---

### Post by juicehill on 2009-11-25
Just installed new updates this morning, I was asked to restart to complete install.

Upon restart, grub had a new option to boot to, .15 kernal thingy above the original .14.

When trying either of these my system hangs at the first splash screen before the brown loading screen.  HELP!  >: :(

---

### Post by philipp2084 on 2009-11-25
Did you do a dist-upgrade? i.e. upgraded the kernel at the same time? 

See if you can start single user mode (recovery mode).

---

### Post by kammce on 2009-11-25
I think I used to have this issue. I might have a fix to this. Answer these questions and I will see what I can do.

1) Does your computer Hangup after the Gnomes progress bar screen or before that?
2) Try this: Press "esc" at the GRUB boot up screen so you can view the kernels that you can boot from. Wait 10 seconds then select the latest one. See if that helps.

---

### Post by juicehill on 2009-11-25
@ philip:  I'm not sure how to awnser your first question, I installed these updates as recomended by the update manager, and i did not take note of what i was particularly installing, I admit i was very hasty and lacking care at the time.  

I did uncheck an item for installation for reasons now i'm not sure why, and had a another software source polling information (not sure if it did actually apply any updates [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) sid main)

I cannot boot into recovery mode, i get simular system hang-ups.  .14 hung up once when searching for /root file system - and .15 after checking the usb devices.

@ kammce:  Hang up before Gnome Progress bar (hangs @ white ubuntu logo) -- And I automatically boot to grub since i have a windows xp partition install -- and i've tried all options besides the memtests :p )

---

### Post by kammce on 2009-11-25
What version of Ubuntu do you have? 
Also try pressing "Ctrl + Alt + Delete" to bypass any hangups when you try to boot to recovery mode. Although doing this is sorta dangerous if you are bypassing the part in the boot were the the computer is trying to search for the "/root" filesystem.

---

### Post by juicehill on 2009-11-25
The latest 9.10 - fully updated and running ati ccc

---

### Post by kammce on 2009-11-25
I am so happy I didn't upgrade to 9.10. I have heard so much crap from that version of ubuntu. If I were you, I would downgrade to 8.04 (Most stable) or 9.04.  But thats just me...... 

Can you tell me what happens exactly when you boot from Kernel 2.6.---.15, 2.6.---.14, .15 (recovery mode), and .14 (recovery mode).

---

### Post by juicehill on 2009-11-25
Pretty much what i've said is what i see so far, unless you have a method with which i can log information to locate a possible useful error message, or something along that line.

It seems i've found myself in albiet of a jam here, 9.10 has been running very stable untill now, only thing i really missed was the option to choose the login sound.. lol :/ wow huh

I made a new install in another partition so i could access my ext4 files in the bad install and backup anything i wanted, so i might just install over both soon with 8.04 or a clean 9.10.  But i will wait to troubleshoot a little more.   And I would like to figure out how to avoid this problem in the future on a clean install..  I would like to be able to keep my system fully updated, ocd <---

---

### Post by juicehill on 2009-12-04
Although I did not recover the complete 9.10 installation, I am now using 9.10 again with everything updated besides the kernal .15 updates.  Running stable as before.

Would make a general recommendation to people to make sure not to update this kernal on new installations.

In update manager an easy way to avoid them seems to be to go to the Update tab and deselect "Recommended (Karmic-Updates)" while leaving Security Updates checked. 
The only single update that still shows kernal in description is..

linux-libc-dev
"Linux Kernal Headers for developement"

I have not installed it yet, should I be avoiding it aswell?

I'll put solved since i'm just avoiding the problem atm.

---

