---
title: "partition size incorrect - restored image w/ clonezilla"
date: 2009-08-17
forum: General Help
---

### Post by MystaMax on 2009-08-17
Hello. I recently upgrade from ubuntu 8.10 to 9.04. In the process, I upgraded my hard drive from 100GB to 160GB. my /home partition was only 6.8GB in size (bad decision from the start). So, I partitioned my new 160GB before installing ubuntu 9.04. Here's what it looked like

/ = 15GB (sda1)
/home= 40GB (sda2)
/media/media/= 90GB (sda6)

I used clonezilla to image my 8.10 /home (6.8GB) partition, and clonezilla to restore it to the new /home (40GB) on the 160GB.

I'm not entirely sure of the clonezilla options I chose, but I believe I went w/ the beginner mode, and not expert, selecting save-part, and only selecting the sda6 (home on 8.10). 

df -h reports:

/dev/sda2/ Size=6.8GB Used=6.4GB 97% full

gparted reports:

/dev/sda2 Size=40GB Used=39.44GB

How do I correct this so "df -h" reports the correct size? And so gparted reports the correct free space? Can I complete this without reimaging?

---

### Post by Herman on 2009-08-17
I think probably you restored your old 6.8 GB file system inside your new 40 GB partition but you didn't resize your file system to fill the new partition.

What you should do now is resize your file system to fill up the partition.

You can do that with a live CD. Open the terminal and use the resize2fs command,
```
resize2fs -p /dev/sda2 
```Where: '/dev/sda2' is the linux designation for your Ubuntu partition

If you don't like using the command line, just open GParted and right-click on the partition and click 'check', then 'apply', then 'apply' again and wait a few minutes and GParted will run some commands for you, the last of them being resize2fs. That should fix it.
[FONT=Bitstream Vera Sans Mono]
[/FONT]

---

### Post by MystaMax on 2009-08-18
You should be smiling right now, b/c you sir are the man! Thank you for your thorough explanation. Your steps worked great to resolve my issue.

I actually used the gparted to complete the task if anyone is wondering. I hope this can help someone else.

Thanks again.

---

### Post by HiImTye on 2009-08-18
> **MystaMax said:**
> You should be smiling right now, b/c you sir are the man!

he may not be but that made me smile lol

---

### Post by Herman on 2009-08-18
:) Yes, I am smiling, it always makes me happy when somebody gets what they want, I'm a sucker for happy endings. Thanks for taking the time to provide the positive feedback.
The way I learned about that was by having that same problem myself :)

---

### Post by gerv on 2010-09-23
Another vote here for Herman being The Man :-) This was exactly my problem, and you solved it - I can use my new 500GB drive as 500GB, not as the same size as the old one (100GB) :-))

---

### Post by jwiens on 2010-10-30
Not to take away the success of your solution, because it WAS a success, but you should let the noobs (like me) know that you can't use the check option in GParted when the partition has been switched and rebooted into the new part/dev as it cannot be unmounted .... BUT running the original command (with sudo) will solve, so ..... THANK YOU!!

---

### Post by matsuzine on 2010-10-30
Not certain, but I think this is the default for clonezilla and you always need to resize the file system.  Does anyone know if there is an option to have clonezilla take care of this automatically?

---

### Post by bcollignon on 2011-02-19
This worked for me!  Thanks again.  Clonezilla and GParted are, as far as I'm concerned, the best programs of their kind around.  Properly used, they can save you from cataclysm.

---

