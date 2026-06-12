---
title: "Please Reply ASAP Dual boot installation"
date: 2010-12-21
forum: General Help
---

### Post by sherbieny on 2010-12-21
I have a 320 HDD with Windows XP on a 50GB partition and two other 170GB and 70GB partitions I want to install ubuntu on the 70GB partition (ALL OF IT), I used a flash disk to run ubuntu and now I'm stuck with the choises of erasing the hard disk, install with windows, and manually partition what should I choose

or should I just install using wubi from windows and choose the whole 70GB partition as its size??

please reply ASAP

---

### Post by VCoolio on 2010-12-21
Choose manually, choose the 70 GB one to format to ext4 (if you didn't already) with mount point / (that's a single slash, "/"). Leave the rest alone. Consider splitting the 70 Gb into 10 for / and 60 for /home, so you can do a fresh install without having to backup your user stuff, files etc first.

Addition: lf you want to automatically have the other partitions available too, you can edit the file /etc/fstab later. Google fstab or search these forums and you'll find plenty howtos, it's quite easy.

---

### Post by Verbeck on 2010-12-21
if you select manually
then atleast 10 gb for /
type=swap   size=same size as ram <-----(the installer would complain if its not there)
the rest as /home

(file system type as ext4 would be fine)

---

### Post by sherbieny on 2010-12-21
Thanks for the fast reply :)

so, how to make the partition (in my case dev/sda3) into / and /home and others if I want 

when I choose the partition and click change it takes me to "edit a partition" panel where there is no place to divide the partition

or should I choose new partition table?

also is these steps will make a dual boot menu when I reboot?

and what to choose in the boot loader?

---

### Post by VCoolio on 2010-12-21
If you're on the live cd you can use gparted for splitting the partition; I don't know about the installer without seeing it before me. Don't worry about grub (the boot loader), that's automatic and you'll know what to choose. It will look like:

some-ubuntu-line-here
some-ubuntu-line-here (fallback)
windows

The fallback is for when something is wrong; it will boot with some basic options.

---

### Post by drewsus on 2010-12-21
> **Verbeck said:**
> if you select manually
then atleast 10 gb for /
type=swap   size=same size as ram <-----(the installer would complain if its not there)
the rest as /home

(file system type as ext4 would be fine)

Just to confirm, this is what you do **EXCEPT** make your swap partition 2x the size of your ram if you want to be able to suspend/hibernate. 

Assuming you have 2GB RAM (adjust swap partition accordingly to be 2 times your RAM):

10GB "/" ext4 partition at the beginning of the 70GB Partition.
4GB "swap" at the end of the 70GB partition.
56GB (remainder) "/home" ext4 partition using the left over space from the 70GB partition.

Remember: 1GB=1024MB. Use the calculator in the live CD.

Furthermore, since you are new to this, I would recommend you backing up your information on the other partitions first....

---

### Post by VCoolio on 2010-12-21
This may help: [https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning). I'm off to bed now. Have fun.
Also, twice RAM for SWAP is too much imo; if you have few RAM, add half, so swap = 1,5 ram. If you have more than 1Gb ram I think swap=ram should suffice. But opinions on these matters differ.

---

### Post by sherbieny on 2010-12-21
> **drewsus said:**
> Just to confirm, this is what you do **EXCEPT** make your swap partition 2x the size of your ram if you want to be able to suspend/hibernate. 

Assuming you have 2GB RAM (adjust swap partition accordingly to be 2 times your RAM):

10GB "/" ext4 partition at the beginning of the 70GB Partition.
4GB "swap" at the end of the 70GB partition.
56GB (remainder) "/home" ext4 partition using the left over space from the 70GB partition.

Remember: 1GB=1024MB. Use the calculator in the live CD.

Furthermore, since you are new to this, I would recommend you backing up your information on the other partitions first....

I just got this hard-drive so there is nothing except the XP windows

anyway I'm on the menu in the picture now, so what to choose Do I choose a new partition table or what?

---

### Post by Verbeck on 2010-12-21
> **drewsus said:**
> Just to confirm, this is what you do **EXCEPT** make your swap partition 2x the size of your ram if you want to be able to suspend/hibernate. 

???
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
> 
Also, it's recommended that the swap space is twice the amount of  physical memory (RAM) depending upon the amount of hard disk space  available for the system (although this "recommendation" dates back from  a time when physical RAM was very expensive and most Unix systems ran  with many processes in swap space - a situation that hardly applies in  most situations these days, but ancient Unix/Linux myths like this  "recommendation" tend to survive well past their "use by" dates)

> 
High RAM and high disk space With 2 GB RAM and 100 GB hard disk, use 2 GB for  swap since hard disk space is plentiful.

---

### Post by VCoolio on 2010-12-21
Select the /dev/sda3 line in the middle, hit change, create three partitions, one 10 Gb type ext4, one whatever size, type swap, one the rest, type ext4. Then back in this screen, for 10 Gb mount point /, for the rest mount point /home, for the swap use as swap, no mount point.

---

### Post by sherbieny on 2010-12-21
Please someone tell me how to divide the partition
and what to choose in boot loader

about the swap I have 4GB RAM

---

### Post by sherbieny on 2010-12-21
thanks for the clear reply

but when I enter 10GB and click ok I get the message in the picture so should I continue or what?

---

### Post by VCoolio on 2010-12-21
Don't change the bootloader option. What 'previous changes' did you do during installation? If nothing you recall, just continue. Resizing will take some time, but then adding the others to the empty space will take just seconds. Now I'm really off to bed.

---

### Post by drewsus on 2010-12-21
@Vcoolio and Verbeck:
Exactly as I said, if you want Hibernation to work, your swap should be 2x your RAM. It is not required if you do not want to be able to do that. I really don't care what the FAQ that you linked to says. Just read all the posts out there about hibernate not working. All the solutions are to make your swap 2x your RAM. Why not save the hassle? If your SWAP is not large enough to take all your RAM, it doesn't make sense that hibernate would work. Be safe, make it 2x your RAM. 

As for the rest sherbieny I cannot help further, I have a calc exam tomorrow. Sorry.

---

### Post by ram2500 on 2010-12-21
I think for Wubi, the maximum install is 30GB. If you did decide to go the Wubi route, I would *not* install Wubi on the same partition as Windows, as it will essentially have a 5-30 GB file sitting in the partition, which wouldn't be good speed-wise. In other words, create a blank partition to hold the Wubi install, and be sure to install it there. 

I also recommend creating a "common" partition, about 50 GB or so, that holds your data, so that it can be accessed from Windows and Ubuntu. Of course, you can access the files from the Windows partition, and with a little work, from the Ubuntu partition (non-Wubi), but it is so much easier to just have your files right at hand instead of having to drill down to your home or user folder to get to your files.

---

