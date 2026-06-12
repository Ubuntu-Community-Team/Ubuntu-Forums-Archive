---
title: "Ask about how to restore RAID HDD form images"
date: 2012-08-26
forum: General Help
---

### Post by winnd4spd on 2012-08-26
Dear all,

My RAID box has just broken because of my mistake. I then searched online and found that the images of my RAID HDD are available.

However, when I read though it, I think that the way they used to back up and restore their HDDs is though Linux. There are 4 images ***.bz2 for 4 partitions of the HDD:

SDA_MBR_FREESPACE.bz2

SDA1_IMA.bz2

SDA2_IMA.bz2

SDA3_IMA.bz2



Cheers,

Win



Update: Local Ubuntu helped me out. I also would like to share the idea to anyone need

cd ~/ (the name of the backup file)

# Restore free space
bzip2 -cd (name sub folder for the HDD A) /SDA_MBR_FREESPACE.bz2 | dd of=/dev/sda

# Make new partitions, set correct label and flag
parted /dev/sda mklabel gpt
parted /dev/sda 'mkpart primary 528482304B 2576351231B' 'set 1 raid on'
parted /dev/sda 'mkpart primary 2576351232B 4624220159B' 'set 2 raid on'
parted /dev/sda 'mkpart primary 15728640B 528482303B' 'set 3 raid on'
parted /dev/sda 'mkpart primary 4624220160B -0' 'set 4 raid on'

# Restore MBR
bzip2 -cd (name sub folder for the HDD A)/SDA_MBR_FREESPACE.bz2 | dd of=/dev/sda bs=446 count=1

# Verify that everything still looks good.
parted /dev/sda print

# Restore partitions
bzip2 -cd (name sub folder for the HDD A)/SDA1_IMA.bz2 | dd of=/dev/sda1 bs=32M
bzip2 -cd (name sub folder for the HDD A)/SDA2_IMA.bz2 | dd of=/dev/sda2 bs=32M
bzip2 -cd (name sub folder for the HDD A)/SDA3_IMA.bz2 | dd of=/dev/sda3 bs=32M

Done the same with other bays

Note: "sda" is the location of HDD which could be changed (like C,D,E.. on windows)
If you have a problem with "permission" then use command: 
sudo su 
(your pass)
This will help you login to superuser and have the permission

---

### Post by zero2xiii on 2012-08-26
Hay,

All seems really easy.

Breakign down the commands might make more sence to you.

Essentialy what the guy did was backup everything on the drive byte for byte and then rewrote it byte for byte.

the command "dd" coppies almost anything to almost anything byte for byte. It is a VERY powerful and extremely dangerous tool.

If you are as new to linux and have little experience with low level interaction, I will HIGHLY suggest taking your computer to a store or other computer specialist that can rebuild the array for you. As doing it wrong will destroy the data beyond any recovery. Since dd coppies data byte for byte and write byte for byte, there is no way to undo an operation done by dd.

Cherz and good luck :)

---

### Post by winnd4spd on 2012-08-26
> **zero2xiii said:**
> Hay,

All seems really easy.

Breakign down the commands might make more sence to you.

Essentialy what the guy did was backup everything on the drive byte for byte and then rewrote it byte for byte.

the command "dd" coppies almost anything to almost anything byte for byte. It is a VERY powerful and extremely dangerous tool.

If you are as new to linux and have little experience with low level interaction, I will HIGHLY suggest taking your computer to a store or other computer specialist that can rebuild the array for you. As doing it wrong will destroy the data beyond any recovery. Since dd coppies data byte for byte and write byte for byte, there is no way to undo an operation done by dd.

Cherz and good luck :)

Thank zero2xiii,

The local Ubuntu community in my place helped me to slove it out

Win

---

