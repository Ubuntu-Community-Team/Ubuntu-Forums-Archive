---
title: "Windows killed UBUNTU!"
date: 2011-07-18
forum: General Help
---

### Post by leilei1 on 2011-07-18
So I originally had an Ubuntu partition on my hard drive which occupied about half of it. I installed Windows 7 in the remaining unallocated space and I was planning on doing a grub update from a live cd afterwards. BUT when I looked at my partition table, the space where the ubuntu partition used to be is now unallocated space!! PLZ help!

---

### Post by peter d on 2011-07-18
Windows will not recognize your Ubuntu partition - it cannot read ext3 or 4 filesystems.

Suggest you insert the live CD and check that you can see the Ubuntu partition and work on Grub from there.

---

### Post by Cybie257 on 2011-07-18
As suggested, use the LiveCD or even try using EXT2FSD ([http://www.ext2fsd.com/](http://www.ext2fsd.com/)), which will allow read/write, VIA Windows, on Ext through Ext4 Linux partitions. (Latest Version test and tried and works)


But, if you say that windows is reporting 'Unallocated Space' rather than just a nameless partition (Healthy Partition), it is likely that the partition was deleted. Using a LiveCD and some tools, you should be able to recover your Linux Install, so don't overwrite until you seek the tools necessary to fix/recover your partition. There is one Linux tool that I know does a great job recovering partitions, but I can't seem to recall the name at this time, but there is hope. :)

-Cybie

---

### Post by seawolf167 on 2011-07-18
Echoing the above posts, simply [download ]("http://www.ubuntu.com/download/ubuntu/download")and boot off a Ubuntu LiveCD. Once in the live environment, you can open the disk manager or GParted to view your partitions. Once you do this you can see if your partition has indeed been erased.

If it has not, you can [reinstall Grub ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")(which a Windows install **will **overwrite), and then once booted back into Ubuntu, simply update grub to search for other installations.

```
sudo apt-get install os-prober
sudo update-grub
```

---

### Post by leilei1 on 2011-07-19
So I did something really bad. I tried rewriting the filesystem to the partition and none of my files showed up. So I am currently using photorec to retrieve my files. The only thing is that its also grabbing a bunch of ubuntu os files along with them so I have a bunch of extra files to sort through once its finished. Is there a way to repair this or do I have to scroll through 1 million and counting files?

I know this was very stupid but I was panicked and I just screwed everything up.

Okay photorec just finished and the files that cae up were a buch txt files with code and a bunch of pictures from the internet. Are all of my files now gone?

I should also say that I first ran testdisk on my hard drive and it found the partition saying that the file system was damaged when I pressed p to view the files. So I rewrote the partitions it found but I couldn't access it. So I figured if I rewrote the file system it would fix it but when I did that none of my files appeared. so I just ran photorec and it recovered over 1,200,000 files. So I would have to sort through all of them and I don't even know if all my files are there. Is there a way to recover my file system? I tried running fsck but that didn't do anything. I have no idea as to what I should do at this point. Also testdisk and photorec see the partitions but when I run gparted it shows my entire hard drive as unallocated. Yet I can mount the windows partition and the ubuntu partition(which was rewritten with a new filesystem as stated before) so they are there but they don't appear on gparted.

---

### Post by leilei1 on 2011-07-20
So I take it I have to sort through the photorec output.

---

