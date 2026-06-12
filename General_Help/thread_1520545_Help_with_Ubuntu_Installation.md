---
title: "Help with Ubuntu Installation"
date: 2010-06-29
forum: General Help
---

### Post by silentrock on 2010-06-29
Hello guys,im really new to ubuntu and ive tried to install ubuntu 10.04 to my pc previously wich resulted in a total fail and me paying $90 to a technician.

So when he formated my HD i told him to make a 80GB partition so i could install Ubuntu the right way,and now i want to install it to this parition.

My HD is partitioned in 3

Sda1-266GB (VIsta)
Sda2-80GB   (going to be ubuntu but currently empty)
Sda3-9GB     (Used to be Factory Image)


I want to go through the installation and install UBuntu 10.04 Lucid Lynx in Sda2 so i can make a Dual boot and select between Vista and UBuntu on each startup,what exactly should i do in the installation process?

What option should i choose so it installs in Sda2?
Thanks.

---

### Post by DJonsson2008 on 2010-06-29
For 25$ you could easily buy another hard drive, and simply install ubuntu onto it. Some motherboards allow you to push F12 and select what
drive you are booting from. 

I've also had success in installing Ubuntu to USB drives as small as 4GB. 

My dual boot attempts did not in the end result in stable installs,
and were fraught with problems.

I'm not an advocate of dual boot machines based on that experience, perhaps others have had more success with dual boot on the same HD, but I also see people trying to tweak dual boot issues frequently in this forum.

---

### Post by supergrav on 2010-06-29
No need to worry! During graphical installation, while you'll being asked for paritions select manual way.
After that, you will see your 80GB partition and choose it. Specify that you want "/" (your root folder) to be mounted there, choose filesystem and continue. Have in mind that you'll need a swap area.

---

### Post by silentrock on 2010-06-29
Im at mexico,this stuff is really expensive if you wnat it well done around here,otehrwise they can change your computer parts to cheaper ones.
 
So i format this partition and make it FAT32 filesystem or soemthing?
 
AND can i select Sda3(9 GB) to be the swap area? thanks.

---

### Post by nothingspecial on 2010-06-29
When you get to the partitioning bit,

choose manual (advanced)

Do not touch the vista partition

select the empty one and choose to use it as an ext4 journalling file system

choose a mountpoint of /

choose to format the partition.

Aslong as the other partition is no bigger than 3 gig and empty then it will be fine for swap.

---

### Post by silentrock on 2010-06-29
the partition is 9 gig is that ok?

---

### Post by garvinrick4 on 2010-06-29
Put your Ubuntu CD in and boot off of it. If it does not boot off of CD then go into BIOS and change to boot CD first and leave it there.
 Choose to install when boots answer the question about time, language and such. when you get to where to install choose manual.  It will ask where and you choose sda2 and then
ext4 format and / for install. It will ask if you want swap if 2 gigs of ram or more ignore if less use 2 times the amount of Ram in system for swap. continue on and pick your password and login name and such on last page 8 I believe it will have a advanced button in lower right hand corner choose sda not sda2 or sda1 but choose sda, very important to install grub (boot) in sda
  Install and when you reboot after taking Cd out you will have choice of either install of Vista or Ubuntu in a menu (grub menu). 
 Below is a pdf file on how to operate Ubuntu it is free and nice to have around.

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by silentrock on 2010-06-29
Yes im running from an USB trial and i jsut love it,its just that i want to have it the correct way wit hno problems and without affectig my HD.

SO i select sda3 which is 9 GIG as swap area? or i resize it to 3 gig? and if i do the last thing,will it afect Windows because of the partition rezising thanks

---

### Post by silentrock on 2010-06-29
OK sda3(the partition i want for swap area) is 9 GIG if i resize it to 3221 MB (around 3 gig) will it affect sda1 which is my vista partition?

---

### Post by nothingspecial on 2010-06-29
Resize it to double your ram.

Up to 3 gig (this is my personal opinion)

Then grow your empty partition into it.

9 gig is way too much for swap.

I don`t think it will harm, but it will certainly be wasted drive space.

---

### Post by supergrav on 2010-06-29
It won't affect sda1. You may add the rest (approx.) 6GB left to sda2.

---

### Post by nothingspecial on 2010-06-29
Oh, and 
[SIZE=4][COLOR=Red]

Back up anything you don`t want to loose[/COLOR][/SIZE]

[SIZE=6][COLOR=Red]Right now[/COLOR][/SIZE]

before you do any more partition editing.

---

### Post by silentrock on 2010-06-29
OK i sda2 is now ext4 

and sda3 was resized to 4000 MB (4 GIG) 

that wont affect Vista right?

---

### Post by silentrock on 2010-06-29
darn too late,WILL IT AFFECT MY PC??!?

---

### Post by nothingspecial on 2010-06-29
> **silentrock said:**
> darn too late,WILL IT AFFECT MY PC??!?

Just back your files up.

Whatever you do to your pc can be fixed

If you loose your stuff, it`s possible but not pretty, and can be expensive., but it is not
definite .

YOU SHOULD HAVE BACKUPS ANYWAY 
 
Don`t panic.

---

### Post by silentrock on 2010-06-29
I have my important files backed up,i just want to know if i may proceed to the installation without ruining my PC and resulting in a" NO such device #######

grub rescue>" error which was the problem that made me take it to the technician 
am i clear to proceed without afecting sda1 ( Vista)?

---

### Post by nothingspecial on 2010-06-29
Never, in my experience.

Over 50 linux installs

---

### Post by silentrock on 2010-06-29
OK i proceeded with the installation,hope i dont have to spend anotehr $90   :S

---

### Post by silentrock on 2010-06-29
is this normal? 

> If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted

also im not able to see the other installation parameters

---

### Post by nothingspecial on 2010-06-29
> **silentrock said:**
> is this normal? 



also im not able to see the other installation parameters

It is nomal.

What do you mean,  by other installation parameters

---

### Post by silentrock on 2010-06-29
the other installation settings,so thanks i may now proceed and hope that i dotn get that error that almost made me pee on my pants.

---

### Post by silentrock on 2010-06-29
Thanks nothingspecial the installation is going to end soon(96%) and i htinkits going to be a succesful install this time :P

---

### Post by silentrock on 2010-06-29
Succesful installation,thanks for your support guys im so happy :D

---

