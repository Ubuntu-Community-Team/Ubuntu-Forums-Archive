---
title: "RAID showing as two seperate drives"
date: 2011-02-03
forum: General Help
---

### Post by nry on 2011-02-03
I have a motherboard with the following chipset Intel® 945GM + Intel® ICH7R Chipset

This board: [http://emea.kontron.com/products/boards+and+mezzanines/embedded+motherboards/miniitx+motherboards/986lcdmmitx.html](http://emea.kontron.com/products/boards+and+mezzanines/embedded+motherboards/miniitx+motherboards/986lcdmmitx.html)

I have two 320GB HDDs setup in hardware raid as shown below. But in gparted they are showing as two seperate drives. Why is this?

Raid setup:
[img]http://img714.imageshack.us/img714/9906/61792293.jpg[/img]

GParted
[img]http://img511.imageshack.us/img511/6759/75595685.jpg[/img]

fdisk -l 
[img]http://img88.imageshack.us/img88/8715/98189360.jpg[/img]

What am i doing wrong here?

---

### Post by YesWeCan on 2011-02-03
You may need to read this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I am aware of 3 main categories of RAID.
1. I always use software RAID. This involves a Linux utility named mdadm. Mobo RAID is not required. This is not as fast as full hardware RAID but is usually pretty darned fast.
2. Hardware RAID (full) is where all the RAID is handled on the Mobo or a card. I believe this is seamless to the OS. It is expensive: cards cards can cost hundreds of dollars. Very fast. RAID controller chips are big and hot like graphics chips.
3. Host RAID or FakeRAID. This is some sort of hybrid. Some work is done on the Mobo but I think most is done by the OS with special drivers. This is the usual type of RAID supplied on desktop Mobos. The Linux utility is dmraid.

Your Mobo appears to use #3. I've never used it myself but people do. If you wanted to use software RAID instead then you must disable all RAID in the bios.

---

### Post by psusi on 2011-02-03
> **YesWeCan said:**
> 
3. Host RAID or FakeRAID. This is some sort of hybrid. Some work is done on the Mobo but I think most is done by the OS with special drivers. This is the usual type of RAID supplied on desktop Mobos. The Linux utility is dmraid.


All of the work is done in software.  That software takes the form of a driver they give you for Windows, and a bios extension rom.  Other than that, there is no hardware support.  The only difference is that when placed into "raid mode" the AHCI controller reports a different PCI ID so it will be claimed by the raid driver instead of the AHCI driver in Windows.  The Linux AHCI driver claims both IDs.

If you don't need to dual boot with Windows, then you are better off with mdadm Linux software raid since it is better supported.  If you must dual boot with Windows, then dmraid enables access and works fairly well.  The gparted in current versions of Ubuntu have a bug where it will not show the raid array in the device list.  This has been fixed in Natty, and in current versions of Ubuntu, you can get around it by installing the kpartx package, or manually launching gparted and passing it the correct raid device name, which is /dev/mapper/something.

---

### Post by YesWeCan on 2011-02-03
That is very interesting. So FakeRAID really is just a sham with regard to hardware support. That's good to know as I nearly bought a mobo recently with so-called raid on it as I thought the performance would be better.
So why does Windoze need this when Linux doesn't. Or s it a cynical conspiracy between MS and the Mobo mfrs? :p

---

### Post by psusi on 2011-02-03
> **YesWeCan said:**
> That is very interesting. So FakeRAID really is just a sham with regard to hardware support. That's good to know as I nearly bought a mobo recently with so-called raid on it as I thought the performance would be better.
So why does Windoze need this when Linux doesn't. Or s it a cynical conspiracy between MS and the Mobo mfrs? :p

Because windows software raid support is poor.

---

### Post by ronparent on 2011-02-04
If you want both windows and linux to install and operate on a shared raid set you have to use 'fakeraid'. The software that allows this in Ubuntu is known as dmraid. The simple answer to the OP is that gparted has a bug in 10.04 and 10.10 that prevents partitioning of raid drives. The work around is to install kpartx to the a live cd session you want to install to a supported raid set. This will enable gparted to see and create the raid partitions during installation.

---

### Post by SeattleJoe98101 on 2011-04-24
I had many problems with dmraid until I uninstalled dmraid v 16 and installed v 15.  See prior posts here:   [http://ubuntuforums.org/showthread.php?t=1608366&page=3](http://ubuntuforums.org/showthread.php?t=1608366&page=3)

My setup had ubuntu booting from a single drive and a raid1 array on 2 2tb drives.  So I installed Maverick and then discovered that if I uninstalled dmraid and installed the Karmic Version (I believe its RC 15) that everything worked fine.  I just have to be careful every time I do upgrades to make sure that I don't allow the software to upgrade dmraid.

I'm hoping that Natty will have a new version of dmraid that solves the problem, but I'm not counting on it.

---

### Post by SeattleJoe98101 on 2011-04-24
Sorry I got the thread wrong.  The post I was referring to is here:

[http://ubuntuforums.org/showthread.php?p=10113096#post10113096](http://ubuntuforums.org/showthread.php?p=10113096#post10113096)

I'm going to wait until 4/28 or next weekend and try a live cd of Natty.  That should tell whether they've fixed the problem.

I know other posters have said that installing kpartx would solve the problem.  It didn't help for me, although its possible it was part of the solution.  What definitely worked was installing the karmic version of dmraid.  Since I did that everything has worked fine despite the fact that I dual boot with Windows 7 and Vista.

---

### Post by psusi on 2011-04-25
SeattleJoe, please don't try to take over someone else's very old thread.  Either start a new thread, or better yet, file a bug report detailing what does not work for you with the Maverick version.  Without a bug report, it isn't going to get fixed.

---

