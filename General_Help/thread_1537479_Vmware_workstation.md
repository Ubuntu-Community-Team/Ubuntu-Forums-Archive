---
title: "Vmware workstation"
date: 2010-07-23
forum: General Help
---

### Post by a sandwhich on 2010-07-23
Hello, I am going to be getting a new computer soon, which I hope to run ubuntu with. But I use cs4 production premium and lightwave. Will I be able to run these in vmware workstation with near native enviroment speeds? I will be tranferring from windows, will I be able to use the drives from my old system in the new one?

---

### Post by bodhi.zazen on 2010-07-23
You most certainly can use the old drives. Ubuntu wik rw both FAT and NTFS partitions, if you are asking about Data, or you can simply reformat them to ext4 ...

In terms of your applications, I am not familiar with them. In general you will likely have less problems with Virtualbox then VMWare, otherwise you will see some performance hit. Typically this is off set because the VM are fresh installs of Windows so they run faster ...

---

### Post by a sandwhich on 2010-07-23
I heard there were several problems and bugs when dealing with ntfs on ubuntu. Does this apply 10.4/

---

### Post by bodhi.zazen on 2010-07-23
> **a sandwhich said:**
> I heard there were several problems and bugs when dealing with ntfs on ubuntu. Does this apply 10.4/

What problems ? Ubuntu has managed ntfs partitions with no more or less problems then windows as long as I can recall.

I think it you information is very likely inaccurate, although you may be aware of some specific bug report.

The biggest problem with nfts is an absence of tools to repair the filesystem if there is a problem, so, if you are not going to run windows, I suggest you simply back up your data and use ext4.

If you do not want to do that, I do not anticipate any problems with ntfs (beyond the problems that exist with ntfs in windows).

---

### Post by a sandwhich on 2010-07-23
Thank you. If I have two drives for a ubuntu partition and 1 for a windows, will I be able to view the ubuntu drives in windows and the windows in ubuntu?

---

### Post by watupgroupie on 2010-07-23
You can view the NTFS Windows partition inside Ubuntu. But the Ext4 Ubuntu partition will not be visible within Windows.

---

### Post by bodhi.zazen on 2010-07-23
Windows is more limited. You can try a third party driver

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I would go with NTFS for a shared data partition. Second choice would be ext3.

I am not sure how the fs-driver does with ext4 (probably not well).

---

### Post by CharlesA on 2010-07-23
That driver doesn't work with EXT4 unless you have it set a certain way. Works great with EXT3 tho.

---

### Post by bodhi.zazen on 2010-07-23
> **CharlesA said:**
> That driver doesn't work with EXT4 unless you have it set a certain way. Works great with EXT3 tho.

Thank you for the information.

---

### Post by a sandwhich on 2010-07-24
If I am installing ubuntu to a new drive that I just got, should I format it on the operating system that is on the other two drives, or just plug it in and let ubuntu do that?

---

### Post by DeMus on 2010-07-25
> **a sandwhich said:**
> Hello, I am going to be getting a new computer soon, which I hope to run ubuntu with. But I use cs4 production premium and lightwave. Will I be able to run these in vmware workstation with near native enviroment speeds? I will be tranferring from windows, will I be able to use the drives from my old system in the new one?

I would put an extra disk into the new computer, just for Windows.
Install Windows on, including CS4.
Then install Ubuntu like you have planned on your new drive(s). Ubuntu will take over boot now and includes Windows into your Grub. That way you can choose which OS to boot. Ubuntu will be the default setting, just only when you plan to use Windows you have to respond to the boot menu.
Advantage of dual boot vs Virtual is speed in general and especially in video since the vm drivers are not that spectacular. With dual boot you can install the latest video drivers for your card.
If you plan to use Windows only for cs4, disable the network after installing the necessary updates. That way you don't need an anti-virus scanner which improves the speed of your computer. The less services running in the background the better.
Have fun.

---

### Post by a sandwhich on 2010-07-25
Yes, that is what I decided on, but I am asking should I format the drive in windows before loading ubuntu on it or just hook it up and install ubuntu with no formating.

---

### Post by bodhi.zazen on 2010-07-25
> **a sandwhich said:**
> Yes, that is what I decided on, but I am asking should I format the drive in windows before loading ubuntu on it or just hook it up and install ubuntu with no formating.

It does not matter if you format the new drive (from windows) or not, the Ubuntu installation process will format the partitions it uses as part of the installation either way.

---

