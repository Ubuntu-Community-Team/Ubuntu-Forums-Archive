---
title: "Improper Shutdowns"
date: 2010-05-08
forum: General Help
---

### Post by arpan251089 on 2010-05-08
This has been a problem for me since while. Whenever my PC shutdowns improperly, i'm not able to boot the OS which runs when the PC shutdown.

I have Ubuntu 9.04 and windows XP.

In windows XP whenever this happens I get the safemode screen and then selecting any option leads to some process which ultimately reboots the PC.

In Ubuntu the splash starts it shows 10% disk scan and then a console starts which display some errors and starts the maintenance shell. I don't know what to do in that shell so i exit and then i get a blue screen with a dialog(console) which says Unable to start X Server (your graphical environment) due to some internal error. It says something more about GDM(I don't remember).

NOTE: Though one of the OS doesn't start the other one works fine. So i guess this is not a hardware problem. maybe the partition in which the OS resides gets corrupted. But this never happened before. I have shutdown my computer improperly so many times.

I used fsck for ubuntu but nothing useful happened except the diskchecking stopped when splash comes up. but still ends with that X server error.

Pls help

---

### Post by arpan251089 on 2010-05-08
Well fsck prints this while running

[176.030600] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0.8%
[176.030661] irq_stat 0x40000008
"          " cmd ....
Emask (media error) <F>

status: {DRDY ERR}
error: {UNC}

/dev/sda3 : UNEXPECTED INCONSISTENCY; RUN fsck manually

fsck died with exit status 4

---

### Post by sandyd on 2010-05-08
> **arpan251089 said:**
> Well fsck prints this while running

[176.030600] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0.8%
[176.030661] irq_stat 0x40000008
"          " cmd ....
Emask (media error) <F>

status: {DRDY ERR}
error: {UNC}

/dev/sda3 : UNEXPECTED INCONSISTENCY; RUN fsck manually

fsck died with exit status 4
boot up from your ubuntu livecd.

Go to applications -> accessories -> terminal

```

fdisk -l
```

that will show your partition info.

you will get something like```

**/dev/sda1   *           1       52948   425303786   83  Linux**
/dev/sda2           59360       60801    11582865    5  Extended
/dev/sda5           59360       60801    11582833+  82  Linux swap / Solaris


```

on the first line, you can see that the line ends with "linux"

you should have a line like that as well (it might not be the first though)

you will need the first column of that line. (in my case it is /dev/sda1, so I will refer to it as /dev/sda1 throughout this post. just replace it with your own).

```

sudo fsck -y /dev/sda1
```

take a nap while your waiting

---

### Post by arpan251089 on 2010-05-08
this is what i did

fsck -y dev/sda3 coz mine is sda3

and the text in my second post is what was printed when i run the above cmd.. the process does takes place but with this text printed at regular interval

---

### Post by sandyd on 2010-05-09
hmm...

it should not be the same as the second post, because your now running fsck manually...

---

### Post by dino99 on 2010-05-09
you can check your hdd and partitions with theses tools:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)
[http://partedmagic.com/](http://partedmagic.com/)

you can check your bios settings too and maybe update it

---

### Post by arpan251089 on 2010-05-10
> **carlee said:**
> 
it should not be the same as the second post, because your now running fsck manually...

don't count the last two lines they were printed while fsck was scanning automatically. but the upper lines are printed even when i manually do fsck.

Now some how i managed to start ubuntu(after a successful manual fsck).. but when the login screen should come i got a gdm warning that "my home directory doesn't have the read permission (or something like that...) and i can't login"


> **dino99 said:**
> you can check your hdd and partitions with theses tools:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)
[http://partedmagic.com/](http://partedmagic.com/)

you can check your bios settings too and maybe update it

i have partedmagic. can you explain me how to use it. using it will not effect my windows??

and how to update bios?? how will it help??

---

### Post by RemmyNumber7 on 2010-05-14
Carlee thanks i will try that but i have originally have Ubuntu 8.08 and upgraded to 8.10 will that still work?

---

### Post by arpan251089 on 2010-05-21
Well can anyone tell me whats the difference between a hard disk access for normal booting and the hard disk access for disk checking for errors if there is any... cause i think all these errors occur when my hard disk is checked for errors (due to improper shutdown)... so if thats the culprit i can switch off disk checking  due to improper shutdown... and may even trace the problem...

---

