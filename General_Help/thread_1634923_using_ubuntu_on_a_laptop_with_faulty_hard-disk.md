---
title: "using ubuntu on a laptop with faulty hard-disk"
date: 2010-12-01
forum: General Help
---

### Post by ubun_tut on 2010-12-01
hi, i have a 2-year old acer laptop that has been running windows xp from day 1. however, some days ago, it failed to start, and the windows repair mechanism fails to get rid of this problem. the technician at the computer repair shop also could not repair it, and suspects that something is wrong with the hard disk.

i am able to use the ubuntu live cd to run this machine. my question is, is there a way to check (maybe via terminal commands?) for faults on the computer while i am running this live cd? i did a 'df', and it reports a few items, such as tmpfs, varrun, varlock, udev etc, each of which is about 1 GB in size. this adds up to way smaller than 250 GB that is inside.

the next question is, is there a way to somehow install ubuntu onto this faulty machine, so that i dont need to run the live cd all the time? is it possible to determine the faulty sectors in the hard disk, then use g-parted to cut out a still-good portion, and then install ubuntu onto that?

edit: i just ran gparted, and it shows up 4 partitions, which do add up to about 250 GB. 2 of these items (type ntfs) have exclamation marks beside them, and under 'information' it is stated that they have bad sectors. the other 2 partitions are ok, and total about 15 GB. can i ignore the faulty partitions altogether and install ubuntu onto the good partitions?

---

### Post by ronnielsen1 on 2010-12-01
It would probably be better to check your hard drive with Hirens boot cd. It has a lot of hard drive utilities. 

As far as installing w/o a hard drive, you would need somewhere to go with the files - usb maybe?

---

### Post by bbb777 on 2010-12-02
edit: sorry wrong post

---

### Post by ubun_tut on 2010-12-02
yes, i was thinking of booting from a usb drive every time i use the computer too. for now, though, i have managed to install ubuntu hardy onto the faulty hard disk (surprisingly) after deleting the windows os from it and formating it to ext32. i did not use the entire windows partition, but rather i used about half of that (~100 GB). the ubuntu seems to be running fine, even after a few reboots. does this mean the ubuntu install has somehow managed to avoid using the faulty sectors, or even better, repaired it?

---

### Post by ronnielsen1 on 2010-12-03
Only if it was data errors. Mechanical errors will come back. Of course you said the tech suspected a bad hard drive - doesn't mean it was. Best Buy tells customers they need a new hard drive all the time.

---

### Post by ubun_tut on 2010-12-03
other than the tech guy, when i hit 'information' on the partition in gparted, it says that the partition has some physical damage. so i think the damage should be real. anyways, i am not complaining now i can get the laptop running again. dont like the idea of replacing the hard disk because that will probably cost as much as buying a new netbook..

---

### Post by Spyderkid on 2010-12-03
You could use "Tiny Core" Linux it runs in the RAM Memory so there's no need for a Hard Disk even though you need to put the CD in for boot up.

---

### Post by C.S.Cameron on 2010-12-03
Have you tried to repair the partitions using gparted?

---

### Post by ubun_tut on 2010-12-04
i think i tried something like repairing when i was examining the hard disk using gparted, but couldn't repair. if i remember correctly, it cited 'physical damage' or something like that. 

@Spyderkid: it is more convenient for me to carry around a thumbdrive than a CD, so i guess i will stick to a thumbdrive boot as my last resort. thanks for the suggestion

---

### Post by lisati on 2010-12-04
<appreciative aside>
I feel your pain: after it's BIOS failed to recognize its HDD a handful of times, my laptop is waiting for me to figure out how to get into it without breaking anything, so I can de-gungify it (I smoke) and check the connectors before deciding if I should take it in to be checked.
</appreciative aside>

If the "bad sectors", as reported by gparted, are on a Windows partition, a short-term solution might be to use something like CHKDSK or SCANDISK.

---

### Post by ubun_tut on 2010-12-04
the problem is that to do scandisk or chkdisk you have to get into windows and initiate these from there. my computer couldn't even get to the windows logo stage

---

