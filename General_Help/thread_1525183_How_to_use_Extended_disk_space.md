---
title: "How to use Extended disk space"
date: 2010-07-06
forum: General Help
---

### Post by umakanth on 2010-07-06
My HDD is 500GB

Master Boot 20 GB ext4  **Devise**: /dev/sda1 **Mounted a**t /.

Extended 180 GB             **Devise**: /dev/sda2
     4 GB  Swap Space       **Devise**: /dev/sda5
  100 GB   ext4                 **Devise**: /dev/sda6 **Mounted at** /usr
    76 GB    ext4                **Devise**: /dev/sda7 **Mounted a**t /tmp

    100 GB ext4                  **Devise**: /dev/sda3 **Mounted at** /media/New Volume

Now my Q?
my 20 GB ext4 is full
how to save file in 100 GB ext4 and 76 GB ext4
and move some file to 100Gb area
how i go to usr and tmp area

Thx
Umakanth

---

### Post by pedro_orange on 2010-07-06
Copy files from your / to whichever place you want.
You can do this in Nautilus or using cp

```
cp /path/to/files /path/to/big/empty/drive
```

You can get to the /usr /tmp folder by going to the top root directory / (Like C:/) and you can see it there.

---

### Post by umakanth on 2010-07-06
> **pedro_orange said:**
> Copy files from your / to whichever place you want.
You can do this in Nautilus or using cp

```
cp /path/to/files /path/to/big/empty/drive
```

You can get to the /usr /tmp folder by going to the top root directory / (Like C:/) and you can see it there.
Hi prdro_orange
thk for your help
good job 

how to use this code I am new user for ubuntu

---

### Post by pedro_orange on 2010-07-06
Well if you're familiar with Windows, open Nautilus. (It's the default file browser within Ubuntu) - Just go to Places > Home. 

If you keep hitting the "Up" arrow you will arrive at /, which is the root (read: top) of the file system. You should see /temp and /usr from here. 

You can simply drag and drop files from this browser.

Or, you can use the terminal command I gave you in my previous reply. Applications > Accessories > Terminal (I think....I'm at work, can't remember)

---

### Post by pedro_orange on 2010-07-06
Also...I wouldn't recommend you use /tmp, I would have thought that this folder would be used by a lot of applications and so on as a temporary directory. Perhaps you're better off having your home directory (or another directory that has a lot of data in) on a separate, larger partition

---

### Post by umakanth on 2010-07-06
> **pedro_orange said:**
> Well if you're familiar with Windows, open Nautilus. (It's the default file browser within Ubuntu) - Just go to Places > Home. 

If you keep hitting the "Up" arrow you will arrive at /, which is the root (read: top) of the file system. You should see /temp and /usr from here. 

You can simply drag and drop files from this browser.

Or, you can use the terminal command I gave you in my previous reply. Applications > Accessories > Terminal (I think....I'm at work, can't remember)


[URL="https://docs.google.com/present/edit?id=0Ada4Oln04oNuZGttN2t2d18xOW42cXZwY3A&hl=en&authkey=COe-uIIL"]https://docs.google.com/present/edit?id=0Ada4Oln04oNuZGttN2t2d18xOW42cXZwY3A&hl=en&authkey=COe-uIIL
[/URL] 
Master Boot 20 GB ext4  **Devise**: /dev/sda1 **Mounted a**t /.

Extended 180 GB             **Devise**: /dev/sda2
     4 GB  Swap Space       **Devise**: /dev/sda5
  100 GB   ext4                 **Devise**: /dev/sda6 **Mounted at**  /usr
    76 GB    ext4                **Devise**: /dev/sda7 **Mounted a**t  /tmp

    100 GB ext4                  **Devise**: /dev/sda3 **Mounted at**  /media/New Volume [COLOR=Red][B]shown in RED line ( this 100GB mount like EXT Disk) but is part of the 500GB 
[COLOR=Black] can i do for 
usr (100 GB) & tmp (76 GB) folder like this How?[/COLOR]

Thx for your HELP
[/B][/COLOR]

---

### Post by Cavsfan on 2010-07-06
Don't mean to butt in, but when I initially setup Ubuntu up I also set up several different partitions for everything.
I found that I was in the same situation you are finding yourself in.
So, I set my swap to twice my RAM 4GB (1024 x 8 - 8072) and the rest of the partition to
"/" EXT4. 
That way it all handles itself. I have 100GB setup for both swap and EXT4 and the rest I dual boot win 7.

I find I am using under 20GB for everything in Ubuntu.
(just my 2 cents)

---

### Post by umakanth on 2010-07-06
> **cavsfan said:**
> don't mean to butt in, but when i initially setup ubuntu up i also set up several different partitions for everything.
I found that i was in the same situation you are finding yourself in.
So, i set my swap to twice my ram 4gb (1024 x 8 - 8072) and the rest of the partition to
"/" ext4. 
That way it all handles itself. I have 100gb setup for both swap and ext4 and the rest i dual boot win 7.

I find i am using under 20gb for everything in ubuntu.
(just my 2 cents)
thx

---

### Post by Cavsfan on 2010-07-06
> **umakanth said:**
> thx

You are very welcome! :D

---

### Post by warfacegod on 2010-07-06
> **Cavsfan said:**
> Don't mean to butt in, but when I initially setup Ubuntu up I also set up several different partitions for everything.
I found that I was in the same situation you are finding yourself in.
So, I set my swap to twice my RAM 4GB (1024 x 8 - 8072) and the rest of the partition to
"/" EXT4. 
That way it all handles itself. I have 100GB setup for both swap and EXT4 and the rest I dual boot win 7.

I find I am using under 20GB for everything in Ubuntu.
(just my 2 cents)

Does that include your personal files or no. If not then your install is way too big even accounting for that 8 GB swap (which is also rather large).

My current install, including swap which is 0 MB, is 2.5 GB. Unless I'm reading your post incorrectly, your install is roughly 5 times bigger than mine.

---

### Post by Cavsfan on 2010-07-06
> **warfacegod said:**
> Does that include your personal files or no. If not then your install is way too big even accounting for that 8 GB swap (which is also rather large).

My current install, including swap which is 0 MB, is 2.5 GB. Unless I'm reading your post incorrectly, your install is roughly 5 times bigger than mine.

Yes, that includes everything.  I was told whatever your RAM size is to double that for your SWAP.
Since I have 4GB actual RAM and 1024MB is a GB I have 8072MB for SWAP and the remaining 90 something GB 
is available for Ubuntu to use. Music, Videos, Pictures, etc. 
I do not feel 100GB is that big. Although I haven't used 1/3 of it so far, but my camera puts out 12 Meg pixel  
pictures (4000x3000 pixels). That and the AVIs it takes could eventually take up a lot of room. 
I like to prepare for the future. I have a 500GB HD that Ubuntu uses and the rest is used by Windows 7 (resource hog)!
Also have a 1TB Phantom Green USB drive I backup to. It was only about $69.
My whole system was ~$1000 plus the 1TB drive and the wireless router.

We don't write checks and everything is paid via the internet. We keep track of our bank accounts and bills. 
Therefore if I lost this system, I would scrogged!
So, I try to go a little overboard, which I don't really think I am doing. I wish I had a
RAID setup or some other redundant backup.

---

### Post by warfacegod on 2010-07-06
No, no. 100 GB isn't that big at all. From the wording your previous post it sounded like just your OS was taking up 12 GB. 20 with the 8 GB swap. 

That double your RAM for swap size is long outdated info. with todays hardware swap is only really necessary for Hibernating in which case it only needs to be slightly bigger than RAM. Video encoding can also be swap intensive but double still generally isn't necessary.

---

### Post by umakanth on 2010-07-07
in 20 GB oracle VM virtualbox Windows XP  10 GB and 2 GB Ubuntu 7 GB my files 
now i moved 7 GB to 100 GB new Pat..

Processors  **AMD Phenom(tm) II X4 **965 Processor 
Motherboard **GIGABYTE MA785GMT-UD2H**
RAM **2GB DDR3 1666**+
**500 GB HD**
**Sony DVD RW**
**WD 1 TB **USB EXT HDD
**SAMSUNG 80 GB** USB EXT HDD
**Seagate *80 GB*** USB EXT HDD
**Transcend 60 GB** mini USB EXE Disk

can i update like this

Now i am add 2 x 3 = **6 **GB RAM... T ...  6 + 2 = **8 GB**
so double my RAM for swap size  16 GB

500 GB 

300 for /.                                                     .............60 % for OS                                 
              ubuntu 150 GB
               oracle VM virtualbox Windows XP  150 GB
100 GB for file my file                                  .............20 % for working file bakup
100 GB Free                                                .............20 % for Emg


in 2 month time i want to move out of windows and 100 % ubuntu
thx for u r help 

with your help i can move to ubuntu 100% in two month time

---

