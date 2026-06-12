---
title: "Samba"
date: 2010-06-07
forum: General Help
---

### Post by COKEDUDE on 2010-06-07
Is there any point of installing Samba when dual booting between ubuntu and Windows XP? I'm able to access my XP partition from Ubuntu with no problems and share files with no problem. Unfortunately it doesn't work the other way. When I'm in my XP partition I'm not able to access my Ubuntu partition. Is there another problem I have or something else I need to do?

---

### Post by yetiman64 on 2010-06-07
> **COKEDUDE said:**
> Is there any point of installing Samba when dual booting between ubuntu and Windows XP? I'm able to access my XP partition from Ubuntu with no problems and share files with no problem. Unfortunately it doesn't work the other way. When I'm in my XP partition I'm not able to access my Ubuntu partition. Is there another problem I have or something else I need to do?

Not really of use to you as samba is for sharing files over a network, also in dual booting when one OS is operating the other is not, therefore no networking is possible between the 2 OSes being dual booted.
Samba is only of use to you if you intend to share files with other completely separate machines via a LAN for example.

For getting Ubuntu partition access in windows you would need to install in XP a filesystem driver like the ext2IFS driver, available here [http://www.fs-driver.org/](http://www.fs-driver.org/) .

Although it is an ext2 ifs driver, it will mount ext3 partitions as ext2 (not sure about ext4 though- it may not - What Ubuntu OS are you using? Keep in mind Lucid uses ext4 as default).

Probably a better means of file access for both systems is to repartition the drive and create a shared NTFS partition (That is if you have the space available). Or leave the partitions as is and install a second NTFS HDD as a shared drive to which both will have access. Cheers.

---

### Post by COKEDUDE on 2010-06-07
I've been giving Lucid a trial run for a few days. It looks like I will go back to mint then. I really liked mint and it still uses ext3. How do I setup a shared NTFS partition?

---

### Post by RJ12 on 2010-06-07
You will need to create a partition and format it as NTFS. I believe you can do this with Disk Utility in System > Administration > Disk Utility

You can also install GParted

Be sure to do this from a LiveCD as I think the HD needs to be unmounted

---

### Post by COKEDUDE on 2010-06-07
> **RJ12 said:**
> You will need to create a partition and format it as NTFS. I believe you can do this with Disk Utility in System > Administration > Disk Utility

You can also install GParted

Be sure to do this from a LiveCD as I think the HD needs to be unmounted

Is there also a way to do this from the terminal? I like using the terminal whenever possible. Its fun to learn about the terminal.

---

### Post by yetiman64 on 2010-06-07
> **COKEDUDE said:**
> I've been giving Lucid a trial run for a few days. It looks like I will go back to mint then. I really liked mint and it still uses ext3. How do I setup a shared NTFS partition?

Only "need" to go back to mint with ext3 **if** you choose the ext2ifs driver in XP. Shared NTFS partition is another totally separate option to you.

Question: **Do you use a desktop PC or a laptop? **

If a desktop and you can afford to purchase a 2nd HDD, the easiest option for "shared NTFS partition" is to install a 2nd drive and format it to NTFS. Both XP and Ubuntu can use it.

If you use a laptop/netbook, consider using an external usb HDD as the  shared NTFS partition (yet another option to you.)

 >      [QUOTE]
                                                                      [SIZE=2]Originally Posted by **RJ12**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9425216#post9425216")[/SIZE]                 
                 [I][SIZE=2]You will need to create a partition  and format it as NTFS. I believe you can do this with Disk Utility in  System > Administration > Disk Utility

You can also install GParted[/SIZE] [SIZE=2]

Be sure to do this from a LiveCD as I think the HD needs to be unmounted[/SIZE] [/I]
Is there also a way to do this from the terminal? I like using the  terminal whenever possible. Its fun to learn about the terminal.     [/QUOTE]As good as it is to learn the terminal, I too recommend the use of Gparted from a live-cd (consider a 2nd HDD as **1st option** though). To attempt this from terminal would be quite complex and potentially damaging to your system.

Even using Gparted from a live-cd involves "shrinking" and possibly "moving" partitions and can be damaging if used wrong.

[B]I recommend you do a complete backup of all your data to cd, dvd, usb stick or external HDD, before touching partitioning (ie. copy all your data off the drive being partitioned --if you choose this option !).  

[/B]

---

### Post by COKEDUDE on 2010-06-09
I use a laptop. 

I have 3 external HD's. Its from backing up about 6 years of data :).

---

