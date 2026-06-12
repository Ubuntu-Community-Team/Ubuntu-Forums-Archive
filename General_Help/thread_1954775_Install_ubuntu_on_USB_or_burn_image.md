---
title: "Install ubuntu on USB or burn image"
date: 2012-04-08
forum: General Help
---

### Post by Fwission on 2012-04-08
Normally for my portable ubuntu installation I use start-up disk creater and remove the welcome screen. However, I've been reading that installing the actual OS is better and more stable. On the flip side, people have been saying the OS is slower and more unstable.

Could anyone who has both used a live image and installed Ubuntu on a portable USB explain which is safer and faster?

---

### Post by cody1233 on 2012-04-08
I am running a full install of Ubuntu off of a 16-GB flash drive.  It is pretty fast, but there are high-speed USB drives on my device.  It's safe, but you have to guard the drive with your life so it doesn't come loose.

---

### Post by Basher101 on 2012-04-08
a USB is not actually meant for such things, thats what SSDs are for. So keep in mind that your stick will get worn out alot faster than usual. Otherwise, USB sticks are just slower, miniature external SSDs..

---

### Post by cody1233 on 2012-04-08
Yeah, but I didn't have money to buy a new drive...So I'm being cheap :D

---

### Post by Basher101 on 2012-04-08
> **cody1233 said:**
> Yeah, but I didn't have money to buy a new drive...So I'm being cheap :D

well when it comes to budget it is an elegant portable form..now try to get windows 7 on a stick :lolflag:

i once took such a usb stick to school to see if they work with ubuntu..90% of the desktops i tried ( 10 in total :D) worked flawlessly with it. I was quite surprised.

---

### Post by Fwission on 2012-04-08
Well what I really meant to ask is it better to use a liveCD with persistent file on USB, or to fully install ubuntu on USB

---

### Post by Basher101 on 2012-04-08
> **Fwission said:**
> Well what I really meant to ask is it better to use a liveCD with persistent file on USB, or to fully install ubuntu on USB

that..i do not really know. Haven't given it much thought, but my guess would be a full install will work better, since you have all directories installed. The persistance file is only for a more temporary use of Ubuntu with the USB stick. 

to sum it up:

Use USB with a persistent file for short use

Use USB with full install for a longer period usage

this is all i can advise you.

regards

---

### Post by Cheesemill on 2012-04-08
I have full installs of several distros on USB sticks. My advice is to use ext2 as the filesystem as it will greatly reduce the number of writes to the device thus prelonging the lifespan.

Having a full install on a USB also means you can update the system properly, as far as I remember you can't update the kernel on a Live USB + persistance installation.

---

### Post by oldfred on 2012-04-08
I have 12.04 in a 8GB flash partition on my 16GB flash. I have not used it a lot, but it works with both my laptop and desktop. I also used gpt partitioning just to learn about gpt.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

---

### Post by Fwission on 2012-04-08
> **oldfred said:**
> I have 12.04 in a 8GB flash partition on my 16GB flash. I have not used it a lot, but it works with both my laptop and desktop. I also used gpt partitioning just to learn about gpt.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

Well installing on a USB is not very difficult, the hardest part is that I also keep a partition that I use to keep files for windows computers on, but I have that part all figured out. Thanks guys

---

### Post by fiatveritas on 2012-04-09
I run Ubuntu off my USB at my school's computers because I can't stand Windows' startup time. Probably the only reason you'd want to install Ubuntu on a HDD is because you can add a Java Environment which completely filled up my 4GB drive--where 2GB are dedicated for storage. Another reason I run Ubuntu off a USB is because I like running Chrome and sometimes Firefox and my school's servers don't regularly update their web browsers.

---

