---
title: "hard drive questions"
date: 2012-09-24
forum: General Help
---

### Post by disturbed13 on 2012-09-24
okay i recently had my 1TB HDD fail with my Vista OS
so i lost all of my product keys
and now i am more parnoid then ever about loosing by OS disk
i have another 1TB HDD that i can clone my OS disk to
im just a little unsure about useing clonezilla
so now on to my question

if i was to use Ubuntu on another HD could i just copy one drive to the empty one?
and in my BIOS set the current drive to the primary boot order, then Ubuntu as a seconday, and possibly the last disk in the boot order

would this work?
would i have 2 bootable Vista distro?
i know i would have a dual boot at minimum
but im hoping i can have a tripple boot with a cloned OS disk

any help would greatly be appreciated
thanks peeps :-P
mmmmm sugar :-P

---

### Post by zero2xiii on 2012-09-24
Hay,

Unfortunately it is not as easy as it might sound.

Although the clone will contain all the readable data, it will not be able to boot it straight since the drive will seem corrupt to windows. (I know for a fact this happens on windows 7 even when you just resize the partitions). But however, if you have a windows CD you should be able to boot to a recovery console on the cloned drive and fix the MBR (unplug the ubuntu drive for this!!) and do all the required maintenance  tasks on the drive and make it bootable, but it is a rather tedious process with a lot of trial and error.

All of the above is true in the asumption that the OS data at the very least is not corrupted. Depending on HOW the drive failed, there might be close to zero hope on just "fixing" the OS and going on as if nothing happend.

There are a few ways to recover the product key from specific windows files, but I do not think forum policy allows such methods to be described as it can be used to harvest sensitive data. Google might be a friend here.

Cherz

---

### Post by doktorOblivion on 2012-09-24
I actually did this not too long ago for my Win7 partition.  My requirement was that I wanted to move off of an HDD onto a SSD for better performance.  To perform this move I used my copy of Acronis True Image.  First I created a partition (NTFS) that contained a full backup copy of my system, just in case things went wrong.  Plus its always good to have one of those.  Next, I created an exact clone of my Win7 partition using Acronis Disk Director.  This took some time since you have to make sure you choose the correct geometry, etc...  Once finished, I had to boot Ubuntu in order to make the correct changes to grub2, at least temporarily, so the new partition would show up on the boot screen.  Once I got the new partition to boot, I had to go into the registry, after backing the entire thing up, and change all occurrences of the unique drive letter I had choosen prior to the clone ( e.g. Q: ), to the drive letter windows would expect for all the applications, etc ( e.g. C: ).  Reboot again, change grub2 for good.  Reboot again, select the new Win7 partition, I was done.

---

### Post by disturbed13 on 2012-09-24
hay!
thanks for the replys guys
but i think theres a mix up
ive already recovered from the drive failure

and since then ive bought $500 worth of software
that i dont want to loose

so ill re-ask just to make 100% sure that we are all on the same page
i have a primary 1 TB HD with my Vista install and all of the saves
i have another 1 TB HD that is sitting empty
i can add yet another HD that is like 160 GB
its a lappy HD, and this small dive is what will have the Linux OS

now with the boot order correct in my BIOS
the current 1 TB in primary, the Linux OS in Secondary, and the for now empty 1 TB in the third position
could i just boot into linux
and use it to select everything from my main drive and drag and drop it into the empty dive?
if i did so would it boot from the third dive?

again thank you so much for taking the time to look
and try to help
thanks

---

### Post by zero2xiii on 2012-09-25
> **disturbed13 said:**
> 
could i just boot into linux
and use it to select everything from my main drive and drag and drop it into the empty dive?
if i did so would it boot from the third dive?


hay, the short answer is no.

You need to 'clone' the drive. Sigh. The word clone has gotten so misused over the past few years. You can try True Image from Acronis, but I have not tried, nor tested it in any manner.

What I meant with clone was doing a byte for byte copy of the drive, and as I said above, I will say again. All methods, even if you use some simple GUI app or some hardcore CLI app, if the files are corrupt, or damaged in any sence, then it will not work no matter how you clone/copy/image the drive. The integrity of the files is most important. Further more, is the original drive bootable? If not, then it will not be as easy as doktorOblivion stated, then you will have to "fix" the boot manualy. Again, not just reinstall windows as this will just simply wipe the registry and all other related things, you will need to reconstruct the boot from the ground...

So first start with if it is bootable at all, are all the files intact etc. Also, this is a much more windows discussion than it is ubuntu.

Cherz

---

### Post by disturbed13 on 2012-09-25
okay
i really do appreciate the help
but i still have a follow up question

# )    how is Acronis True Image supposed to make a complete disk image if it runs on Windows. it wont, it can copy something that is already in use. i.e. the core of the OS, if that part is lost then so is your data. the pointers that tell the OS where on the HD the data is are gone forever!

## )    does anyone have any have any good recommendations for a program that will clone one HD to another from in Linux?


thanks everyone!!!

---

### Post by zero2xiii on 2012-09-27
> **disturbed13 said:**
> 

## )    does anyone have any have any good recommendations for a program that will clone one HD to another from in Linux?


Hay,

```
man dd
```

Cherz

---

