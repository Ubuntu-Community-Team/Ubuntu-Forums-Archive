---
title: "Hibernate Mode"
date: 2010-01-15
forum: General Help
---

### Post by eipapp on 2010-01-15
Running Ubuntu 9.1. Have 512 Mb of Ram and have allocated 2Gb for swap partition. I am running Win XP on same machine. Cannot get computer to go into hibernate mode while in Linux. When I click on Hibernate the computer begins going into hibernate but then just as quickly comes back up to normal running mode.
Can anyone help ?

---

### Post by john newbuntu on 2010-01-15
What are your outputs after running the following in a console?
```
cat /sys/power/disk
cat  /sys/power/state
cat /sys/power/pm_test

```

---

### Post by eipapp on 2010-01-15
after disk:
"(platform) test testproc shutdown reboot"

after state:
"standby mem disk" 

after pm-test:
"(none) core processor platform devices freezer"

---

### Post by john newbuntu on 2010-01-15
Make the following change and then try hibernate
```
sudo echo shutdown > /sys/power/disk
sudo echo disk > /sys/power/state
```

---

### Post by eipapp on 2010-01-15
Tried this but after first line (/sys/power/disk) got the message "Permission Denied"

Do you have a work around ???

Thanks,

---

### Post by hashky on 2010-01-15
I have the same problem.  So I tried to change the permissions so that the commands would run.  I can change the permissions to allow read/write for the owner but the permissions do not stay.

And, I cannot change the files either.  

Any suggestions?

hashky

---

### Post by john newbuntu on 2010-01-17
Ok do this:
sudo su
and then type the commands I gave you.

---

### Post by eipapp on 2010-01-17
Sorry but that didn't work either. 
After typing the first line you gave me I get the following:

bash: /sys/power/disk: Permission Denied

I checked and I am checked as "Administrator the system", for what it's worth.

---

### Post by drewsus on 2010-01-17
out of curiousity, might you have an SD card in your computer?

---

### Post by eipapp on 2010-01-17
No, I do not.

---

### Post by drewsus on 2010-01-17
kk, I just had this problem before and it was for that reason

---

### Post by hashky on 2010-01-25
I found out that to get the commands to work you have to type
Sudo -s

Enter your password and then you have root permissions. The commands will now work.

This did not work for me.

My question.  How do I revert back?

cat /sys/power/disk is the same as before.
[platform] test testproc shutdown reboot

cat /sys/power/state changed.
mem disk

How do I get standby back in before mem disk?

---

### Post by hashky on 2010-02-28
An update:

Ubuntu 9.10 on Dell Inspiron 1501 laptop. 
I finally got Suspend to work.  Sometimes the brightness has to be adjusted on return from the Suspend Mode.  Hibernate does not work.

Ubuntu 9.10 on Dell 4400 desktop.  Neither Suspend or Hibernate work after install or on Live CD.  Suspend and Hibernate both work under Ubuntu 9.04 and LinuxMint 8.  When I install Samba on Ubuntu 9.04, Suspend and Hibernate no longer work.

Ubuntu 9.10 on Asus Pentium 4 home built desktop system.  Suspend and Hibernate both lock up the computer and the hard drive is continuously busy.  (That can't be good for the hard drive.)  I plan to install Ubuntu 9.04 on this computer next week.   

All 3 computers are in a dual boot arrangement with Windows XP.

Ron Spruell

---

