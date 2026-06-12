---
title: "remove share on unmounted &lt;dual Boot&gt; drive"
date: 2011-04-03
forum: General Help
---

### Post by bearslumber on 2011-04-03
Hi,

I have a dual boot laptop Ubuntu 10.10 + Windows XP.

When browsing my Windows C Drive in Ubuntu I decided to create a share to the windows "my documents" folder.

The problem is that the windows drive is not automatically mounted at launch of ubuntu and as a result I get the following errors:

```
Could not find "/media/14F0AD48F0AD30C2/Documents and Settings/Lucas Redding"
```

and a search box is launched (See Attached Image). Although this is relatively harmless, it is a pain and I am dying to resolve it.

I have tried to look at the Samba and Nautilus settings but I am unable to find any that automatically mount the windows drive.

Any help is greatly appreciated.

Regards

Bearslumber

---

### Post by Morbius1 on 2011-04-03
[1] Create a more coherent home for the partition to live in:
```
sudo mkdir /media/WinXPC
```[2] Edit /etc/fstab as root:
```
gksu gedit /etc/fstab
```[3] Add a line to the end of fstab:
```
 UUID=14F0AD48F0AD30C2 /media/WinXPC ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
```[4] This step is very important - Run the following command to test for errors and mount the new partition:
```
sudo mount -a
```[5] Make sure it runs without errors and it does everything that you want it to do before rebooting.

---

### Post by Rebelli0us on 2011-04-03
Use "Ubuntu software center" to install "NTFS configuration tool" and set it to **auto-mount** your NTFS partitions at boot time.

---

### Post by Morbius1 on 2011-04-03
The first thing that ntfs-config does is asks you if you want to enable write support for ntfs. ntfs has had write support enabled by default for some time now so you have to ask yourself some questions:

Why doesn't ntfs-config know that.

What on earth does it do when you answer yes.

ntfs-config, pysdm, and mountmanager represent too high a risk for error. It's best to go old-school. Besides most of those are no longer maintained.

Just my opinion.

---

### Post by bearslumber on 2011-04-03
Hi Morbius,

Your solution worked a treat.

I used linux many moons ago and etc/fstab seems to have changed beyond recognition.

Many thanks and much appreciated.

Also thanks Rebelli0us. I think I'll stick with Morbius's solution, as it is quite clear that NTFS has full read write support by default. The only problem here was recognising that the mount was only temporary and therefore not compatible with persistent shares that I unwittingly created.  

Regards

Lucas

Aka Bearslumber

---

