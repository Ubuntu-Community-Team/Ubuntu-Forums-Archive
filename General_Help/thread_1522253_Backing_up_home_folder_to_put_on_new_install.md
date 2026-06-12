---
title: "Backing up home folder to put on new install"
date: 2010-07-01
forum: General Help
---

### Post by false_chicken on 2010-07-01
My hard drive is failing. And I need to backup my home folder but I cant boot into the drive because it makes noises and stops. But I can get to it in the 10.04 live cd. But many files I cant access because I dont have the permissions. How can I get the required permissions to back it up then restore it on a fresh install? Thanks.

---

### Post by mr clark25 on 2010-07-01
run this command from the live cd:
```

gksu nautilus

```

this will bring up the file browser as root, which should let you do whatever you want.



i would recommend moving your home folder twice, and then running a md5sum to make sure nothing got corrupted. if you need help with this, just let us know.

---

### Post by false_chicken on 2010-07-02
I have copied backed up my files with no issues:). Now I am sitting here at the disk partitioning screen and would like to do the separate partition option. As I hear it is easier to recover from file system errors and such plus I like less fragmentation of /. Any advice on how to do this? Or a good guide on it?

---

### Post by garvinrick4 on 2010-07-02
> **false_chicken said:**
> I have copied backed up my files with no issues:). Now I am sitting here at the disk partitioning screen and would like to do the separate partition option. As I hear it is easier to recover from file system errors and such plus I like less fragmentation of /. Any advice on how to do this? Or a good guide on it?
Are you doing single or a dual boot? You do have a sdaX that you have to install it in? X being your partition #. How much Ram do you have. You are doing a manual install?

---

### Post by false_chicken on 2010-07-02
It will be a single boot. If needed windows will be installed on another  drive later. then ill just put grub over it. I have 3 gigs of ram and the harddrive is 160 gigs. I am doing manual partitioning. I am trying to figure out the optimal partition setup.

---

### Post by garvinrick4 on 2010-07-02
> **false_chicken said:**
> It will be a single boot. If needed windows will be installed on another  drive later. then ill just put grub over it. I have 3 gigs of ram and the harddrive is 160 gigs. I am doing manual partitioning. I am trying to figure out the optimal partition setup. I like to make sda1 /boot and sda2 extended partition next partition will be a logical partition for / and you have plenty of ram no swap needed. On last page of install which is page 8 I believe there is an advanced tab click on it and make sure it is sda not sda1 or sda2 make sure sda
 If you are doing more linux installs later might as well make a /home as largest and the / as maybe 10 gig or so. / only takes up 4 gig when installed and upgraded. For example below click on.

---

### Post by false_chicken on 2010-07-02
> **garvinrick4 said:**
> I like to make sda1 /boot and sda2 extended partition next partition will be a logical partition for / and you have plenty of ram no swap needed. On last page of install which is page 8 I believe there is an advanced tab click on it and make sure it is sda not sda1 or sda2 make sure sda
 If you are doing more linux installs later might as well make a /home as largest and the / as maybe 10 gig or so. / only takes up 4 gig when installed and upgraded.

I think i am confused lol. I think it needs to be worded simpler lol. I only plan to have lucid on this drive. I see options for mount points (/ , /usr , /home) And I dont know exactly what to do. I think your explanation was good but too complex for me to understand.

---

### Post by garvinrick4 on 2010-07-02
> **false_chicken said:**
> I think i am confused lol. I think it needs to be worded simpler lol. I only plan to have lucid on this drive. I see options for mount points (/ , /usr , /home) And I dont know exactly what to do. I think your explanation was good but too complex for me to understand. Okay / is your file system like your C: drive in 
windows. /home is where you keep your music, documents downloads and such. It only be convenient if there is a possibility of more than one linux install. If just one ever ignore.
Make a 300 meg or so sda1 for /boot in ext4 and then the rest make a extended partition and then the / is formatted in ext4 in a logical partition as big as you want. You can always shrink it later if you decide you want to put another Ubuntu version in future. Just ignore all the other like /var and such for now not important to you.
Remember advanced tab at end of install on page 8 or so in lower right hand corner and
select sda
 3 Types of partitions Primary (only 4 allowed on drive) Extended a house for all the logical partition you want. Windows will not live in logical partitions, only Primary. Extended counts as 1 primary. But holds a lot of logical partitions for linux. Linux is formatted now in ext4, Windows in NTFS.
 The 300 meg boot partition I like to use, some do some do not. I like it. Counts as 1 primary. But you still will put all boot info in sda not sda1 you can read up on that at a later date. I am going to give you a Ubuntu book  in .pdf format to have around it is nice to read about Ubuntu and the instruction manual for your install.

[Main Page -]("http://ubuntuguide.org/wiki/Main_Page") 

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

