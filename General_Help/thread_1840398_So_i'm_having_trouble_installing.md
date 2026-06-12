---
title: "So i'm having trouble installing"
date: 2011-09-07
forum: General Help
---

### Post by itechtom on 2011-09-07
I'm new to this sort of thing, so I've followed a few easy steps from various sites and videos on how to partition my hard drive with windows 7. I partitioned 25GB worth of space and is now an unallocated partition....

So (tell me if I'm doing it wrong here)..I restart windows and then reboot again with my ubuntu ISO. I don't get the option to install side by side and when I go to install it manually to the drive, the space I have created is listed as unusable.

Is there something I'm doing wrong or am I missing something out :S any help would be appreciated as I'm really looking forward to being able to use this for the first time :)

---

### Post by e79 on 2011-09-07
> **itechtom said:**
> So (tell me if I'm doing it wrong here)..I restart windows and then reboot again with my ubuntu ISO. I don't get the option to install side by side and when I go to install it manually to the drive, the space I have created is listed as unusable.

Can you click on this 'unusable' partition and choose to use it (format it, use as ext4, mount point is "/" without quotes) ?

If it does work, then select the whole drive to put GRUB on it (the name of your drive should appear in the scroll box) and continue your installation.

Hope this helps

---

### Post by itechtom on 2011-09-07
Hmm no it also doesn't mention what type it is e.g ntfs...

It gives me the only option revert for some strange reason. I am actually a noob when it comes to this. 

Im still rather confused as to why when I go to allocate drive space I only get two options. One is removing windows and replacing with ubuntu (which I don't want to do) or the "something else" option in which I can find my space I've created but it is unusable :/ 

Apologies if this is frustrating to you guys how dumb I am at this haha

---

### Post by e79 on 2011-09-07
Could you post a picture of this screen perhaps using a camera ?

---

### Post by itechtom on 2011-09-07
sure here you go!...ipads are useful afterall hehe

[IMG]http://i1128.photobucket.com/albums/m491/Itechtom/ae0cea6d.jpg[/IMG]

[IMG]http://i1128.photobucket.com/albums/m491/Itechtom/4c626dbc.jpg[/IMG]



if you need any more photos then I can do so also. I am only available for an hour now as I have work to attend to :(

---

### Post by Blasphemist on 2011-09-07
You can only have 4 primary partitions, and you already have 4. So ubuntu can't create an extended partition to use as that is a type of primary partition. You'll need to delete one of your existing partitions. What do you have in them? 

You may want to refer to this site to learn more about this. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by e79 on 2011-09-07
This is a long shot but here's what I think is going on.

You seems to have already reach the number of maximum Primary partitions on your disk (partition that allows an operating system to be installed and boot) as I see 4 NTFS partittion (sda1, sda2, sda3, sda4). The 5th one (the blank and unusable one) is probably an Extended partition, which cannot hold an operating system (only data).

If I'm right...well you would need to erase and reuse one primary partition...and only you could know which is what...

Might say I'm a bit lost on which advice give you next...

---

### Post by itechtom on 2011-09-07
hmm well im in a bit of a situation then as this is what i have.

[IMG]http://i1128.photobucket.com/albums/m491/Itechtom/Untitled.png[/IMG]

so I thought i wouldve been able to install it onto my Data (d) drive but I cant see that being possible. so if I were to erase a partition then I have no idea what I should erase =/ lol I presume I need to keep my D drive?

---

### Post by e79 on 2011-09-07
well C: and D: and for sure the boot partition (the 100MB one - which should be left untouched) ...so the only possibility left would be to destroy your 17GB Recovery partition....which would then prevent you to do a factory reinstall of your Windows...unless you have the Windows DVD in case that happens...

Though decision.....

The only real solution left as far as I can see would be to use WUBI to install it....
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Taken from the WIKI
> While Wubi does not install Ubuntu directly to its own [partition]("http://en.wikipedia.org/wiki/Disk_partitioning")....[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29")

Maybe someone could advise better....

---

### Post by Blasphemist on 2011-09-07
The recovery partition is the one to delete. It is really just a copy of the install disks. Do you have win 7 install disks now? If not you should get some from microsoft. They only let you install a clean win 7 though and you'd still have to install all programs and restore all files created. A good complete backup is of course much better.

Deleting the recovery partition will let you install ubuntu but you'll still have issues because your free space will not be contiguous. Resolving that would mean moving partitions and is not without risk of data loss. GParted is on the ubuntu live cd and can do that but your first task would seem to be getting a good backup done. Do you have that? Windows includes a backup that can do this.

If it was me I'd want to reorganize the disk. If you want to go that direction please do this. Boot to the ubuntu live cd, install boot-repair, uncheck everything except create boot info summary and post back here the web address that it gives you for the boot info summary. It automatically posts the results to the web that we would need to help with reorganizing the disk.

---

