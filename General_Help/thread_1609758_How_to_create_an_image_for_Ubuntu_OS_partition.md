---
title: "How to create an image for Ubuntu OS partition ?"
date: 2010-10-30
forum: General Help
---

### Post by geek2330 on 2010-10-30
Ok, have a system with 10.10 with the things I need, I installed this OS on a laptop which has a 40gb drive. 32-bit version.
Before installing ubuntu i had Windows7 and had split the drive in 2 partitions (20/20) and currently have an image of the Windows7 OS in the 2nd partition.

Anyway, when installing ubuntu i used the 1st partition that has Windows7 OS and made 3 partitions out of it:

-12gb partition for /root
- 3gb partition for /swap
- 5gb partition for /home

In the Windows world i use Ghost utility(DOS version) to image my single Windows7 partition completely. This works fine.

Since in ubuntu we usually create multiple partitions, 

1-what utility can be used to create an image of the partition ?
2-do you JUST create the image of /root ?

I really want to create an image now that i can then restore if something happens to the OS and be back in business quickly without reinstalling ubuntu from scratch.

Thanks..!!

---

### Post by papibe on 2010-10-30
I would recommend take a look at Clonezilla. It's a live CD that can clone even windows partitions. The interface is a little old fashion, but it works. Checks this links:

[INDENT][LIST]
[*][Wikipedia]("http://en.wikipedia.org/wiki/Clonezilla").
[*][Clonezilla site]("http://clonezilla.org/").
[*]Clonezilla [review ]("http://www.youtube.com/watch?v=7nHur5BvV6o")on youtube.
[*]Clonezilla in [depth ]("http://www.youtube.com/watch?v=7WGSMHWV73s&feature=channel")on youtube.
[/LIST][/INDENT]

Good Luck!

---

### Post by geek2330 on 2010-10-30
ok, thanks.

What about my question #2, do you just image the /root partition?

..

---

### Post by papibe on 2010-10-30
Since 40Gb it is not too much, why not to clone/backup the whole disk?

Anyway If were you I would backup my /home, since / (known as root) it is easier to recover in case of a catastrophe. Even in the worst case scenario (complete reinstall), it wouldn't be so bad. On the other hand, it is indeed a wise decision to backup your windows partition since it's more complicated to recover, and also because it contains your user files.

Regards.

---

