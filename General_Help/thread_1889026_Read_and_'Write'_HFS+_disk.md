---
title: "Read and 'Write' HFS+ disk"
date: 2011-11-30
forum: General Help
---

### Post by katya_sehgal on 2011-11-30
I have a HFS+ external disk that I wish to use with Ubuntu. 

This is what I have done till now:

Following the advice on  ```
http://raamdev.com/2008/mounting-hfs-with-write-access-in-debian/
```

I went for > sudo apt-get install hfsplus hfsutils hfsprogs

After which, I edited my fstab entry to include:

> 8664920a-12b8-375e-98df-20100d87646e /media/katya hfs+ user ,rw,force 0 2


Then, through Nautilus, I tried changing permissions for the external drive. I was unable to do that.

I get the following error message:

> Sorry, could not change the permissions of "WD SmartWare": Error setting permissions: Read-only file system


and 

> The owner could not be changed. Sorry, could not change the owner of "katya": Error setting owner: Read-only file system


'katya' is my external HFS+ drive's name.


I understand that disabling 'journaling' in HFS+ is not a good idea as it is a useful function.

I need to access the drive urgently.
What's the solution?

---

### Post by cholericfun on 2011-11-30
i vaguelly remember having to disable journaling in HFS+ in order to access the drive for writing. I think thats the only way to do it but i let you google that yourself.

---

### Post by jjex22 on 2011-11-30
Just a thought, but your fstab settings don't match mine:

>  /dev/sda1 /mac **hfsplus** force,rw,**exec,auto**,users,**uid=501,gid=100** 0 1 

Gotta be honest I stole this setting from somewhere on the forums ages ago :)

hope it helps!

Edit: don't forget to restart after!
Edit 2 - also just noticed you've got a space between user and the comma - if this is in your fstab, could also be a problem.

---

### Post by katya_sehgal on 2011-11-30
> **jjex22 said:**
> Just a thought, but your fstab settings don't match mine:



Gotta be honest I stole this setting from somewhere on the forums ages ago :)

hope it helps!

Edit: don't forget to restart after!

I entered your solution and tried to change user through nautilus. It did not work. Did you have a 'journaled' HFS+ drive by any chance?

> 8664920a-12b8-375e-98df-20100d87646e /media/katya hfsplus force,rw,exec,auto,users,uid=501,gid=100 0 1

---

### Post by katya_sehgal on 2011-11-30
> **jjex22 said:**
> Just a thought, but your fstab settings don't match mine:



Gotta be honest I stole this setting from somewhere on the forums ages ago :)

hope it helps!

Edit: don't forget to restart after!

Restart the laptop or the drive?

---

### Post by katya_sehgal on 2011-11-30
> **cholericfun said:**
> i vaguelly remember having to disable journaling in HFS+ in order to access the drive for writing. I think thats the only way to do it but i let you google that yourself.

I have also looked at solutions to disable journaling through Ubuntu and Windows. I have not found straightforward answers.

---

### Post by katya_sehgal on 2011-11-30
In the case anybody wants more information to solve this issue:

Information about the external drive.

I have 2 partitions. I have not made them. I had used this drive with a mac. 

/dev/sdb1 and /dev/sdb2

/dev/sdb1  is fat32 (file system), boot(flag)

/dev sdb2 is hfs+ (file system), and it's mount point is /media/katya
This is the main partition, as in, it's size is 930.54 GB and my data goes in this partition.

Using this info:

> 8664920a-12b8-375e-98df-20100d87646e /media/katya hfsplus force,rw,exec,auto,users,uid=501,gid=100 0 1

or 

> 8664920a-12b8-375e-98df-20100d87646e /media/katya hfs+ user ,rw,force 0 2


Is there any error?
Also note that I have installed the hfs programs using:

> sudo apt-get install hfsplus hfsutils hfsprogs


Whether possible or not, kindly let me know.
(If not, then what's the next best method)

---

### Post by jjex22 on 2011-11-30
Hi there, it's definitely journalled - as is the mac way - it's on an internal partition though...

But yes restart your PC - hopefully it'll pick it up at boot?

---

### Post by katya_sehgal on 2011-11-30
> **jjex22 said:**
> Hi there, it's definitely journalled - as is the mac way - it's on an internal partition though...

But yes restart your PC - hopefully it'll pick it up at boot?

At start up... serious error were found in disk drive...

press i to ignore     
s to skip mount
m for manual recovery


I pressed "s" to skip mount



Edit: I removed the usb and re-plugged it. Ubuntu is now reading the drive. For safety, I am deleting the fstab entry I had made.

---

### Post by cholericfun on 2011-11-30
> **katya_sehgal said:**
> I have also looked at solutions to disable journaling through Ubuntu and Windows. I have not found straightforward answers.

this is just very vague recollection of mine, i think it was an issue of *switching off the journaling in OSX* or never. Havent done any searches on recent developments though...

---

### Post by OrangeVixen on 2012-10-23
Make sure that you create the file system using a Mac whenever possible, was that drive's filesystem create with a Mac?

Yes, you MUST disable journalling.

Also, make sure that the permissions are set to read/write for ALL users (which is not the default).

Sometimes HFS file systems get corrupted when you write multiple files to it at once.

---

