---
title: "accidentily overwrote windows and other things"
date: 2010-02-19
forum: General Help
---

### Post by theedyeah on 2010-02-19
Hey everyone, first time posting here, but i have been using these boards for a while now for my problems.

I just did something that is moderately serious in my book.

while trying to put a iso/img to a USB drive using "dd" command (actual command: "dd if/=/home/<username>/Desktop/<image file name> of/=/dev/sda1"), I accidentally wrote to /dev/sda1 (which is my windows partition on this dual booted computer). When i try to boot into windows, it gives a error that it cannot find the parition. the iso was about 400meg, it was a install iso for another form of linux (arch linux).

Is there anyway that I can get my windows partition to work again, or am i just going to have to say goodbye to all my music, pictures, etc. And I think some of my teachers require me to use windows based software... So I would like to eventually get back into windows though.

I am running Ubuntu 9.10, I am on a laptop (HP HDX 16t)

I am going to get ubuntu back onto my netbook (i destroyed that earlier tonight by deleting a partition that had the bootloader on it... i am just wiping that though)

---

### Post by uRock on 2010-02-19
If you are dual booting can you mount that partition and copy files or boot a LiveCD and copy files to a thumb drive?

---

### Post by theedyeah on 2010-02-19
I currently cannot mount my harddrive and get to my windows files. I cannot see the hard drive when i go to computer.

All I have are:
cd/dvd drive
4gig usb stick
filesystem

I think i overwrote the partition's information when i used the dd command and did it to sda1

---

### Post by uRock on 2010-02-19
It may be possible to retrieve files. Hopefully someone will soon come along with good instruction. Sorry I can't help.

---

### Post by theedyeah on 2010-02-19
after i click my windows partition in grub:
error: no such device: 05bc835340db69d4

Press any key to continue...

I will keep trying to figure it out while "doing" homework.

---

### Post by wilee-nilee on 2010-02-19
If you install gparted in Ubuntu it will let you look at the partitions to see what is still there. You can reload a MS bootloader to get back the MS then reload grub to offer either distro on boot, what MS was it? and do you have the install or a recovery disc.

---

### Post by theedyeah on 2010-02-19
so I got gparted and this is what it says:
/dev/sda1 (caution flag) file system: unknown, size 283 gigs used unknown unused unknown flags boot

the partition is there, I just cannot access it from ubuntu or boot to it.

I assume that most of the data was still there, and I had(have?) windows 7 ultimate 64bit

My fear is that i overwrote a lot of the windows files that were at the beginning of the drive and that it also overwrote any of the bootables. I assume getting my install disk out and putting it in would fix it, but that is in Chicago and I am in Minneapolis for school...

---

### Post by uRock on 2010-02-19
> **theedyeah said:**
> so I got gparted and this is what it says:
/dev/sda1 (caution flag) file system: unknown, size 283 gigs used unknown unused unknown flags boot

the partition is there, I just cannot access it from ubuntu or boot to it.

I assume that most of the data was still there, and I had(have?) windows 7 ultimate 64bit

My fear is that i overwrote a lot of the windows files that were at the beginning of the drive and that it also overwrote any of the bootables. I assume getting my install disk out and putting it in would fix it, but that is in Chicago and I am in Minneapolis for school...

If you have a burner, then you can download the repair iso for Windows 7 and run it.

---

### Post by aysiu on 2010-02-19
> **iRock said:**
> It may be possible to retrieve files. Hopefully someone will soon come along with good instruction. It's very possible. Instructions here:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by uRock on 2010-02-19
> **aysiu said:**
> It's very possible. Instructions here:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

I love your site. It should come added into firefox's bookmarks with the mozilla pages at install.

---

### Post by theedyeah on 2010-02-19
update:

Downloaded a windows repair iso and burned it. It claims that nothing can be done.

...

I will try recovering the files, but i do not know what files i erased, and its not my files i necessarily want... i want to boot back into windows, and if i erased/overwrote the boot files, then i feel like i am up a creek without a paddle...

still fiddling.

---

### Post by lidex on 2010-02-19
You should probably follow [aysiu's]("http://ubuntuforums.org/showpost.php?p=8849292&postcount=9") advice to salvage your data then just re-install windows.

---

### Post by theedyeah on 2010-02-19
I am currently recovering the files, but am still trying to find a way to not need to use them. 

Trying to find a way a way to get into that partition is going to be rough.

---

### Post by theedyeah on 2010-02-19
I am currently trying to re-set up the partition manually using gpart and gparted tools, and hopefully i might be able to re-write the partition tables / bootable files that are needed for my windows partition. or if i set-up the partition for windows again, maybe the boot CD will recognize the partition and repair it.

---

### Post by uRock on 2010-02-19
If you have to reinstall, you will lose all of your data in that partition. I am sorry to hear that the repair disk didn't work. I guess it was worth a shot.

---

### Post by spandey on 2010-02-19
I almost did similar things a week before and was able to recover using systemrescuecd  ([http://www.sysresccd.org/](http://www.sysresccd.org/)) and Testdisk in it.  Usually it works great if you have not written anything to disk. 

Regards,
Pandey

---

