---
title: "raid ubuntu/windows grub setup"
date: 2009-07-09
forum: General Help
---

### Post by NastyNative on 2009-07-09
I was wondering if any one can help me with the grub loader

Im having issues getting the dual boot to load ubuntu instead it 
goes right into Vista and does not give me an option to 
load ubuntu..


and what we found out so far unfortunately some one tried to 
help me but they didn't know exactly how to do it.

You can find the general info on this thread 
installation setup 

CLICK HERE --->[GENERAL INFO]("http://ubuntuforums.org/showthread.php?p=7590237#post7590237")

---

### Post by Jebtrix on 2009-07-09
So you installed Ubuntu on a separate 160Gig while Windows is on a RAID that your BIOS is set to boot from right? I'll at least get you started. To make it easier change your BIOS to boot from 160Gig drive first. Most likely your using software 'assisted' raid and are going to need to install dmraid in Ubuntu:

```
sudo apt-get install dmraid
sudo dmraid -ay
```

Most likely it will say array already activated.
```

gksudo gedit /boot/grub/menu.lst
```

I'm going to make an assumption here, add (the menu.lst will have a boot to windows example, just paste this below that):
```
title           Windows Vista
root            (hd1,0)
makeactive
chainloader     +1
```

Save then:

```
sudo update-grub
```

---

### Post by NastyNative on 2009-07-09
Hi Jebtrix thanks for helping me with this..

Ok i did the reseach about my mobo bios and setting up my hard drive as primary boot.

Because my Raid uses (nvidea) raid drivers when I go to my bios 
under "Hard Drive boot Priority" It only gives me the option to 
boot "Nvidea Stripe 153GB" (which is my raid) and "Bootable additional card"
I do not have the option to boot from the WD 160GB.. Unless I disable my RAID 

Onchip sata = enabled, Onchip Sata Controller = Enabled
Onchip Raid Config = 
sata 1 + sata 2 enabled.
The WD is connected to Sata 3 which I have enabled and tried to restart but it still loads the RAID (sata 1+2)

Now the code you provided is to add raid drivers to the WD drive.
I know im a nubie but I wanna understand why I would need 
raid drivers for a single drive?
maybe these drivers will allow my mobo to see the WD as a RAID setup?

 
The grub loader from what I have read needs to be loaded to the correct partition
I thought I loaded it to the correct partition "/" when I 1st installed ubuntu

"sudo grub"
this will get me the grub> prompt

"find /boot/grub/stage1"
which produces
"(hd2,0)"
this tells me the grub loader is in my set up in (hd2[which is hard drive 2, which is also part of my raid],0 [which is the partition])

The next code is "setup(hdx,y)"
So shouldn't I load it this way according to my set up (hd3[which is the 3rd hardrive representing the WD 160],1 [which is the 1st partition "/"])

Like I said I'm new to this dual boot thing.
I just wanna understand what you are asking me to do, im not saying your wrong 
im saying i just wanna know what it means.
Im in no hurry to get this working , but I do wanna understand what im doing and 
also get the Grub loader to work properly with my RAID ntfs vista.

---

### Post by Jebtrix on 2009-07-10
Well lets start with your BIOS. I use nvidia raid also. Different mobo manufacturers will have different bios setup configurations but this is how mine is. Under Boot Device Priority I have the option to set first boot device to Hard Disk/CDROM/Floppy/etc. There is a separate menu for Hard Disk Drives. In that menu is where I can tell it to boot from RAID1, RAID2, or my non raid sata drive (basically specifies the actual Hard Disk for the Boot Device Priority menu Hard Disk option). It goes by boot priority, so make sure the WD160blahblah disk is at the top of the hard disk list. What is your mobo model? 

Honestly you can do this two ways. You could either have your BIOS boot to Vista, and add Linux to Vista's boot loader. Or boot to Ubuntu and add Vista to grub boot loader.

If you want to try having Vista do the work take a look here:
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

---

### Post by Jebtrix on 2009-07-10
> maybe these drivers will allow my mobo to see the WD as a RAID setup?

No. You have Ubuntu installed on a single drive. If you had your BIOS pointing to that drive to boot from, you would be able to boot into Ubuntu and thats it. In order to make Ubuntu give you the choice to boot to your Vista (on RAID) it needs to be able to actually see the raid. By default Ubuntu will not see nvidia raid (aka softwareraid/fakeraid). Ubuntu will see the inidividual drives that make up the array, but that doesn't help. It needs the dmraid package to give it that ability to see your raid array as a single logical drive. Once it can recognize the raid properly, you can set up grub to boot to it, aka Dual Boot System.

---

### Post by NewbieNik on 2009-07-11
> **Jebtrix said:**
> . By default Ubuntu will not see nvidia raid (aka softwareraid/fakeraid)..

Not strictly true. New Jaunty can realise that the disks are RAID'd and boot from them. Mine does (I have another issue on boot, but it still loads grub and the splash screen)
I am usng nVidia nForce4 chipset with 4 x 160Gb 2.5" SATAII drives in a striped (RAID0) array. It also recognises Mirroring (RAID1), but not mirrored striping (RAID 1+0).
It doesn't help the original poster, but thought I'd point it out.

---

### Post by NastyNative on 2009-07-11
> **Jebtrix said:**
> 

If you want to try having Vista do the work take a look here:
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

I cannot use this to boot from vista because it requires that 
I log in with root privileges an since I cant boot 
into Linux how can I log in with root privileges?

Ok so i found this easyBCD
which is a vista boot loader so I can 
add the linux grub, but once again vista 
does not recognize the linux partition 

So the problem Im having is linux is not being loaded
because I have vista as the primary drive which im trying 
to change but the only way to do it is to disable my raid drive.

vista doesnt recognize linux, 
linux is not set to boot 1st..

I dont know what else to do.
I will keep trying to boot into linux 
by playing with the bios ..

---

### Post by NastyNative on 2009-07-11
> **Jebtrix said:**
> So you installed Ubuntu on a separate 160Gig while Windows is on a RAID that your BIOS is set to boot from right? I'll at least get you started. To make it easier change your BIOS to boot from 160Gig drive first. Most likely your using software 'assisted' raid and are going to need to install dmraid in Ubuntu:

```
sudo apt-get install dmraid
sudo dmraid -ay
```

Most likely it will say array already activated.
```

gksudo gedit /boot/grub/menu.lst
```

I'm going to make an assumption here, add (the menu.lst will have a boot to windows example, just paste this below that):
```
title           Windows Vista
root            (hd1,0)
makeactive
chainloader     +1
```

Save then:

```
sudo update-grub
```

ok since i was able to make linux the primary drive now I followed your steps

``````````````````````````````````````````````
mclovin@AbitANM2:~$ sudo apt-get install dmraid
[sudo] password for mclovin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdmraid1.0.0.rc15
The following NEW packages will be installed:
  dmraid libdmraid1.0.0.rc15
0 upgraded, 2 newly installed, 0 to remove and 154 not upgraded.
Need to get 140kB of archives.
After this operation, 459kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main libdmraid1.0.0.rc15 1.0.0.rc15-6ubuntu2 [105kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main dmraid 1.0.0.rc15-6ubuntu2 [35.1kB]
Fetched 140kB in 1s (136kB/s)
Selecting previously deselected package libdmraid1.0.0.rc15.
(Reading database ... 101349 files and directories currently installed.)
Unpacking libdmraid1.0.0.rc15 (from .../libdmraid1.0.0.rc15_1.0.0.rc15-6ubuntu2_amd64.deb) ...
Selecting previously deselected package dmraid.
Unpacking dmraid (from .../dmraid_1.0.0.rc15-6ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up libdmraid1.0.0.rc15 (1.0.0.rc15-6ubuntu2) ...

Setting up dmraid (1.0.0.rc15-6ubuntu2) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: deferring update (trigger activated)

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
mclovin@AbitANM2:~$ 
```````````````````````````````````````````````````````````````````````

When i go into menu.lst 

Im assuming this is where I have to change it??

````````````````````````````````````````````````````````````````````````
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
````````````````````````````````````````````````````````````````````````

do you want it to look like this???

````````````````````````````````````````````````````````````````````````
# examples
#
# title		Windows Vista
# root		(hd1,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
``````````````````````````````````````````````````````````````````````````

before I save it I wanna make sure this is what you need it to look like..

Thanks I will wait for a response..

---

### Post by yeaitsdark on 2009-07-11
I think this tutorial should help you.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I personally find editing the BCD file... very annoying. Beware messing that up, sometimes "repair" on the Windows CD will not solve that issue as it won't sometimes detect any errors. (There are ways but, it's just not as easy as editing the menu.lst)

Note once you do get Grub installed and working, make sure you check the mapping correctly in your menu.lst file. root=/dev/mapper/Mapper_Device_ID. Else Grub will boot the kernel, and then it will have no idea where it's files are.

On the Live CD etc, verify the proper locations and partitions etc (gparted for instance), and write the names down for later reference.

Hope that helps a bit.

---

### Post by NastyNative on 2009-07-11
I dont know why but that link keeps on sending me to a reply for this same thread ...

check it out..

---

### Post by yeaitsdark on 2009-07-11
sorry my bad link is [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by NastyNative on 2009-07-11
Remember I do not want to install linux on my raid..

I can now log into Vista or Ubuntu by changing the hard drive boot 
prioroty..

What im having trouble doing is getting the Splash screen..

I have tried Easybcd which alters the Vista loader to 
recognize the ubuntu grub loader but it doesnt recognize it.

Im still waiting for JEB to answer my last post before 
I edit the menu.lst and save it...

---

### Post by yeaitsdark on 2009-07-12
> **NastyNative said:**
> Remember I do not want to install linux on my raid..

In linking that tutorial I was hoping to give you insight into the whole process. The workings of the software raid in regards to Grub. By extension I am suggesting installing Grub, not Ubuntu to your raid array.

If you are forced to disable the array in order to boot the 160GB drive, than.. well I don't much see the point. Hence, I would install Grub to the array and boot it that way.

If you don't want to do it this way, then you must follow the link Jebtrix gave you about editing the BCD file, as you will need Windows to boot your Linux. 

If you'd like to use Grub, then use the link I gave you and start from "Installing the Bootloader". 

If you are able to Boot the 160GB drive AND have the array active, (I'm re-reading your posts and not understanding whether or not you've achieved this), then you would still be following the link I gave you. The difference being is installing Grub into the 160 drive, but you must still map example: (hd1,0) to the dmraid map i.e dev/mapper/nvidia_myarray1.

I'm really trying to be as like simple and straight forward as I can be in explaining this other wise Grub just booting straight out (hd0,0) will be unreadable data on the actual drive and not the array.

---

### Post by NastyNative on 2009-07-12
Ok I understand what you are saying.

Unfortunately im so new to this that an insight 
just confuses me.

I can boot from either the 160 WD drive with the Ubuntu installation 
or I can boot from my raid 0 with vista.
of course I have to do it by switching the boot priority 
and since my family also uses my computer Im afraid
of then entering the bios since they really dont know much.

How do i exactly do this and if your not sure how to do 
it exactly I rather wait for a response from some one 
that has done, Which im sure there has to be some one with the 
same setup out there.

The link you sent me is very confusing and its got  
a warning to save all my files, this is what im 
afraid of is screwing up my RAID setup.

I dont understand all of this code and I do it because it 
tells me not because I understand it.
Like I said before Im in no rush to get this working 
im more concern about understanding and do in it correctly.

My one question, if i install a Fake raid..
will the fake raid software now run my 
current Raid setup with windows and not my nvidea
software??

Has any one else done the same thing im trying to 
do and can please guide me.

This is what I understand so far.
You need a boot loader installed on the partition 
so that the splash screen can recognize the OS's

Because I have Linux as the priority boot drive I need 
to install a linux raid software so that the splash
screen can be aware of the vista installation.
This is the part im having trouble doing.

Can I mess up my raid setup?

Im sorry if im so ignorant to all of this but like everything else 
you gotta do it to understand it.

Thanks for your help

---

### Post by yeaitsdark on 2009-07-13
It's quite all right. I very much understand your hesitation. My computer is setup is very similar to yours. I have an EVGA motherboard (so it's an NVidia chipset). I run two WD Raptors in a raid 0, via the "fake or software" raid device included on the motherboard.

Windows Vista detects this array as does Windows 7 without issue. With an XP installation (which I also have on my array), I had to inject the raid drivers into the installation before installing. I also run Ubuntu from the raid array as well. 

So I have gone through this process several times. To answer your questions,
> **NastyNative said:**
> My one question, if i install a Fake raid..
will the fake raid software now run my
current Raid setup with windows and not my nvidea
software??

Windows uses the driver from Nvidia to access the raid array. Linux/Ubuntu uses dmraid(software) to access the raid array. So under no circumstance does either operating system take "control" of the array. So nothing to worry about there. It simply uses dmraid or nvidia drivers to use the array, and uses your CPU to compute the algorithms to write to the array.
> **NastyNative said:**
> 
This is what I understand so far.
You need a boot loader installed on the partition
so that the splash screen can recognize the OS's

By splash screen, you mean Grub right? Yes. Grub must know where to look for (in your case Vista).

Do for the me the following so I can prepare more concise and tailored directions for you. Boot either Ubuntu on your PC, or boot a Live CD. Then I'd like the outputs from these commands.

This will list all your drives:
```
sudo fdisk -l
```

If you are doing this from a Live CD you will also need to install dmraid.
```
sudo apt-get install dmraid
```

This will set active the partitions on the array. It will most likely say "/dev/mapper/nvidia_blahblah is already active". Just paste that to me.
```
sudo dmraid -ay
```

I presume you only have 1 partition on your raid array for Windows. Then you have 2 partitions on your 160GB hard drive for Linux and it's swap. This will just help me give you a better idea of your setup so that I can give you a better idea on how to set it up so you don't have to always go into the Bios just to pick Windows or Ubuntu.

I hope this gives you a better grasp of what's going on. In short what we will do is modify grub on your single hard drive to boot Linux and Windows. This will not affect your current array at all. Let me know those outputs and I'll put something together for you to try.

---

