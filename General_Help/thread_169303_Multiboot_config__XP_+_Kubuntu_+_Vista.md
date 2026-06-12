---
title: "Multiboot config : XP + Kubuntu + Vista"
date: 2006-05-02
forum: General Help
---

### Post by davidbubu on 2006-05-02
Hello there!
Im quite new in Linux world, so I need some assistance from Linux/GRUB gurus.
I have a machine with one HD (160 GB) - 4 partitions.
 First I installed WinXP on C: (NTFS) , I left D: drive empty (NTFS), E: I used to install Kubuntu and have aslo F(NTFS) drive, using it from Windows. I instaled Kubuntu without any problem , however later I messed up with swap partition - created 2 swaps and use only one actually. List of my hd's is like this : (see attached image).
 I have nice GRIUB multiboot and can load either WinXP or Kubuntu. BTW I dont remember if I have GRUB on MBR or or on separate partition. So far so good. Now I have to install Windows Vista CTP on my empty D: drive. As far as I understand Vista will use its own boot loader which is incompatibale with GRUB/LINUX. My questions is : is there any way how to have all 3 OS working on one machine? If not is there any way to safely remove Kubuntu , install Vista and then try to reinstall Kubuntu? I MUST preserve my WinXP as is ( Im working on it) anyway. How can I determine where GRUB is located : MBR or any other place? I can temporarily sacrifice my Kubuntu just to have Vista installed ( need it fot some RnD task). 
I attaching my menu.list for GRUB loader : 
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Any help wil be grtaly appreciated. 
David.

---

### Post by trotski on 2006-05-02
Essentially, if Vista is anything like XP, it'll remove GRUB from the MBR.  You'll have to use your Kubuntu disk or KNOPPIX, etc. as a rescue disk.  From there you can put GRUB right back into the MBR.  THEN, you'd duplicate the Windows entry in your menu.list for Vista on D (/dev/sda2).  It should be root (hd0,1).  I guess that'd do it.  I've not been following Vista all that much, though.

---

### Post by Alienist on 2006-06-09
Just to document my own experience with Dapper/Xp/Vista:

I had a working dual boot with Dapper and XP to which I added the Vista beta on a partion on my slave drive. This eliminated my grub, of course, although I didn't really think about it at the time. After a lot of searching someone recommended using Super Grub Disk which is included on the Ultimate Boot CD. This worked quite easily. Then I spent another good chunk of time trying to figure out how to add Vista to my grub menu. Someone else offhandedly mentioned that the Vista loader is actually under the XP option in the grub menu. It booted and all is well. Triple booting *is* possible.

---

### Post by Grog140 on 2006-06-09
If you do a clean install then Grub doesn't pick up the Vista partition automatically.

I started over today and finally installed ubuntu and then realized there was no option to boot from :(

---

### Post by catlett on 2006-06-10
Your windows boot loader will be able to boot vista. If you don't mind reinstalling. Install vista. The windows bootloader will be inbstalled. It will have an entry for XP and Vista. The windows loader has no problem booting to other win installs.
You can mess around with your grub menu but this is easiest. Reinstall kubuntu (or Ubuntu) with the ALTERNATE INSTALL CD. When you gey to the grub installation part it will ask you if you want to install grub to the mbr. Choose no. It will then give you an option to put it on a aprtition or a floppy. Choose the floppy.
Grub will be installed on the floppy. Now your computer will be setup as follows. When you start your computer it will boot to the window bootloader menu. This looks very similar to grub. Just a plain text menu. You will have an XP and a Vista option.
If you want Ubuntu put the floppy in the floppy drive and start your computer. The computer will boot to the floppy (you shouldn't have to change your bios, most computers do the A drive first) The grub menu will appear. Use it like you normally do.

---

### Post by undertherift on 2006-06-10
I spent the night battling this problem.

Apparently Vista does not use NTLDR, so you need to have a work around for that. 

I just recently found this post.
[http://forums.microsoft.com/MSDN/ShowPost.aspx?PostID=335542&SiteID=1](http://forums.microsoft.com/MSDN/ShowPost.aspx?PostID=335542&SiteID=1)

I'm in the process of reinstalling everything, and then i'm going to work on this.

i'm using Kubuntu, winxpsp2, and vista beta 2.  (and i want to use grub)

oh yeah, and
i have an 80 gig hard drive.. i want to make a 40 gig vista partition, 20 gig xp partition, X sized linux, Y free space... (for adittional installs... OSX maybe?)


UPDATE:
I've got the triple working in a fashion.  Grub works, and has kubuntu and Windows listed.  When i select windows, it takes me to the windows boot loader, and then i ahve to select XP or Vista.  

Not quite what i wanted, but i guess it works.

---

### Post by Grog140 on 2006-06-10
[QUOTE=catlett]Your windows boot loader will be able to boot vista. If you don't mind reinstalling. Install vista. The windows bootloader will be inbstalled. It will have an entry for XP and Vista. The windows loader has no problem booting to other win installs.
You can mess around with your grub menu but this is easiest. Reinstall kubuntu (or Ubuntu) with the ALTERNATE INSTALL CD. When you gey to the grub installation part it will ask you if you want to install grub to the mbr. Choose no. It will then give you an option to put it on a aprtition or a floppy. Choose the floppy.
Grub will be installed on the floppy. Now your computer will be setup as follows. When you start your computer it will boot to the window bootloader menu. This looks very similar to grub. Just a plain text menu. You will have an XP and a Vista option.
If you want Ubuntu put the floppy in the floppy drive and start your computer. The computer will boot to the floppy (you shouldn't have to change your bios, most computers do the A drive first) The grub menu will appear. Use it like you normally do.[/QUOTE]

That is pretty clever. But alas, I do not have a floppy drive (newish Laptop). So it looks like I am going the difficult way.

---

### Post by jrd on 2006-06-11
I tri boot XP,Vista,and Kubuntu. When Vista wipes grub just put the install cd back in and go through the motions till you get to the partition part, select the correct formats (root for your current root ect..) but do not partition. Then it will say something about a dirty install but just say no. then skip down the list to the "install grub" part. Let it install grub and reboot. Btw, to boot Vista from grub just choose the xp option, then the Vista boot loader will ask if you want to boot XP or Vista.

---

### Post by johnniecarcinogen on 2006-06-13
Vista beta 2 does not boot the same way as XP and the previous beta versions of Vista.

JRD what version of Vista do you have installed?

---

### Post by jrd on 2006-06-14
I have "Beta 2 Build 5384". Also, while were talking about Vista, Does it take forever to boot and shutdown on everybodies computer or is it just me?

---

### Post by EndGame on 2006-06-14
[QUOTE=jrd]I have "Beta 2 Build 5384". Also, while were talking about Vista, Does it take forever to boot and shutdown on everybodies computer or is it just me?[/QUOTE]

Actually, in my case anyhow, Vista boots much quicker than XP Pro/X64 and Ubuntu............

Also, I've tried several ways to get my triple boot going including those listed above to no avail......ProOne is about to come out with a new build of "Vista Bootloader" which will allow Linux/Vista to live happily together so I've decided to be patient.

---

### Post by jrd on 2006-06-14
So after reinstalling grub, you boot and select XP, then it just goes strait to XP? Or does it even offer XP? Also, what are you system specs? Maby i'm just not up to Vista standards. I have an Athlon 2800, 512MB of ram, and a Nvidia MX4000 video card.

---

### Post by juu801 on 2006-06-15
I've been having issues with this the past several days. I installed Vista knowing it would kill my mbr. I figured it would be a simlpe reinstall of grub. 

I followed some of the suggestions in this thread. When I booted from the live cd and tried putting grub back in the mbr the system would hang up. It would check the DVD drives to see if the was any media and then when it got to where it should have booted off of the hard drive it just sat there. I noticed my master DVD drive had the LED lit. I tried going through the install and just installing grub. It yelled at me and said it couldn't finish. 

I then grabbed my Mepis Live CD and reinstalled grub. The grub menu that it created only had an entry for Windows. If I chose it I got the menu that Vista created listing the two options of XP and Vista. I had backed up my previos grub menu before starting so I copied it over the new one after backing that up for comparison. 

The menu came up but if I selected any of the Ubuntu options (I have three kernel verisons I haven't gotten around to trimming down) Windows XP and I tried adding one for Vista they would all return me to the menu except Vista would say the filesystem was unrecognized and jsut hung after that. 

I changed the xp setting to reflect the entry that Mepis had made. Now I have  my choice of Windows through the menu Vista installed but I can't boot Ubuntu. Any ideas/suggestions would be greatly appreciated. I was near completion of customizing Ubuntu the way I wanted it and I'd hate to have to start over.:confused:

---

### Post by jrd on 2006-06-15
> It yelled at me and said it couldn't finish
It did that to me too. After that scroll down the list of intall steps until you get to the grub part, then intall grub and reboot, Just skip everything between the partiton step and the grub step. Mine is not a live cd though, maby thats the problem.
Hope this helps.

---

### Post by juu801 on 2006-06-15
> It did that to me too. After that scroll down the list of intall steps until you get to the grub part, then intall grub and reboot, Just skip everything between the partiton step and the grub step.

That's what I did. I got the menu of the install steps when straight to grub. It spit out a bright red screen saying the install of grub had failed. It then returned me to the menu of install steps.

I've discovered that I can kinda boot into Ubuntu. If I choose the normal selection I'm returned to the grub menu instantly. If I choose the recovery mode selection it boots to a command line. I've tried re-installing grub this way and it still does the same thing.

So, I have grub installed I just can't get the entries for Ubuntu to work. If I had put them in by hand I would assume it was me. But, since I backedup my menu.lst before any of this these are the entries that Ubuntu made and were working fine prior to installing Vista.

---

### Post by juu801 on 2006-06-16
Ok I can boot into Ubuntu. I started playing around with the entries in the menu and by deleting the line that contained "savedefault" it boots fine now. I'm not quite sure what this option does but I don't seem to need it and I can use Linux again yeah!

Old Entry
```
title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
[COLOR="Red"]savedefault[/COLOR]
boot

```

New Entry
```
title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
boot

```

---

### Post by longinus on 2006-06-17
I installed all the systems the same way.. first XP, than Ubuntu, and now Vista. I lost the MBR as I should, and tried some methods to restore the grub. For a quick solution, you can use the super grub boot CD. It will find your old grub menu, and show it to you. Works fine.

But to get a permanent solution, I booted with Ubuntu live CD, and restored grub with the comands..

# grub
# root (hd0,5) -- for mine partition, of course.
# setup (hd0)

It worked fine...  now when I enter the Windows XP option in grub, I see the Vista boot loader, and can choose vista or xp.

Now the only thing left to figure out is how to remove the Vista boot loader if I want to delete vista partition and just have ubuntu/XP. :-({|=

---

