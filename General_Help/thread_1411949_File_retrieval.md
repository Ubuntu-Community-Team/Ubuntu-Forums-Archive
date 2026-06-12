---
title: "File retrieval"
date: 2010-02-20
forum: General Help
---

### Post by AndyWhite87 on 2010-02-20
Hello,

Just bought a laptop with windows 7 on it so i downloaded ubuntu. I have them as a partition so i can still access windows 7. Was just wondering if i could access the files on the windows 7 partition and cut them to ubuntu? Just loads of music i wanna get over as only got usb stick.

cheers

---

### Post by SuperSonic4 on 2010-02-20
Yes, you can do that without a problem.

Remember that windows cannot read ext* natively and cannot read ext4 at all so you may be better off creating an NTFS data partition and set it to mount at boot in ubuntu

---

### Post by gsparky2004 on 2010-02-20
Open a terminal (Applications -> Accessories -> Terminal) and type the following:
```
sudo fdisk -l
```
Then copy and paste the results back to here.

---

### Post by howefield on 2010-02-20
Ubuntu should be able to read your Windows file system just fine, but Windows won't be able to access your Ubuntu system without third party software.

---

### Post by AndyWhite87 on 2010-02-20
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          24      192748+  de  Dell Utility
/dev/sda2              25        1330    10485760    7  HPFS/NTFS
/dev/sda3   *        1330       14267   103918588    7  HPFS/NTFS
/dev/sda4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown

---

### Post by gsparky2004 on 2010-02-20
Based on the "fdisk -l" output, if you want to access your Win7 files *for just one Ubuntu session* (meaning from the time you turn it on til you turn it off), then use the following commands in the terminal:
```
sudo mkdir /media/sda2
sudo mkdir /media/sda3
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda3 /media/sda3
```
From this point, you *should* be able to access the files on the NTFS partitions.  Now, if Win7 is anything like Vista, then you'll find your music under "/media/sda3/Users/(your username on Win7)/Music".  I suggest just opening "Places -> Computer", selecting "Filesystem" on the left, then start drilling down starting at "/media", then to "sda3".  
If you want to make this permanent, meaning that those two partitions are mounted automatically every time you start Ubuntu, then you need to do the following:
1)  Open your /etc/fstab file for editing
```
sudo gedit /etc/fstab
```
2)  Add the following two lines to the end of the file:
[B]/dev/sda2 /media/sda2 ntfs nls=iso8859-1 0 0
/dev/sda3 /media/sda3 ntfs nls=iso8859-1 0 0[/B]
3)  Save the file and exit the text editor
4)  Restart your system. 
One last comment.  howefield is exactly correct that this will only allow Ubuntu to read your Win7 files.  **Win7 will not allow you to read your files on your Ubuntu partition without special software to do so.**  Why?  Because they're Microsoft, that's why.  If you're not NTFS, that means you're not part of their Borg.  Which means it's ignored.
Please let me know if this works for you.

---

### Post by howefield on 2010-02-20
Have you tried simply going to the Places menu and selecting your Windows partition ?

It may be listed as "50 GB Filesystem" or something similar like that. I labelled my Windows partition "Windows", so that's what I see when I go to the places menu.

Not sure you have to go through the above for a Windows file system ?

---

### Post by AndyWhite87 on 2010-02-20
Thank you very much!

Ive managed to access the files for this one time use, im just copying the files i want onto my desktop for the time being.

I hope this will copy them permanently as I am wanting to get rid of the windows 7 partition.

---

