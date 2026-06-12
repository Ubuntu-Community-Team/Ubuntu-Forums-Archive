---
title: "reformat"
date: 2012-04-13
forum: General Help
---

### Post by saskatchewan on 2012-04-13
Hi

I recently purchased an ASUS U31s with an intel core 13-2330 m.

It has windows 7 and two partitions.  I would like to remove Windows and install ubuntu and retain two partitions.  One for data and one for running the os.

Can anyone help me?

I have Ubuntu on the smaller partition.  I tried using killdisk to get rid of windows but it is an older version of killdisk so I could not get it to work.

---

### Post by Lemuriano on 2012-04-14
Hi,

From the live cd or usb go to gparted and work from there. Backup your data if any.

---

### Post by r-senior on 2012-04-14
You get this option in a standard install. There will probably be three options that come up:

1. Install Ubuntu alongside Windows
2. Install Ubuntu on the whole disk
3. Something else

If you choose the third option, you get to partition the disk however you want. It will show you the existing partitions and you can clear those out and use those. Or you can remove those partitions completely and start from scratch.

For OS and data partitions, you'd create three partitions:

1. Root partition, ext4 filesystem, mounted as /
2. Data partition, ext4 filesystem, mounted as /home
3. Swap partition

12-20GB is a decent size for a root partition (a 12.04 vanilla install uses 4-5GB but then there's room for more programs). A good rule of thumb for swap is twice your memory size up to a a total of 4GB. If you want the machine to hibernate, the swap needs to be larger than your memory. Then allocate the rest to your data partition.

It feels awkward the first time you do it but it's quite a simple process.

Obviously everything that was on the disk is lost when you do this.

---

### Post by Nytram on 2012-04-14
I'd recommend creating a 3rd partition for Swap (virtual memory.)

---

### Post by saskatchewan on 2012-04-14
> **r-senior said:**
> You get this option in a standard install. There will probably be three options that come up:

1. Install Ubuntu alongside Windows
2. Install Ubuntu on the whole disk
3. Something else

If you choose the third option, you get to partition the disk however you want. It will show you the existing partitions and you can clear those out and use those. Or you can remove those partitions completely and start from scratch.

For OS and data partitions, you'd create three partitions:

1. Root partition, ext4 filesystem, mounted as /
2. Data partition, ext4 filesystem, mounted as /home
3. Swap partition

12-20GB is a decent size for a root partition (a 12.04 vanilla install uses 4-5GB but then there's room for more programs). A good rule of thumb for swap is twice your memory size up to a a total of 4GB. If you want the machine to hibernate, the swap needs to be larger than your memory. Then allocate the rest to your data partition.

It feels awkward the first time you do it but it's quite a simple process.

Obviously everything that was on the disk is lost when you do this.
Thanks!!  I will give that a try!!

---

### Post by saskatchewan on 2012-04-21
Hi

I still can't get it to boot from my external DVD burner.  Is there a way I can get at that by pressing one of the F keys on start up?  I really have to get rid of Windows 7.  It is a disappointing product.

Thanks for your help

---

### Post by Lemuriano on 2012-04-21
Did you select dvd in the bios as the first option to boot from.

Regards.

PS. Did not realize it was an external dvd. In my case is f1 but I don´t know your particular model..

---

### Post by saskatchewan on 2012-04-21
It is an external samsung SE-S084.  How would I get into the bios?  By pressing F8 or F9?

---

### Post by Lemuriano on 2012-04-21
Sorry I haven´t  work with an external HDD.

---

### Post by saskatchewan on 2012-04-21
No problem, I manged to get to the bios and got rid of that horrible windows 7 however, when I click on the file folder, it only shows what is in the one partician.  How do I get it to show that other two particians.

---

### Post by saskatchewan on 2012-04-21
I mean in Ubuntu.

I did get into the bios and got it to recognize the external drive, thus, I am running Ubuntu 11.10 right now :-)

---

