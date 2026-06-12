---
title: "CR-48 Space"
date: 2011-08-16
forum: General Help
---

### Post by Scaea on 2011-08-16
I have one of those little Chromos notebook things and have decided that Chromos isn't really worth it. With the solid state an' all, Ubuntu boots almost as fast and, well, I like Ubuntu more.

But I am wondering: because I only have about 600MB free on the little 15GB SSD:

All the files I can see only take up ~4GB and the partition Ubuntu occupies is 11GB. Where's all the rest of my space? Is it just hidden files that aren't being counted? I thought I had more last time I booted Ubuntu into the thing (it has been reset a few times) but 600MB just ain't that much.

Anyone know what could be happening?

---

### Post by pqwoerituytrueiwoq on 2011-08-16
my 64bit 10.04 install uses > 7gb for system files
there are certain settings you should do when using a ssd with ubuntu to avoid wearing it out quickly
use noatime and nodiratime in fstab (if you use ext3/4)
enable trim with the discard option (10.04 does not support trim out of the box)
use a ram disk for firefox cache
if you are planning on making it more like a traditional netbook you may want to get a small hdd (or a decent ssd) and take the ssd out in case you decide to switch back

---

### Post by Scaea on 2011-08-16
So you think my SSD is wearing out a bit?

Does anyone know if 11.04 have trim abilities in it out of the box? (I'm not on my laptop right now)

---

### Post by pqwoerituytrueiwoq on 2011-08-16
doubt is is wearing out yet you should use those options asap though in fstab or you will
anything over 10.04 supports trim out of the box (but it is not enabled)
all 10.04 needs is a kernel upgrade (the first command will use maverick's kernel the second will use natty's)
```
sudo apt-get install linux-headers-generic-lts-backport-maverick linux-image-generic-lts-backport-maverick
```or
```
sudo apt-get install linux-headers-generic-lts-backport-natty linux-image-generic-lts-backport-natty
```edit /etc/fstab
sudo gedit /etc/fstab
look for a line like this
```
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4    **discard,**errors=remount-ro**,noatime,nodiratime** 0       1
```the bold parts are what i added for ssd usage
do this for any line that uses ext3/4

---

### Post by kerry_s on 2011-08-16
did you wipe all the other partitions?

i wiped the whole drive & created 1 "/" partition when i setup mine.

---

### Post by pqwoerituytrueiwoq on 2011-08-16
mine is setup a bit different 
ssd only has /
/tmp is on the ram 
/var and /home is on a hdd here
but you don't get that option having one drive bay
since you have a small drive i assumed you made a single partition
if you enable trim with discard it should free up some space
you may also want to use [bleachbit]("apt:bleachbit") to free up some space
the reason for the noatime,nodiratime is to stop it from setting the last accessed time on the files/folders this setting that create a ton of writes and a ssd has a limit on writes the ssd in the CR-48 is probably a higher grade ssd than mine is mine is meant for low write environments speaking of the write limit don't use a swap partition on a ssd

---

### Post by Scaea on 2011-08-16
No, I did not wipe mine. I only followed the ever-so-popular script provided [here]("http://chromeos-cr48.blogspot.com/2011/04/ubuntu-1104-for-cr-48-is-ready.html"). On the Chrome OS forums, it is implied that it is quite difficult to wipe it all the way down as the hardware "[doesn't support initrd]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48")".

How can you do this?

---

### Post by pqwoerituytrueiwoq on 2011-08-16
gust go ahead and edit your fstab file with the stuff in bold that should do it with a reboot
since it is using natty the kernel supports trim already
then check your disk usage

---

### Post by kerry_s on 2011-08-16
> **Scaea said:**
> No, I did not wipe mine. I only followed the ever-so-popular script provided [here]("http://chromeos-cr48.blogspot.com/2011/04/ubuntu-1104-for-cr-48-is-ready.html"). On the Chrome OS forums, it is implied that it is quite difficult to wipe it all the way down as the hardware "[doesn't support initrd]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48")".

How can you do this?

I did the bios flash, so I can install anything on my cr-48.

---

### Post by Scaea on 2011-09-26
> **kerry_s said:**
> I did the bios flash, so I can install anything on my cr-48.

So for some Absolute Beginner Talk, how does one do a "bios flash" on a CR-48?

---

### Post by Scaea on 2011-10-07
> **kerry_s said:**
> did you wipe all the other partitions?

i wiped the whole drive & created 1 "/" partition when i setup mine.

How can I do this!??

---

### Post by Scaea on 2011-10-07
> **kerry_s said:**
> I did the bios flash, so I can install anything on my cr-48.

How can I "do a bios flash" so that I can install anything on a Cr-48?

I cannot get anyone to even try to answer this question. They all send me [here]("http://chromeos-cr48.blogspot.com/2011/04/ubuntu-1104-for-cr-48-is-ready.html").

---

