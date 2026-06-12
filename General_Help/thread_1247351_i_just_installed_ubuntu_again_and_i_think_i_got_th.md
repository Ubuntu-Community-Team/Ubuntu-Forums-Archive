---
title: "i just installed ubuntu again and i think i got the partition wrong?"
date: 2009-08-22
forum: General Help
---

### Post by goku12205 on 2009-08-22
I can't go to firefox is there anyway i can get more memory so i can run more programs or should i just unistall ubuntu and do it all over again and get the partition
right this time?
 
one more questtion how do u unistall ubuntu without deleting the partition?
 
THANKS

---

### Post by AmerNewbieInDE on 2009-08-22
well, if you installed and it boots, you did it right. what error are you receiving.

---

### Post by michy99 on 2009-08-22
Check out this thread and see if it applies to your situation:

[http://ubuntuforums.org/showthread.php?p=7658271#post7658271](http://ubuntuforums.org/showthread.php?p=7658271#post7658271)

---

### Post by JC Cheloven on 2009-08-22
Well, you should try to be more specific in the future. I _imagine_ that:

- You installed buntu in a too small partition, and want to make it larger.
- Your present partition is about or less than 6Gb.
- You have other partitions, with other operating systems in them.

If the above is right, the proces could be something as:

- Boot from an OS in a partition contiguous to that of ubuntu
- Srink that partition (using system tools or other software)
- Boot from ubuntu live cd
- Enlarge the small partition by the space left by the other o.s.

If you need further guidance, please give more details, and post the output of ```
sudo fdisk -l
```

---

### Post by sandyd on 2009-08-22
> **goku12205 said:**
> I can't go to firefox is there anyway i can get more memory so i can run more programs or should i just unistall ubuntu and do it all over again and get the partition
right this time?
 
one more questtion how do u unistall ubuntu without deleting the partition?
 
THANKS
are you talking about RAM or swap?

if its RAM, you have to **PHYSICALLY** add ram to your computer.

if its the hard disk, you can boot a livecd, and run gparted. THen resize the partitions until its allright.

---

### Post by goku12205 on 2009-08-23
> **michy99 said:**
> Check out this thread and see if it applies to your situation:

[http://ubuntuforums.org/showthread.php?p=7658271#post7658271](http://ubuntuforums.org/showthread.php?p=7658271#post7658271)

yah thank u i go it right this time THANK YOU FOR YOUR HELP!!!!

---

### Post by credobyte on 2009-08-23
Unless you installed it from Wubi, you can't uninstall it ( deleting partition would be the one and only way of removing it ).

---

### Post by HolyMythos on 2009-08-23
This happened to me. This is how I fixed it:

Run Ubuntu from your LiveCD. Use the option "Try Ubuntu without any change to your computer". When it's loaded, go up to System>>Administration>>Partition Editor.

Now, you can do one of two things. You can either decrease the size of your other OS (which I'm guessing is windows) and then increase the size of Ubuntu, OR you can just delete Ubuntu and reinstall, which is easier IMO.

If you want to resize your other OS and increase Ubuntu, someone has linked to a thread above which tells you how. It's a little confusing at first.

If you want to reinstall, you're going to need to delete your old Ubuntu first. Find your old Ubuntu in that program. DO NOT delete anything NTFS. The size of it should probably be 2.5gb, there will be another one that says linux-swap, you can delete that two. You should only have to delete two partitions. Do not delete anything from Windows. If the Ubuntu is mounted, you're going to have to unmount it, just rightclick it and hit unmount.

Once unmounted and deleted, you can double click on the install on the desktop and install Ubuntu. Remember to move the slider around step four!

---

