---
title: "How Little Swap Do I Really Need?"
date: 2009-10-25
forum: General Help
---

### Post by winotree on 2009-10-25
[If this is not posted in the appropriate forum, please move it]  I recently installed Koala 9.10 and have been very satisfied with it  -- however I notice that the default install uses a good bit of my SSD for swap as shown by **gparted** at nearly 500MB.  Granted, I don't really know what I'd use all that extra space *for*  but I'm really curious as to how much space is necessary;  what's the minimum the Koala needs to function on an older model netbook doing what it was designed to do?

ASUS EeePC 701(B) 4G SSD
1 GB RAM

winotree@h1n1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.5G  1.7G  1.7G  51% /
udev                  498M  264K  497M   1% /dev
none                  498M     0  498M   0% /dev/shm
none                  498M   76K  498M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw
/dev/sdb1             7.5G   70M  7.0G   1% /media/disk

If additional information is needed please let me know.  As I said, this is more a curiosity than a necessity.  :D

EDIT - I know *how* to change the **hda5** partition -- my question is: how small can it be before I potentially hurt my system...

---

### Post by snowpine on 2009-10-25
0mb. I have no swap partition on my Dell Mini 9 (8gb ssd, 1gb ram) and Ubuntu runs fine. Swap is only necessary if you don't have enough ram for your daily tasks, or you want to hibernate to disk (in which case it must exceed the size of your ram).

---

### Post by Matt__ on 2009-10-25
I dont run any swap at all as i have no wish to hibernate system and have 4Gb Ram..

(to hibernate you will need swap == RAM in use)

never got anywhere near maxed out RAM yet so no probs so far!

---

### Post by winotree on 2009-10-25
> **snowpine said:**
> 0mb. I have no swap partition on my Dell Mini 9 (8gb ssd, 1gb ram) and Ubuntu runs fine. Swap is only necessary if you don't have enough ram for your daily tasks, or you want to hibernate to disk (in which case it must exceed the size of your ram).
That's the answer I wanted to hear!  Thanks, **snowpine** for your help.  ;)

---

### Post by winotree on 2009-10-25
> **Matt__ said:**
> I dont run any swap at all as i have no wish to hibernate system and have 4Gb Ram..

(to hibernate you will need swap == RAM in use)

never got anywhere near maxed out RAM yet so no probs so far!

I hear you, too, **Matt__** .  I'll use the suspend feature [after two years it's nice to have an OS that lets me use this function out-of-the-box] on a daily basis but have heard that the hibernate feature may cause issues so have not tried it, if for no other reason than this is my one and only computer and I'd rather not have it in deep-sleep and be unable to access the good help I'd get here.  Thanks for your input.  See you around the forum?  :)

---

### Post by gdonwallace on 2009-10-25
Swap works like the swap file in Windoze.  The OS can use it as memory (RAM) if it needs more memory for a task.  If you don't think you need more than 1 gig or memory, then you can do away with the swap partition all together.  

Officially though it is recommended that swap be at least 50% of your physical RAM.

It comes down to choice of the user.  If you can do without, then don't use it.  The only down side may be that some programs MIGHT run slower as they need more memory to run and GNU/Linux needs to dump something from RAM to get it running.  Of course, depending on what you are doing and programs running, it may not make any performance difference at all.

---

### Post by winotree on 2009-10-25
> **gdonwallace said:**
> Swap works like the swap file in Windoze.  The OS can use it as memory (RAM) if it needs more memory for a task.  If you don't think you need more than 1 gig or memory, then you can do away with the swap partition all together.  

Officially though it is recommended that swap be at least 50% of your physical RAM.

It comes down to choice of the user.  If you can do without, then don't use it.  The only down side may be that some programs MIGHT run slower as they need more memory to run and GNU/Linux needs to dump something from RAM to get it running.  Of course, depending on what you are doing and programs running, it may not make any performance difference at all.That's right.  I've tried it both ways and never noticed any differences but didn't know if the changes to **ext4** and **GRUB2** would require it.  Like I said it's a netbook [one of the originals] and I use it as it was intended.  :rolleyes:

*But now* I've got 1.9GB unused space on my 4.0GB SSD and all I can say is:  woo hoo!!:cool:\\:D/

---

### Post by linux4life88 on 2009-10-25
In your case your hard drive is so small that you may want to have no swap space at all. I've heard some say you should have twice as much swap as you have physical ram and I've also heard you should have half of you physical ram as swap space. I have 4gb of ram and only use a 1gb swap space. But as I said you have a very small hard drive so having no swap will be fine. It will only slow down some programs while multitasking, nothing else will be effected when you have no swap space.

---

### Post by shaggy999 on 2009-10-25
> **gdonwallace said:**
> Swap works like the swap file in Windoze.  The OS can use it as memory (RAM) if it needs more memory for a task.  If you don't think you need more than 1 gig or memory, then you can do away with the swap partition all together.  

Officially though it is recommended that swap be at least 50% of your physical RAM.

It comes down to choice of the user.  If you can do without, then don't use it.  The only down side may be that some programs MIGHT run slower as they need more memory to run and GNU/Linux needs to dump something from RAM to get it running.  Of course, depending on what you are doing and programs running, it may not make any performance difference at all.

Where exactly would the OS dump RAM when there is no swap file? Answer: No place. If you run out of RAM and have no swap space what it does is it starts KILLING programs to make room.

Personally, I also use no swap on both my EEE PC 900a (2 gigs RAM total) and on my desktop quad core w/ 4 GB RAM. Oh, also I have a virtual user folder mounted to tmpfs and have quite a few files that get copied over to it from an SD card on boot and there is TONS of room left in RAM.

Swap is kind of a relic from the past when program capacity exceeded physical RAM capacity. That can still happen, especially if you work with extremely large files (digital video, 3D modeling, massive photoshop files, high-end scientific computing, etc) but these days RAM is cheap and program size really isn't increasing as dramatically as it used to.

The only real need for a swap file would be for hibernation, in which case the swap file has to be as big as your RAM... and with gaming motherboards supporting as much as 12 or 24 gigs of RAM these days, who really wants to waste that much space for hibernation? That probably takes a real long time to go into/out of hibernation. I wonder if there's a method for writing "compressed" RAM to disc since there's probably tons of empty RAM on systems like that. I know I rarely go over 1 or 1.5 gigs of RAM used on my desktop machine.

---

### Post by Sven6210 on 2009-12-21
I have an EeePC 900a with 2 GB of RAM and 8 GB hard disk. And as so many here in the Threat I am not using any SWAP at all. I thought about it in order to use the hibernation mode but then I decided not to do it. Using 25 % of my hard disk only for the hibernation mode is not worth it.

By the way, I think it is a pity that nowadays nearly all netbooks are equipped with a hard disk. So far I am very happy with the SSD, especially when travelling I am less concerned about shocks for the netbook. And I use my netbook mostly for traveling. Additional to the 8 GB SSD I have a 8 GB SD Card installed. And 16 GB is O.K. for my mailbox, many letters and spreadsheets and even 6 movies (xvid format).

---

