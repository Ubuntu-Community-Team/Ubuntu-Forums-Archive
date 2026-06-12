---
title: "Shrinking EXT3 partition in Gparted not working"
date: 2009-11-17
forum: General Help
---

### Post by I8NY on 2009-11-17
So i want to shrink the EXT3 partition from 900gb to 500gb and make the NTFS bigger on my 1tb hdd.  The problem is when i boot the live CD that has gparted (ubuntu 9.10 or gpart 0.4.8.6 live cd) it will not shrink the ext3 partition with unallocated space in it.  I can shrink partitions in the ext3 but not the ext3 partition it self.  I don't have the hdd mounted And I really don't want to try to shrink it in the terminal.

---

### Post by dcstar on 2009-11-17
> **I8NY said:**
> So i want to shrink the EXT3 partition from 900gb to 500gb and make the NTFS bigger on my 1tb hdd.  The problem is when i boot the live CD that has gparted (ubuntu 9.10 or gpart 0.4.8.6 live cd) it will not shrink the ext3 partition with unallocated space in it.  I can shrink partitions in the ext3 but not the ext3 partition it self.  I don't have the hdd mounted And I really don't want to try to shrink it in the terminal.

You are not making sense, an EXT3 partition cannot have "partitions in the ext3". If you want to shrink an EXTENDED PARTITION then you must unmount all partitions inside of it and move any of those partitions away from the boundary that you want to shrink.

---

### Post by I8NY on 2009-11-18
oops.. i though the extended partition was a EXT3 partition with mini partition in it.  Okay so i want to shrink the extended partition with unallocated space in it but, it is in between 2 partitions.  How do i get the unallocated space to the side so i can shrink the extended partition?

---

### Post by confused_user on 2009-11-18
can you post a screenshot of gparted so we can see what your partition table looks like?

i've just done what your trying to do so i might be able to help 9i had to move a partition (to get it in the right order) along a the disk a bit and then i could adjust the size.  it really does depend on how the table is laid out though

also post the output of sudo sfdisk -l would be nice.

---

### Post by TheNewGuyHere on 2009-11-18
hello i too am having the same problem as described above i am trying to shrink my ext3 partition on my 1tb hd to 300 gb instead of taking up the whole 1 tb 

this is the output of my sudo sfdisk -l
```
 
Disk /dev/sda: 35681 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  34267   34268- 275257678+  83  Linux
/dev/sda2      34268   35680    1413   11349922+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      34268+  35680    1413-  11349891   82  Linux swap / Solaris

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+ 121600  121601- 976760001   83  Linux
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
alon@alon-server:~$ 
 
```

and this is a screenshot of gparted getting stuck at the same point it gets stuck on every time

[http://yfrog.com/7h51946874p](http://yfrog.com/7h51946874p)

and a screenshot of the output of the sfdisk -l

[http://yfrog.com/7h19087027p](http://yfrog.com/7h19087027p)

---

### Post by dcstar on 2009-11-19
> **TheNewGuyHere said:**
> hello i too am having the same problem as described above i am trying to shrink my ext3 partition on my 1tb hd to 300 gb instead of taking up the whole 1 tb 
..........
and this is a screenshot of gparted getting stuck at the same point it gets stuck on every time

[http://yfrog.com/7h51946874p](http://yfrog.com/7h51946874p)


You have to show the part that **failed**, not the part that was successful.

---

### Post by confused_user on 2009-11-19
OK i meant a screen shot like this one form my system since i stand no chance of helping you based on the info you provided in your post.

[IMG]http://i50.tinypic.com/244y2l4.png[/IMG]

I'm trying to work out what your partition table looks like as it is that that is most likely causing your problem.

---

### Post by I8NY on 2009-11-19
here is my screen shot

---

### Post by confused_user on 2009-11-20
ok, so as you have already worked out, you need to shrink the size of your **extended** partition first and then move it to the right hand side.

That will free up some space next to the NTFS **Primary** partition and then you should be able to resize the NTFS partition (make it bigger).

SO what happens when you right click and select "move / resize

here is a useful guide that will ... guide you

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

let me know how you get on

---

### Post by bodhi.zazen on 2009-11-20
Your unallocated spaces are quite small, a few Mb. Although irritating, you can not always recover these spaces without backing up your data and reformatting.

I am not certain, but I think this results from some type of rounding gparted does, ie rounding so many Gb to cylinders on your hard drive.

---

### Post by dcstar on 2009-11-20
> **I8NY said:**
> here is my screen shot

Unmount **all** the partitions inside the Extended Partition and then you can simply expand the Extended Partition as far as you like.

You must do all of this booting off a Live CD/USB.

---

