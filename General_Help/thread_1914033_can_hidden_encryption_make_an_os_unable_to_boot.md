---
title: "can hidden encryption make an os unable to boot?"
date: 2012-01-23
forum: General Help
---

### Post by cybernetic toaster pastry on 2012-01-23
I have Ubuntu 10.04 and Win7 ultimate on their own partitions, roughly 50/50 of the HDD.
I was considering using Truecrypt to encrypt the entire Windows partition. Thats easy enough. Where I'm concerned is I want to make it a hidden encrypted partition (why do it otherwise).
Simply put, If I make it hidden will I still have the Windows 7 Loader in my boot menu? I don't want to make it hidden if it becomes inaccessible in the boot menu. I ask because on Truecrypt's website it says it is as if the OS doesn't exist.

---

### Post by cryptotheslow on 2012-01-23
> **cybernetic toaster pastry said:**
> Where I'm concerned is I want to make it a hidden encrypted partition (why do it otherwise).

That would depend on what you are trying to achieve. It's often enough just to encrypt and not hide e.g. if the aim is to stop unauthorised access to your files should your laptop / PC be stolen (assuming it is powered off!). Sure the encrypted volume can be seen but there's no way into it without the passphrase / key.

Clearly if your laptop is stolen or accessed while powered on then it's game over as the volume will already be mounted and accessible.

I've no answer to the rest of your question as I've never tried it.

---

### Post by xyzzyman on 2012-01-23
Then you aren't making a hidden Windows install, just encrypted. It's tricky to get dual-boot working with truecrypt. I wound up encrypting my Windows 7 partition, reinstalling grub2 to /dev/sda, and adding the rescue ISO it makes for the partition to my grub2 loader. The normal ISO booter didn't work so I found something that used a memdisk file and this is the entry in my 40_custom file:

```
menuentry "Microsoft Windows 7" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
linux16 ($root)/boot/memdisk iso raw
initrd16 ($root)/boot/truecrypt.iso
}

```

---

### Post by cybernetic toaster pastry on 2012-01-25
Seems a bit more than I want to get into at this time. I am in the process of repairing a couple computers for clients as well as developing a website for a publisher who's a friend of the family. All while working 45hrs at my regular job. Not a whole lot of free time on my hands these days for testing. Thank you for your time and help. I will most likely attempt your method sometime, [xyzzyman]("http://ubuntuforums.org/member.php?u=44719"). 
I believe you have helped me before but I can't remember what thread. Also xyzzy is a reference to Stone Sour, correct?

---

### Post by xyzzyman on 2012-01-25
[http://en.wikipedia.org/wiki/Xyzzy](http://en.wikipedia.org/wiki/Xyzzy)

---

### Post by cybernetic toaster pastry on 2012-01-25
Ah, I misread it and got confused with zzyzx rd by Stone Sour.

---

