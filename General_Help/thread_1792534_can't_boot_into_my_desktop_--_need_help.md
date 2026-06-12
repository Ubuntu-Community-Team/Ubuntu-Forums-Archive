---
title: "can't boot into my desktop -- need help"
date: 2011-06-28
forum: General Help
---

### Post by maizuddin35 on 2011-06-28
Hello guys , everyone!

This morning , my country time, I was doing update and upgrade , and i stumble upon some few problem, while apt-get upgrade.

I think , you should refer here, 
[http://ubuntuforums.org/showthread.php?t=1792084](http://ubuntuforums.org/showthread.php?t=1792084)
this is my earlier(this morning) thread about my problem ... and it solved , well, not until I reboot the computer...

Now , when I'm at the grub loader , there is only three option .that is..
1)the **recovery mode** for **linux-image-2.6.35-28-generic_2.6.35-28**
2)the **recovery mode** for [B]linux-image-2.6.35-30-generic_2.6.35-30
[/B]3)windows 7

what should I do now...please help

your help is greatly apreaciated.:(

---

### Post by An Sanct on 2011-06-28
Hey!

I also updated to the new kernel today, no problems here ...

Did you try to start into recovery mode and update broken packages? [more at this link]("http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/").

---

### Post by maizuddin35 on 2011-06-28
I try using the recovery mode, and use the "repair broken packages" but then I need internet connection to use that, I don't have direct cable internet, I'm using my college wifi connection

---

### Post by An Sanct on 2011-06-29
If you log into "terminal with networking" (I don't remember the exact phrase) then networking-internet will be enabled and the settings from your desktop configuration will be used.

You can have problems if the wifi is not DHCP enabled (requires manual IP setting)

---

### Post by maizuddin35 on 2011-06-29
please check on this new thread problem ---> [http://ubuntuforums.org/showthread.php?t=1793089](http://ubuntuforums.org/showthread.php?t=1793089)

and, if I log into the "terminal with networking" how can I access the wifi connection via the terminal ?

---

