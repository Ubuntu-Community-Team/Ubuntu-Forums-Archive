---
title: "64-bit or 32-bit?"
date: 2010-03-14
forum: General Help
---

### Post by nkbatsi on 2010-03-14
can someboby please answer this.

my installed kernels are:

linux-image-2.6.31-14-generic
linux-image-2.6.31-19-generic

my pc is old 700Mhz with 786 Mb of RAM

I tried to switch to pae kernels but my pc refuses to make any upgrades or changes:
should i try switching to meta-packages or not?

---

### Post by howefield on 2010-03-14
It isn't clear what you want to do, are you asking whether you should use 32 bit or 64 bit as per the thread title ?

Can I ask why you want a PAE enabled kernel ?

---

### Post by gnupipe on 2010-03-14
> **nkbatsi said:**
> 
my pc is old 700Mhz with 786 Mb of RAM


Your computer does not support 64 bit. :)

---

### Post by Slim Odds on 2010-03-14
> **gnupipe said:**
> Your computer does not support 64 bit. :)

LOL, it barely supports 32 bit......

---

### Post by nkbatsi on 2010-03-14
yes it sure barely supports 32-bit, i 'm just asking if these kernels are ok for me or should i change to meta packages

---

### Post by Slim Odds on 2010-03-14
Whatever the installer chose for you should be just fine.

---

### Post by nkbatsi on 2010-03-14
i know my pc is slow but i 'm just searching for a configuration that will be tolerable for me since this computer is just used for internet browsing, cd burning and listening to music. 

right now the problem is that it is very difficult for me to upgrade due to a fault in dpkg i think.

when i type: sudo dpkg --configure -a in a terminal i get no errors on broken packages but still when i try to update or install something i get errors.

this did not happen in the first place, my computer went nuts when i tried to install envyng.

---

### Post by snowpine on 2010-03-14
You will get better help if you post the error messages here and use a descriptive title for your thread. :)

As best as I can understand your question, the answer is: 32 bit

---

### Post by nkbatsi on 2010-03-14
[SIZE="2"]ok let' say i want to update my kernel, i have already tried to update through synaptic but i get errors. so i try -f install. [/SIZE]
 
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.31-20-generic
Suggested packages:
  fdutils linux-doc-2.6.31 linux-source-2.6.31
The following NEW packages will be installed:
  linux-image-2.6.31-20-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/28.9MB of archives.
After this operation, 90.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 152370 files and directories currently installed.)
Unpacking linux-image-2.6.31-20-generic (from .../linux-image-2.6.31-20-generic_2.6.31-20.57_i386.deb) ...
Done.
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.31-20-generic_2.6.31-20.57_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./boot/vmlinuz-2.6.31-20-generic')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.31-20-generic_2.6.31-20.57_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
~$

[SIZE="2"]i always get something like this every time i try to update or install anything, the problem is always something about dpkg[/SIZE]

---

### Post by oldos2er on 2010-03-14
Have you tried clearing your cache? ```
sudo apt-get clean && sudo apt-get update
```

---

### Post by dcstar on 2010-03-14
> **oldos2er said:**
> Have you tried clearing your cache? ```
sudo apt-get clean && sudo apt-get update
```

Yep, that will either remove the corrupted package - or more likely free up enough disk space - so things can be installed.

---

### Post by nkbatsi on 2010-03-18
> **dcstar said:**
> Yep, that will either remove the corrupted package - or more likely free up enough disk space - so things can be installed.

i have tried 

sudo apt-get clean

and 

sudo apt-get update

still i cannot remove the corrupted package,
there's a conflict between packages
 libmagickwand2 and libltdl7
seems that the upgrading of one of them blocks the upgrading of the other or even removing one of them. 

not even fixing them through synaptic is possible.

anyway, many thanks to all of you out there caring for each other's problems. 

i 'll post a new more descriptive thread soon.

---

### Post by Mr_Shifty on 2010-04-04
> **oldos2er said:**
> Have you tried clearing your cache? ```
sudo apt-get clean && sudo apt-get update
```

I was encountering this exact same issue (I'm on 64-bit Ubuntu 9.10) and this just fixed it for me.  Thanks.  :)

---

