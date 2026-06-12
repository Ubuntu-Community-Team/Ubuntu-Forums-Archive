---
title: "Ubuntu taking up extra space in my hard drive?"
date: 2011-01-09
forum: General Help
---

### Post by jcd29 on 2011-01-09
How much space does Ubuntu 10.04 take?

I have a 320 GB HDD I use for data apart from the regular HDD for the OS. Of course when you go to format it, it's actually 298GB. So I made a 248 GB partition, ext4 for ubuntu data, and a 50GB partition for Windows.

It shows as 248.01 GiB in size in GParted, with 217.27 GiB used. 30.75GiB unused.

When I go to Computer, right click on the partition, click Properties, it says Total capacity 244.1 GB, 18.3 GB free, 225.8 GB Used.

So:

1) Why does GParted show it as 248GB and the Properties as 244 GB?

2) More importantly: Why does Gparted show I've used 217.27 GBs, while the Properties show I've used 225.8 GB? What's going on there?

[[IMG]http://img709.imageshack.us/img709/834/screenshot1pl.th.png[/IMG]](http://img709.imageshack.us/i/screenshot1pl.png/)

---

### Post by Kljuka on 2011-01-09
I can't answer to your question but can direct you further:
you should distinguish betwen GB and GiB. It's not the same:
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

---

### Post by jcd29 on 2011-01-09
It still does't add up, I think. If it was just that, then Gparted would show the amount of space used as more than what the Properties show, right?

Percentage wise it seems like the amount of space used shown in Gparted is less than the amount of space used shown in the Properties.

---

### Post by Bucky Ball on 2011-01-09
You haven't installed any OS yet?

Sounds like you are going for a dual boot so start by installing Windows on the partition you've made for it.

When installing Ubuntu choose 'manual partitioning'. You will see your Windows install in there on an NTFS partition. Just leave that be.

Kill the other partition (delete it) and create three partitions:

/ = where your OS lives, 20Gb is heaps;
/home = where your personal data and settings live, big as you want;
/swap = Windows equivalent of a pagefile, 2Gb is fine, 4Gb if you want to hibernate.

Make them all EXT4 (except /swap which takes care of itself).

NOTE: I would personally make the Windows partition big enough for Windows only (check system requirements for your version of Win) and if you want to share data between the two OSs create an NTFS data partition. This would give you five partitions on one physical drive which is not allowed so after you assign the / partition for your Ubuntu OS, make the rest of the free space one big extended partition into which you can add as many logical drives (partitions) as you like. 

;)

---

### Post by jcd29 on 2011-01-09
> **Bucky Ball said:**
> You haven't installed any OS yet?

Sounds like you are going for a dual boot so just install windows on the partition you've made

When installing Ubuntu choose 'manual partitioning'. You will see your Windows install in there on an NTFS partition. Just leave that be.

Kill the other partition (delete it) and create three partitions:

/ = where your OS lives, 20Gb is heaps;
/home = where your personal data and settings live, big as you want;
/swap = Windows equivalent of a pagefile, 2Gb is fine, 4Gb if you want to hibernate.

;)

No I have! I've been dual booting XP and Ubuntu for months now. I just always had that doubt about the discrepancy in amount of space shown in the Properties vs. the one shown in Gparted or whenever I use Windows for another drive, for example.

---

### Post by Bucky Ball on 2011-01-09
Sorry, yea. Weird. What is actually in that partition when you open it in file manager?

---

### Post by hashbangfoo on 2011-01-09
I have used the following script to clean up an install, and keep the bloat at bay...

Obviously, it is run as a sudo job.

Here is the script, cut and paste into a file. Then "chmod +x ubuntu_cleaner.sh (or what ever you name it), and then "sudo ./ubuntu_cleaner.sh":

#!/bin/bash

OLDCONF=$(dpkg -l|grep "^rc"|awk '{print $2}')
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"

if [ $USER != root ]; then
  echo -e $RED"Error: must be root"
  echo -e $YELLOW"Exiting..."$ENDCOLOR
  exit 0
fi

echo -e $YELLOW"Cleaning apt cache..."$ENDCOLOR
aptitude clean

echo -e $YELLOW"Removing old config files..."$ENDCOLOR
sudo aptitude purge $OLDCONF

echo -e $YELLOW"Removing old kernels..."$ENDCOLOR
sudo aptitude purge $OLDKERNELS

echo -e $YELLOW"Taking out the trash..."$ENDCOLOR
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null

echo -e $YELLOW"Script Finished!"$ENDCOLOR

---

### Post by jcd29 on 2011-01-09
> **Bucky Ball said:**
> Sorry, yea. Weird. What is actually in that partition when you open it in file manager?

When I open the partition and right click every folder and click Properties, it shows I've used 213 GB.

So I have no idea where that 225 figure comes from. It's all very odd.

---

### Post by Bucky Ball on 2011-01-10
Try hashbang's script. That could very well clean things up.

---

### Post by jcd29 on 2011-01-10
> **Bucky Ball said:**
> Try hashbang's script. That could very well clean things up.

I really don't know what that does/could do to my system!

Besides, I don't think it'll explain how I'm getting different numbers for the amount of space my drive has, and how much of it I have used.

---

### Post by Bucky Ball on 2011-01-10
> **jcd29 said:**
> I really don't know what that does/could do to my system!



This:

```
echo -e $YELLOW"**Cleaning apt cache.**.."$ENDCOLOR
aptitude clean

echo -e $YELLOW"**Removing old config files**..."$ENDCOLOR
sudo aptitude purge $OLDCONF

echo -e $YELLOW"**Removing old kernels**..."$ENDCOLOR
sudo aptitude purge $OLDKERNELS

echo -e $YELLOW"**Taking out the trash**..."$ENDCOLOR
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null
```Your install may have left unrequired installation packages on the partition. It can happen.

I would also open a terminal and try:

```
sudo apt-get autoremove
```Don't panic. It only removes unused/not required packages and won't break anything. ;)

Also, have a look here:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by jcd29 on 2011-01-10
Done and done.

Same thing still.

---

### Post by jcd29 on 2011-01-10
Any ideas?

Can you guys check with GParted and Properties to see if the same thing happens to you?

---

### Post by Bucky Ball on 2011-01-10
Can guarantee you it wasn't last time I looked and sorry, no ideas. :(

---

### Post by jcd29 on 2011-01-13
No one? :(

---

### Post by jcd29 on 2011-04-27
Here's an illustration.

First image is from right clicking the drive and choosing Properties:

[IMG]http://img171.imageshack.us/img171/6769/screenshotcka.png[/IMG]

Second is from GParted:

[IMG]http://img26.imageshack.us/img26/3639/screenshot1ah.png[/IMG]

Third and final one is from the Disk Utility:

[IMG]http://img695.imageshack.us/img695/1326/screenshot2ht.png[/IMG]

---

### Post by jcd29 on 2011-07-06
Bumping this one last time.

---

