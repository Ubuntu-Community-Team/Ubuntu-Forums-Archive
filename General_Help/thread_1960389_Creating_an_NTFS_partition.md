---
title: "Creating an NTFS partition"
date: 2012-04-17
forum: General Help
---

### Post by QQQ6 on 2012-04-17
This may seem complicated, but I'll try to explain the problem the best I can:

I have an HDD with Ubuntu 11.10 and I want to create an NTFS partition that will be accesible when I connect the drive as a slave in another computer that runs Windows 7. I want the Linux HDD to remain bootable just like it is now.

Will that work? I'm a complete noob when it comes to Linux. I googled a bit and learned about (and installed) Gparted, but I don't want to touch anything because I don't want to screw this up.

This is what it looks like at the moment:

[http://img194.imagevenue.com/img.php?image=684725361_IMG_0929_122_165lo.JPG]("http://i106.photobucket.com/albums/m273/voidhead/IMG_0929.jpg")

---

### Post by cortman on 2012-04-17
GParted is the tool you need. It's very user friendly and easy to understand. Go ahead and install it-

```
sudo apt-get install gparted
```

I can't get to the image you posted, but you can instantly create a NTFS partition from any unallocated space you have on your HDD.
If there isn't any space on the HDD, you will need to boot from a live CD and shrink your Ubuntu partition to make extra space.

---

### Post by codemaniac on 2012-04-17
gpated comes bundled with the Ubuntu live/installation cd .Just pug and play with your partitions .I would suggest gui based partitioning tools like gparted over CLI partitioning tools like fdisk .Here is a tutorial on gparted .[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Mark Phelps on 2012-04-17
I'm presuming you want to get space from the Ext4 partition.

If that is true, since you can't change a partition currently in use, you can't do this from inside Ubuntu while it's running.

Instead, boot from an Ubuntu desktop CD, select the Try Ubuntu option, run GParted -- and use that.

---

### Post by QQQ6 on 2012-04-17
I changed the link in the original post. 

I'm posting the image because I don't want to screw this up.


> **Mark Phelps said:**
> I'm presuming you want to get space from the Ext4 partition.

Yeah, I guess that's the case.

> If that is true, since you can't change a partition currently in use, you can't do this from inside Ubuntu while it's running.

Instead, boot from an Ubuntu desktop CD, select the Try Ubuntu option, run GParted -- and use that.I used a CD with **ubuntu-11.10-alternate-i386** to install Ubuntu. Can I boot from that instead of the desktop one?

---

### Post by Mark Phelps on 2012-04-18
> **QQQ6 said:**
> I used a CD with **ubuntu-11.10-alternate-i386** to install Ubuntu. Can I boot from that instead of the desktop one?
I don't remember if the alternate CD includes GParted by default; the desktop CD does.

Boot using the alternate CD.  Try running GParted. If it says something like "not found", then use the Software Center to install it.  The app is named the GNome Partition Editor (G..Part..Ed).

---

### Post by codemaniac on 2012-04-18
> **QQQ6 said:**
> 
I used a CD with **ubuntu-11.10-alternate-i386** to install Ubuntu. Can I boot from that instead of the desktop one?

Not sure but i have tried with the desktop one .

---

### Post by Cheesemill on 2012-04-18
> **QQQ6 said:**
> I changed the link in the original post. 

I'm posting the image because I don't want to screw this up.




Yeah, I guess that's the case.

I used a CD with **ubuntu-11.10-alternate-i386** to install Ubuntu. Can I boot from that instead of the desktop one?

No, you need to used a Live CD (for example ubuntu-11.10-desktop-i386.iso).

---

