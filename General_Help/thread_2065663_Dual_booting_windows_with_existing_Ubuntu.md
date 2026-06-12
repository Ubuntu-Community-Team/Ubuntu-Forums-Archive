---
title: "Dual booting windows with existing Ubuntu"
date: 2012-10-02
forum: General Help
---

### Post by googleye on 2012-10-02
After deleting all my partitions and freshly installing Ubuntu on the whole drive I realised I will need some programs for Windows. It's my school laptop so I will need it for some classes, it's mainly IronCAD and Master Collection.

Is it possible to create a partition in gparted(guide?) and make Windows install there? Or do I need to install Windows and then start over making a partition for Ubuntu? How much space would I need for Windows + IronCAD + Master Collection? I barely need anything for regular files, 500 mb will due.

Also, how does this affect the general performance? Is running Windows virtually a better choice or does that require a lot of power?

---

### Post by oldfred on 2012-10-02
Windows will install to any primary partition (sda1 thru sda4) that is NTFS with the boot flag. You can create that partition with gparted, but some have said with Windows 7 they had to reformat again as part of the install.

I have seen 20GB  for XP and 30GB for Windows 7 as suggested sizes, but do not know how large your applications are.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by jerrrys on 2012-10-02
You can dual boot, but 500MB for windows will not cut it.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot+install+ubuntu+first&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot+install+ubuntu+first&as_qdr=all&sa=Google+Search&lang=en")

edit:  Out-gunned by oldfred :)

---

### Post by Mark Phelps on 2012-10-02
If you create an NTFS partition using GParted, that will prevent Win7 from creating two partitions during its installation -- the BOOT partition and the OS partition.

However, what you really NEED to do is reformat that partition as part of the Win7 install.  That tends to work better in the long run.

Also, recommend using no less than 30GB for the Win7 install (as oldfred suggested), especially since you're going to be installing additional applications.  Win7 needs extra space to function properly, if you create a partition barely big enough, it will fail down the road.

---

### Post by Cheesemill on 2012-10-02
If your machine is powerful enough you also have the option of running a Windows VM instead.

---

### Post by Prospero2006 on 2012-10-03
Another suggestion:

It sounds like you may not have the option of reformatting, repartitioning, and reinstalling Windows on that particular machine.  

You could install Ubuntu to a usb drive so that it acts like a regular partition.(Kind of a hassle having to plug in the usb and manually select it as the boot device, but in a pinch it's certainly an alternative.)

---

### Post by googleye on 2012-10-03
Running it virtually would be the easiest way but how well will a i3 with integrated graphics manage it? When you say 30gb, is it just for windows or is that enough for more files? Maybe I should aim for around 50.

And since Ubuntu is my primary OS I don't wanna carry around a usb all the time :p

So if I understand this correctly. I can create a ntfs partition and Windows will keep to it? And when I choose format during installation it will ONLY format the ntfs partition? And I'm assuming then since it's only one partition, it will leave grub alone?

---

### Post by Mark Phelps on 2012-10-03
> **googleye said:**
> Running it virtually would be the easiest way but how well will a i3 with integrated graphics manage it? When you say 30gb, is it just for windows or is that enough for more files? Maybe I should aim for around 50.
The 30GB is for the Win7 partition -- which will include the OS, apps, and data files.  If you expect to be creating and/or saving lots of large data files, you should make the partition larger or, if you want to share them with Ubuntu, create a large NTFS shared data partition for them.

> So if I understand this correctly. I can create a ntfs partition and Windows will keep to it? And when I choose format during installation it will ONLY format the ntfs partition?
Yes -- it will only reformat that one partition, not anything else.
>  And I'm assuming then since it's only one partition, it will leave grub alone?
NO -- any Windows installation is going to overwrite the MBR on the hard drive and wipe out any GRUB code there. The only way to prevent that is to have Windows installed on a separate physical drive than Ubuntu.

---

### Post by googleye on 2012-10-03
> **Mark Phelps said:**
> The 30GB is for the Win7 partition -- which will include the OS, apps, and data files.  If you expect to be creating and/or saving lots of large data files, you should make the partition larger or, if you want to share them with Ubuntu, create a large NTFS shared data partition for them.


Yes -- it will only reformat that one partition, not anything else.

NO -- any Windows installation is going to overwrite the MBR on the hard drive and wipe out any GRUB code there. The only way to prevent that is to have Windows installed on a separate physical drive than Ubuntu.

Will Ubuntu automatically be able to read my new partition?

Ah, what are the steps to get GRUB back? "sudo grub-install /dev/sda" ?

---

### Post by oldfred on 2012-10-03
You need a liveCD or USB to boot Ubuntu so you can reinstall grub2 to the MBR or a Linux RepairCD or USB. Then after booting Ubuntu on hard drive you need to run this for grub2's os-prober to find the Windows install and add it to your boot menu:
sudo update-grub

If you want a gui:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Gui, Terminal & alternate install CD rescue grub repair
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I also suggest the separate shared NTFS data partition. Set the Windows system partition as read-only if you want to mount it in Ubuntu. If read only it avoids issues of accidentally damaging something. The Linux NTFS driver shows all the Hidden files & folders that Windows hides. The shared data NTFS partition then can be read/write from both systems. I still have my Firefox & Thunderbird settings in a shared NTFS partition even though I do not boot XP anymore.

---

### Post by googleye on 2012-10-06
Thanks for your help!

---

