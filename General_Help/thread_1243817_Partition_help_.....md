---
title: "Partition help ...."
date: 2009-08-18
forum: General Help
---

### Post by wizzle on 2009-08-18
I get an error when I attempt install updates in ubuntu saying that I need to clear more space in my "/" directory. I've tried all the recommended clean up and deleting files but there are no files to delete as ubuntu is newly installed. Therefore I have come to the conclusion that I need a larger partition for ubuntu to run off of.

I have created a 5GB unallocated partition in Windows Vista. Now I have booted from Ubuntu CD and am looking to expand the partition so I can have room to install updates and such on Ububtu. How do I go about this safely from where I am now? Thank you.
----->[[IMG]http://img208.imageshack.us/img208/4615/screenshotkhc.th.png[/IMG]]("http://img208.imageshack.us/i/screenshotkhc.png/")

---

### Post by zvacet on 2009-08-18
Give that unallocated space to your extended partition sda3.So you need to extend extended partition.

---

### Post by michy99 on 2009-08-18
Here's a good How-to on expanding your Ubuntu partition:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by wizzle on 2009-08-19
> **michy99 said:**
> Here's a good How-to on expanding your Ubuntu partition:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
I followed this process and now I go back to ubuntu and I still do not have anymore space in the / directory I dont know what I did wrong. This is my current image
 [[IMG]http://img33.imageshack.us/img33/5871/screenshotyky.th.png[/IMG]]("http://img33.imageshack.us/i/screenshotyky.png/")

---

### Post by wizzle on 2009-08-20
help please. the unallocated space seems to have merged with the extended partition but it has not expanded my / directory space.

---

### Post by oboedad55 on 2009-08-20
> **wizzle said:**
> help please. the unallocated space seems to have merged with the extended partition but it has not expanded my / directory space.

Well, here's what I'd do. Your mileage may vary. Assuming this is a new Ubuntu installation you have little to lose. I would nuke /sda3 and redo those partitions to include the unallocated space. This isn't a Wubi install is it?

Jon

---

### Post by wizzle on 2009-08-20
ubuntu 9.04 not Wubi. I don't know how to do what you have suggested. Sounds a little dangerous but you are correct, I have nothing to lose on ubuntu but I do on Windows if somethings happens to go wrong.

---

### Post by oboedad55 on 2009-08-20
> **wizzle said:**
> ubuntu 9.04 not Wubi. I don't know how to do what you have suggested. Sounds a little dangerous but you are correct, I have nothing to lose on ubuntu but I do on Windows if somethings happens to go wrong.

It's always a good idea to backup your Windows stuff before you fiddle around with a new OS. Second, how did you create the partitions you now have?

---

### Post by wizzle on 2009-08-20
> **oboedad55 said:**
> It's always a good idea to backup your Windows stuff before you fiddle around with a new OS. Second, how did you create the partitions you now have?
I created the 5GB one in Vista the other small ones were already there.

---

### Post by 4t0m1c_w07f on 2009-08-20
> **wizzle said:**
> I followed this process and now I go back to ubuntu and I still do not have anymore space in the / directory I dont know what I did wrong. This is my current image
 [[IMG]http://img33.imageshack.us/img33/5871/screenshotyky.th.png[/IMG]]("http://img33.imageshack.us/i/screenshotyky.png/")

Now that the unallocated space is in the extended partition, all you have to do is right-click on the ext3 partition and resize then drag the bar to the end so that it fills the gray area..

---

### Post by michy99 on 2009-08-20
Move the left side of sda3 so it is against sda2.

Move the left side of sda5 to use all the free space in sda3.

---

### Post by wizzle on 2009-08-20
> **4t0m1c_w07f said:**
> Now that the unallocated space is in the extended partition, all you have to do is right-click on the ext3 partition and resize then drag the bar to the end so that it fills the gray area..
Thats the strange thing...I have done this already.

---

### Post by michy99 on 2009-08-20
After dragging the bar to resize, did you click on 'Apply'? The changes don't actually take effect until you do.

---

### Post by wizzle on 2009-08-20
> **michy99 said:**
> After dragging the bar to resize, did you click on 'Apply'? The changes don't actually take effect until you do.
yes

---

### Post by wizzle on 2009-08-21
problem solved. I just extended the SDA5 partition into the unallocated space and its all good. I have a new set of problems and errors now to deal with regarding 2 missing packages....

---

