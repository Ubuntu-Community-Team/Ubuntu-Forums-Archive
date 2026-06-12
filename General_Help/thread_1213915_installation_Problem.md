---
title: "installation Problem"
date: 2009-07-15
forum: General Help
---

### Post by ctrlmd on 2009-07-15
Hi 
every-time i try to install ubuntu or any-other distribution on my drive i receive something like this 

[COLOR=Red]**linux cant be installed drive /db5 busy you need to restart your computer and try again**[/COLOR] 

and when i restart my computer to make another shot i couldn't accomplish the installation procedure   the same error acquire so  i Deleted all harddisk drives except for windows partition  and repartition + format all of them then try to install ubuntu didn't succeed same error pops out i thought there is something with distribution so i tried another one FEDORA 11 + SUSE 11.1 but i receive the same error


any idea why this happened :mad: :confused:

---

### Post by prem1er on 2009-07-15
How are you trying to install, with a Live CD wubi?

---

### Post by ctrlmd on 2009-07-15
> **prem1er said:**
> how are you trying to install, with a live cd wubi?

Normal Live CD downloaded from ubuntu website

---

### Post by cholericfun on 2009-07-15
what kind of computer do you have and what type of live-cd to go with it?

and did you try the "try out without change to disk" option at boot to see if Ubuntu is up and running from CD?

---

### Post by ctrlmd on 2009-07-15
> **cholericfun said:**
> what kind of computer do you have and what type of live-cd to go with it?

and did you try the "try out without change to disk" option at boot to see if Ubuntu is up and running from CD?

1- Desktop  3.0 p4 | 2G RAM | Motherboard Gigabyte GA-N650SLI-DS4L |nVIDIA GeForce 7300 GS | 320 G HD

2- Gnome Live CD 9.04

3- YES" i always use try out without change" on all distributions and it's running perfectly on CD

---

### Post by carml on 2009-07-15
From the live cd can you type the result of ```
df -h
``` so we can know your disk usage?

---

### Post by ctrlmd on 2009-07-15
> **carml said:**
> From the live cd can you type the result of ```
df -h
``` so we can know your disk usage?

cant restart at the moment but if you want to see disk usage here is a picture from windows  side i was trying to take the 34 G DRIVE FOR ubuntu couldn't so i reformated to ntfs 
[IMG]http://i26.tinypic.com/vrzqm8.jpg[/IMG]

---

### Post by carml on 2009-07-15
Ok,have you tried to use the manual install? So you can indicate to Ubuntu which part of the disk to use,maybe the last partition is indicated ad sda4.
It's weird you can't install because that partition  has more than strictly needed space and yuor PC seem to accomplish the needed minimum requirements.

---

### Post by prem1er on 2009-07-15
> **carml said:**
> Ok,have you tried to use the manual install? So you can indicate to Ubuntu which part of the disk to use,maybe the last partition is indicated ad sda4.
It's weird you can't install because that partition  has more than strictly needed space and yuor PC seem to accomplish the needed minimum requirements.

Yes, I also feel like you are selecting the wrong partition/drive to install to.

---

### Post by ctrlmd on 2009-07-15
> **carml said:**
> Ok,have you tried to use the manual install? So you can indicate to Ubuntu which part of the disk to use,maybe the last partition is indicated ad sda4.
It's weird you can't install because that partition  has more than strictly needed space and yuor PC seem to accomplish the needed minimum requirements.

If you mean by manual install when you select the third option on partition section 

with /    and swap area then yes i always use  this method never tried to do the Automated way

---

### Post by ctrlmd on 2009-07-15
> **prem1er said:**
> Yes, I also feel like you are selecting the wrong partition/drive to install to.
  i  can assure you that i was selecting the correct drive and i've never face a problem like this before im using ubuntu from 7.10 so its not difficult stage to install ubuntu.

---

### Post by carml on 2009-07-15
Ok let's check something else,try to burn the iso at a low speed and as someone suggest on a CD-R not a CD-RW (someone reports of possible troubles with CD-RW) and boot from that CD.

---

### Post by michy99 on 2009-07-15
Try deleting the partition and let Ubuntu install into the unused space.

---

### Post by ctrlmd on 2009-07-15
> **carml said:**
> Ok let's check something else,try to burn the iso at a low speed and as someone suggest on a CD-R not a CD-RW (someone reports of possible troubles with CD-RW) and boot from that CD.
  
i did that more than once on a DVD with 2x or 2.4x  speed even if there is something with the dvd
its not normal to have the same issue with FEDORA AND SUSE so it's not the CD

---

### Post by ctrlmd on 2009-07-15
> **michy99 said:**
> Try deleting the partition and let Ubuntu install into the unused space.

 i DID that before without any result 
[FONT=Verdana][COLOR=RoyalBlue][B]
[FONT=Arial][COLOR=Navy]ok if i have a Drive D with folders Locked with password's by using an application to lock the folders would that make a problem cause every time i try to install it's pointing to DRIVE D as the problem locating there. [/COLOR][/FONT][/B][/COLOR][/FONT]

---

### Post by carml on 2009-07-15
Try to undo that locking,but in my opinion is still strange,because the last times you didn't tell Ubuntu to use D:

---

### Post by ctrlmd on 2009-07-15
> **carml said:**
> Try to undo that locking,but in my opinion is still strange,because the last times you didn't tell Ubuntu to use D:
](*,)if couldn't find a solution i may buy a new HD for ubuntu #-o

---

### Post by carml on 2009-07-15
New idea: did you enabled encryption of the drive within Windows?
I heard that Linux is unable to read NTFS encripted partitions and that could be the reason here,that just a shot in the dark anyway.:-?

---

### Post by ctrlmd on 2009-07-15
> **carml said:**
> New idea: did you enabled encryption of the drive within Windows?
I heard that Linux is unable to read NTFS encripted partitions and that could be the reason here,that just a shot in the dark anyway.:-?

i didn't encrypt any file/folder even if i did it's not normal when you delete an NTFS Partition 
and create a  EXT4 even EXT 3  partition to install ubuntu and it give you an problem with another partition :-?


THANK YOU FOR YOUR TIME I APPRECIATED YOUR HELP 
i think im going to buy a new HD

---

