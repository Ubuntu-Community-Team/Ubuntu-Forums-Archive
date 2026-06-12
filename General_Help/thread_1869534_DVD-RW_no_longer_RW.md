---
title: "DVD-RW no longer RW"
date: 2011-10-25
forum: General Help
---

### Post by K_bo on 2011-10-25
This could be something very, very simple :) 

I have a DVD-RAM 4.7gb that I used to use for watching movies on my DVD player from my computer.  I used it as a RW for a long time.  Later I used it to simply transfer files and have formated it a few times.

The problem now is for some how it is coming up as a READ-ONLY and wont let me format anymore.  In Windows it doesn't even give me the option for format and in Ubuntu, I get this error message when I try to reformat: 
Error creating file system: helper exited with exit code 1: 2861: error writing 131072 bytes: Success
Error calling fsync(2) on /dev/sr0: Input/output errorv

and of course I cant just delete the file off the disk either.  

How do I get the wite protect off so I can use my disk again

Any ideas??

---

### Post by garvinrick4 on 2011-10-25
Try installing xfburn and using that to format or erase with read write disks.
```
sudo apt-get install xfburn
```

---

### Post by duke.tim on 2011-10-25
[s]RW disc's over many burns, will eventually become unreadable. Depending on the brand they can be recommended from anywhere between 5 to 100 writes.[/s]

oops! DVD-RAM
Can be rewritten over 100,000

---

### Post by K_bo on 2011-10-25
I installed Xfburn and with the cd in i started the app and got this messege:

[CENTER][IMG]http://i329.photobucket.com/albums/l380/bayshine/noburnersavail.png[/IMG][/CENTER]

In window i try to take off the read only option under properties and I get his messege:

[CENTER][IMG]http://i329.photobucket.com/albums/l380/bayshine/errormessage.png[/IMG][/CENTER]

And I cant delete that file "bcd" or any other


[CENTER][IMG]http://i329.photobucket.com/albums/l380/bayshine/cd_boot.png[/IMG][/CENTER]

---

### Post by duke.tim on 2011-11-09
If I remember right, there is a little tab/switch on the DVD-RAM that will place it in read-only mode. Has that tab been switched?

---

