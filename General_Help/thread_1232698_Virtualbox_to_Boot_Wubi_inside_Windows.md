---
title: "Virtualbox to Boot Wubi inside Windows"
date: 2009-08-05
forum: General Help
---

### Post by mbeichorn on 2009-08-05
This is a poorly understood subject with no apparent documentation...

I am attempting to use Virtualbox on Windows to boot up a Wubi install of Jaunty I believe that it is possible as I have come across a smattering of posts saying it is possible and has been done. I want the flexibility of being able to boot solely into Ubuntu or Windows but still being able to call the other up as a VM without rebooting. Does anyone actually know how to accomplish this feat?

For the record:
Colinux & varients are not possible as I require an amd64 OS for hardware reasons.
I spent several hours doing research but only found instructions for Ubuntu hosting a Win partition in VBox.
[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

I am also open to partitioning Ubuntu separately, but would prefer to keep it as Wubi.
I could also survive if it was VMware and not VirtualBox.

---

### Post by Scotty Bones on 2009-08-05
I'm not sure if what you are attempting to do is possible.

However, this entry in the VB user manual might be of some use.
9.10.2 Access to individual physical hard disk partitions (p135)

I have never tried a setup like this, so try at your own risk. I don't think this would work with wubi though.

good luck.

---

### Post by mbeichorn on 2009-08-06
Alright, I give up for now. I am going to do a normal install (non-wubi) and use the virtualbox rawdisk abilities. It would be nice to know how to get virtualbox to recognize the .disk file or to mount it in windows and use rawdisk from there. I am going to have to wipe and reinstall in Nov when I get a school copy of Win7 so I will use a seperate partion for now, but in general when dual-booting I prefer wubi. I hope someone comes up with an answer, after all Vbox has an OSE and wubi is open source so there should be a way to hack around the difference. (I am a lowly rocket-science student not a programmer).

---

### Post by xcollin on 2009-08-12
i have come across a similar idea with damn small linux and some of the concepts may be helpful.
according to [http://damnsmalllinux.org/usb.html](http://damnsmalllinux.org/usb.html) you can boot dsl directly from a usb, or inside windows using qemu. i assume that this uses a qcow2 image since qemu uses qcow2 for virtual machine disk images. according to wikipedia's article on qcow,

"**qcow** images could be mounted under linux with mount option "offset" used. E.g. to mount a first (or single) partition from **qcow** image You need the command *mount /path/to/image.img /mount/path -o loop,offset=32256*."

you should be able to install ubuntu in a qcow2 image using qemu and run it as a vm as well as boot directly from it. this seems to me like the closest thing to using wubi.

---

### Post by horse_dung on 2010-04-26
I really don't see any technical issue with a VirtualBox VM booting a Wubi installed Ubuntu.  It would require an additional disk image that locates the ubuntu/disks directory and then loop mounts it/them and continues booting.

The interesting part will be getting Shared Folders working so that the VM can see the host's folders...  I'm going to play around with this now and will post back my results...

---

### Post by horse_dung on 2010-04-27
Okay, I've got it working.  Getting VirtualBox drivers into initrd and then tweaking the scripts to load was a bit of challenge.  I'll tidy it all up and then provide some instructions.

---

### Post by P4man on 2010-04-27
sounds interesting.. would this work with a non wubi install as well?

---

### Post by horse_dung on 2010-04-27
I'm pretty sure there are instructions out there on how to access raw disks in VirtualBox.  You can use the raw disk to boot up pretty much any other "real" operating system you've got installed.

What I've done here is create a super small virtual machine that consists of a mostly standard Ubuntu boot up, but which then uses Shared Folders to find and then mount the WUBI image.

In most other scenarios I'm not sure you'd need to go to these lengths (e.g. boot an .iso image) as support is already there in VirtualBox.  What Windows VirtualBox doesn't support (which frankly is silly) is the ability to say "this file I'm providing you with is a completely raw hard disk image... please boot it and treat it like the real thing...".

I've got a 64-bit version working rather nicely, if anyone wants it let me know (horse_dung[at]hotmail.com) otherwise I'll wait for 10.4 to come out, make sure the approach still works and then post instructions/appliances files somewhere.

---

### Post by horse_dung on 2010-05-02
Okay, I've got WUBI Ubuntu 10.04 LTS running from Windows 7 under VirtualBox 3.1.6 on 64-bit hardware.  I could do with some BETA TESTERS that are willing to try this out.

If you want to try this as an end user then:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download the .ovf and .vdmk files.

2.  From virtual box click on File - Import Appliance and point to the .ovf file you downloaded

3.  Edit the virtual machine settings, under the display section, change video ram to 32M

4.  Edit the virtual machine settings, under shared folders, add new shared folder called "/vbox-wubi" that points to the root of the hard disk which has WUBI installed.  For most people this will be "C:\".  Note that both the name and the directory examples given here shouldn't have the quotes entered, but the slashes should be entered as seen.

5.  Fire up the Virtual Machine and wait for your WUBI Ubuntu 10.04 to appear.



If you want to try this as a developer/hacker:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download make.image

2.  Beware:  the script calls various tools like GRUB and Parted and, while it would be very unlikely, there is still potential for this script to destroy your Ubuntu install, your Windows install, any other operating systems you have installed and you credit rating.

3.  Run ./make.image as the root user to build a VirtualBox virtual machine.

If the script doesn't work then run it again with "-v -v" to get more output and post back.  Enjoy...!  This should work fine for 32-bit.  This definitely won't work with 9.10 or earlier as I had to make some changes to get it to work with 10.04.  This will probably break whenever the host gets a new kernel and you will need to re-run the setup script.

---

### Post by horse_dung on 2010-05-03
Sorry, that URL should have read: [http://drop.io/vboxwubi]("http://dropbox.io/vboxwubi")

---

### Post by P4man on 2010-05-03
Neither url works for me. (Not that I intend to test at this point, though it looks interesting)

---

### Post by antcodd on 2010-05-03
Hi,

I happened to tinkering with this idea today too as I had been wanting to try it for a while. I tried your solution (and thought of a similar idea the other way around by mounting the vdi in a native small Linux but had no idea how to make it work). I tried it with a 32bit Wubi install and had to run the virtual machine with Ubuntu 64bit as the OS choice to get it to boot at all but the mouse and keyboard don't work once booted - probably something to do with trying to run 32bit drivers on your 64bit kernel or something. I suspect it works on running your script from 32bit but I didn't try. Your solution is probably easier for the end user to set up as it is just click and go. Have you looked at the performance, I was under the impression shared folders were rather slow?

I continued with the another, much simpler method that I was trying to get working before finding this thread and managed to make it work :D:

It is possible to write a VMDK disk description file that references the raw Wubi image and make Virtualbox try to boot off it (why Virtualbox doesn't support booting off raw images by default I'll never understand). I pieced together instructions I found for making Ubuntu boot in virtualbox off a raw partition ([http://cargowire.net/articles/seamlessubuntuwindows]("http://cargowire.net/articles/seamlessubuntuwindows")) and instructions I found to make the raw image work with a VMDK file ([http://blogs.techrepublic.com.com/networking/?p=148]("http://blogs.techrepublic.com.com/networking/?p=148")).

To get the disk descriptor working you need to know the number of sectors, cylinders (seems to be 0), sectors per track (63 for me), heads (which seems to be 255 always for images) which can be found using ```
fdisk -l <imagefile>
``` on a linux machine (I just used my old Ubuntu virtual machine - I doubt it works from within wubi since it is booting off that file). I'm not sure how to find out the number of sectors as I got it from when I tried the trial of a program called WinHex referenced in the disk descriptor instructions but it seems only the paid one provides all the information (though it did give sector count).

```
# Disk DescriptorFile
version=1
CID=fffffffe
parentCID=ffffffff
createType="monolithicFlat"
# Extent description
RW <sector count> FLAT "root.disk"

# The Disk Data Base
#DDB
ddb.adapterType = "ide"
ddb.geometry.sectors = "<sectors per track>"
ddb.geometry.heads = "<heads>"
ddb.geometry.cylinders = "<cylinders>"
```

VirtualBox seems to have modified the file and cleared it up with its own sector heads and cylinders and things and added various things so they may not be necessary (and hopefully I remembered correctly what the file was like originally).

I then used the latest version of [Super Grub Disk]("http://www.supergrubdisk.org/") and its auto option was able to boot into Wubi (I tried following instructions from the ubuntu inside windows post for getting a grub boot iso but I must have been doing something wrong like using too old a version of grub without ext4 support or something).

It should be possible to create a minimal Grub 2 iso which just tries to boot (hd0)/vmlinuz and (hd0)/initrd.img (note the lack of a partition number and that there are symlinks that presumably point to the current kernel) but I do not know how to do this and couldn't find any information how to do it. It might even be possible to fake bootsector grub 2 by using another image before the Wubi one in the disk descriptor as in the example disk descriptor in what seems to be the official file format documentation [http://www.vmware.com/app/vmdk/?src=vmdk]("http://www.vmware.com/app/vmdk/?src=vmdk") (I found it through web search).

The only problem I have is the swap file doesn't work since it is trying to load it from /ubuntu/disks - I haven't tried to fix that yet. Everything else seems to work (including Compiz, seamless mode, guest additions don't seem to conflict etc.) apart from some minor issues with VirtualBox starting with a huge window due to Ubuntu remembering the native screen resolution.
 I'm fairly inexperienced with Linux so I don't think I will be able to help much with questions or maintain this (it seemed but I'll do my best and hopefully someone can pick up the idea and make it easier to use :). It would be great to see something similar included in Wubi someday.

Using Windows 7 32bit, VirtualBox 3.1.6, Ubuntu 10.04 32bit

ps: the second drop.io link doesn't work because the URL still points to dropbox.io. The correct link is  [http://drop.io/vboxwubi]("http://drop.io/vboxwubi")

---

### Post by horse_dung on 2010-05-04
> **antcodd said:**
> Hi,

probably something to do with trying to run 32bit drivers on your 64bit kernel or something. I suspect it works on running your script from 32bit but I didn't try.


There are usually far more serious problems when mixing 32/64-bit... I had problems with AppArmor and the system failed to make to a graphical login console.

> **antcodd said:**
> 
Your solution is probably easier for the end user to set up as it is just click and go. Have you looked at the performance, I was under the impression shared folders were rather slow?


The performance was fine, although I haven't done any performance tests... Its probably about half the speed of native, I had originally put that down to it being a VM but it could well be the reduced disk I/O from using a loop onto of vfat onto of Shared Folders.

> **antcodd said:**
> 
It is possible to write a VMDK disk description file that references the raw Wubi image and make Virtualbox try to boot off it (why Virtualbox doesn't support booting off raw images by default I'll never understand). I pieced together instructions I found for making Ubuntu boot in virtualbox off a raw partition ([http://cargowire.net/articles/seamlessubuntuwindows](http://cargowire.net/articles/seamlessubuntuwindows)) and instructions I found to make the raw image work with a VMDK file ([http://blogs.techrepublic.com.com/networking/?p=148](http://blogs.techrepublic.com.com/networking/?p=148)).


I tried this approach but again the system failed to boot because it couldn't find /ubuntu/disks/usr.disk.  You could use two raw vmdk disk images, but then you would need to change the configuration in /etc/fstab and I don't want the VM version to have a different configuration than the real WUBI Ubuntu.

> **antcodd said:**
> 
I then used the latest version of [Super Grub Disk]("http://www.supergrubdisk.org/") and its auto option was able to boot into Wubi (I tried following instructions from the ubuntu inside windows post for getting a grub boot iso but I must have been doing something wrong like using too old a version of grub without ext4 support or something).


Take a look at the make.image script... one of the things it does is install GRUB to a virtual hard disk image.

> **antcodd said:**
> 
The only problem I have is the swap file doesn't work since it is trying to load it from /ubuntu/disks - I haven't tried to fix that yet. Everything else seems to work (including Compiz, seamless mode, guest additions don't seem to conflict etc.) apart from some minor issues with VirtualBox starting with a huge window due to Ubuntu remembering the native screen resolution.


The swap disk doesn't work using my method either because Shared Folders doesn't correctly report that the file is a single contiguous chunk which is needed.  There's a number of problems with using a VDI / VMDK file which have caused no end of hassles, so I might change it to be ISO image based...!

---

### Post by Jose Catre-Vandis on 2010-05-04
> **horse_dung said:**
> Sorry, that URL should have read: [http://drop.io/vboxwubi]("http://dropbox.io/vboxwubi")

You mean  [http://drop.io/vboxwubi](http://drop.io/vboxwubi)  :)


Any chance of a ovf/vmdk for Karmic ?

---

### Post by horse_dung on 2010-05-04
Sure... I'm currently working on doing a 32-bit image for lucid... then I'll work on images for karmic...

---

### Post by Jose Catre-Vandis on 2010-05-04
Thanks horse_dung :)

---

### Post by fedemart on 2010-05-04
Hey horse_dung, thanks for sharing, what you are trying to do would be great for many windows users.

My results:

I followed your instructions but didn't work. I ran the VM but I only see a black screen. I am running windows 7 home premium, 64bits and I had installed wubi before on c://

---

### Post by fedemart on 2010-05-04
I made a mistake, I didn't havve virtualization enables, that's why I got the black screen.

Now the VM tries to start, but I get an error. I took a screenshot.

---

### Post by steveneddy on 2010-05-04
I would not use Wubi even if you paid me.

Either dual boot or install Ubuntu and install Windows in the VM.

---

### Post by fedemart on 2010-05-05
Sorry, I just realized that my wubi installation included Ubuntu 9.4... I will see if I update it to 10.4.

---

### Post by horse_dung on 2010-05-05
32-bit version for lucid is now available at drop.io/vboxwubi...

Performance tests:  performance on two of my three test machines is fine, about 10% slower than native which is pretty much standard for virtualisation.

My last test machine is a Atom processor based netbook.  While it works, it is rather slow - it took about 3 minutes to boot and then its about 100% slower than native.

I'll start working on 9.10 next...

---

### Post by gksmithlcw on 2010-05-16
> **horse_dung said:**
> Okay, I've got WUBI Ubuntu 10.04 LTS running from Windows 7 under VirtualBox 3.1.6 on 64-bit hardware.  I could do with some BETA TESTERS that are willing to try this out.

If you want to try this as an end user then:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download the .ovf and .vdmk files.

2.  From virtual box click on File - Import Appliance and point to the .ovf file you downloaded

3.  Edit the virtual machine settings, under the display section, change video ram to 32M

4.  Edit the virtual machine settings, under shared folders, add new shared folder called "/vbox-wubi" that points to the root of the hard disk which has WUBI installed.  For most people this will be "C:\".  Note that both the name and the directory examples given here shouldn't have the quotes entered, but the slashes should be entered as seen.

5.  Fire up the Virtual Machine and wait for your WUBI Ubuntu 10.04 to appear.

I got this up and running with no issues. The only problem I have now is that I don't appear to have any of the VBox video drivers installed. I keep getting a warning about a Low-Graphics Mode.

Is there a quick and easy way of getting these drivers installed?

---

### Post by horse_dung on 2010-05-20
While running Ubuntu inside of Virtual Box you need to click on the "Devices" menu and select "Install Guest Additions...".  This will connect up a virtual CD-ROM with the device drivers on them.  If it doesn't appear look in the "Places" menu at the very top of the screen for "VBOXADDITIONS_....".

You need to run the "autorun.sh" script as the root user.  If you hit any problems then take a look at the VirtualBox documentation on installing Guest Additions.

Mike

FYI: Sorry for the delay for those people waiting for the older Ubuntu flavours.  I'm looking at changing everything around to use CD-ROM images rather than virtual HDD images.

---

### Post by sungohan on 2010-05-21
I have a question, what is the downloaded .vmdk file for?
In your instruction, you did not mention where to use .vmdk file.

And my ubuntu 10.04 is installed on H:\, so I shared H:\
I am using 32 bit windows 7.

And I got an error while starting the virtual machine on black screen.

The error picture is in here,
[http://my.picresize.com/M6GQSHZCTE](http://my.picresize.com/M6GQSHZCTE)




> **horse_dung said:**
> Okay, I've got WUBI Ubuntu 10.04 LTS running from Windows 7 under VirtualBox 3.1.6 on 64-bit hardware.  I could do with some BETA TESTERS that are willing to try this out.

If you want to try this as an end user then:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download the .ovf and .vdmk files.

2.  From virtual box click on File - Import Appliance and point to the .ovf file you downloaded

3.  Edit the virtual machine settings, under the display section, change video ram to 32M

4.  Edit the virtual machine settings, under shared folders, add new shared folder called "/vbox-wubi" that points to the root of the hard disk which has WUBI installed.  For most people this will be "C:\".  Note that both the name and the directory examples given here shouldn't have the quotes entered, but the slashes should be entered as seen.

5.  Fire up the Virtual Machine and wait for your WUBI Ubuntu 10.04 to appear.



If you want to try this as a developer/hacker:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download make.image

2.  Beware:  the script calls various tools like GRUB and Parted and, while it would be very unlikely, there is still potential for this script to destroy your Ubuntu install, your Windows install, any other operating systems you have installed and you credit rating.

3.  Run ./make.image as the root user to build a VirtualBox virtual machine.

If the script doesn't work then run it again with "-v -v" to get more output and post back.  Enjoy...!  This should work fine for 32-bit.  This definitely won't work with 9.10 or earlier as I had to make some changes to get it to work with 10.04.  This will probably break whenever the host gets a new kernel and you will need to re-run the setup script.

---

### Post by Jose Catre-Vandis on 2010-05-21
> **horse_dung said:**
> 
FYI: Sorry for the delay for those people waiting for the older Ubuntu flavours.  I'm looking at changing everything around to use CD-ROM images rather than virtual HDD images.

No worries, from the look of things it will be worth the wait!

---

### Post by Jucali on 2010-06-05
> **horse_dung said:**
> Okay, I've got WUBI Ubuntu 10.04 LTS running from Windows 7 under VirtualBox 3.1.6 on 64-bit hardware.  I could do with some BETA TESTERS that are willing to try this out.

If you want to try this as an end user then:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download the .ovf and .vdmk files.

2.  From virtual box click on File - Import Appliance and point to the .ovf file you downloaded

3.  Edit the virtual machine settings, under the display section, change video ram to 32M

4.  Edit the virtual machine settings, under shared folders, add new shared folder called "/vbox-wubi" that points to the root of the hard disk which has WUBI installed.  For most people this will be "C:\".  Note that both the name and the directory examples given here shouldn't have the quotes entered, but the slashes should be entered as seen.

5.  Fire up the Virtual Machine and wait for your WUBI Ubuntu 10.04 to appear.



If you want to try this as a developer/hacker:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download make.image

2.  Beware:  the script calls various tools like GRUB and Parted and, while it would be very unlikely, there is still potential for this script to destroy your Ubuntu install, your Windows install, any other operating systems you have installed and you credit rating.

3.  Run ./make.image as the root user to build a VirtualBox virtual machine.

If the script doesn't work then run it again with "-v -v" to get more output and post back.  Enjoy...!  This should work fine for 32-bit.  This definitely won't work with 9.10 or earlier as I had to make some changes to get it to work with 10.04.  This will probably break whenever the host gets a new kernel and you will need to re-run the setup script.
Hey horse_dung,

It's great what you did; I will find this VB version of Wubi really useful... that is, if I ever get it to work.

I followed the instructions you posted but when I try to launch the machine, I get a black screen with nothing but a static cursor on it... that's it. It doesn't boot or change.

I was wondering if anyone could give me a clue as to what might be wrong; I've been playing with the settings and I've checked all of them and it's still not working.

I'm using Windows 7, with the 64-bit files.

Thank you!

---

### Post by codemastercode on 2010-06-11
Hello,

I've been trying to follow your instructions for running Wubi Ubuntu on VirtualBox.
I'm running 10.4 Ubuntu 64-bit, and VirtualBox is running on Windows 7 Professional.
I downloaded the "vbox-wubi-lucid-64.ovf" and "vbox-wubi-lucid-64.vmdk"
I changed the settings accordingly, and tried it, but I just shows me a blank screen.
I gave it 1500 RAM, and I'm not sure how long it should take to startup...any estimates?

---

### Post by SomeoneElse.jp on 2010-07-05
I got the install to work splendidly with Ubuntu, however I'd rather be running LinuxMint which uses a variant of wubi, unfortunately the LinuxMint version of Wubi uses the x:\LinuxMint\ directory instead of the x:\ubuntu\ directory to store the disk images etc. I figured that there would be some way to edit the scripts inside the host virtual machine but try as I might I can't find, and thus launch any editors... I've tried the common suspects, but I admit I may be missing something vital.

Is there any way to get a version of the host virtual machine which has a text editor on it? or perhaps a modification of the script which allows you to specify the full path to the wubi install rather than just the host drive's root?

thoughtfully perplexed

---

### Post by codemyster on 2010-08-02
I'm having a bit of trouble with this now.

I imported the appliance and it showed the settings, and when I hit "Finish", it threw an error about the hard disk not existing. So I copied the virtual disk to the folder it was complaining about, and then received an error saying "Failed to import appliance: File (path to vhd) **exists**". So it doesn't work either way I try it. 

Is there a solution to be had?

EDIT: Nevermind, I'm an idiot. I misread the path that it was saying didn't exist. Everything works now. :)

---

### Post by danmiddle2 on 2010-08-17
> **horse_dung said:**
> Okay, I've got WUBI Ubuntu 10.04 LTS running from Windows 7 under VirtualBox 3.1.6 on 64-bit hardware.  I could do with some BETA TESTERS that are willing to try this out.

If you want to try this as an end user then:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download the .ovf and .vdmk files.

2.  From virtual box click on File - Import Appliance and point to the .ovf file you downloaded

3.  Edit the virtual machine settings, under the display section, change video ram to 32M

4.  Edit the virtual machine settings, under shared folders, add new shared folder called "/vbox-wubi" that points to the root of the hard disk which has WUBI installed.  For most people this will be "C:\".  Note that both the name and the directory examples given here shouldn't have the quotes entered, but the slashes should be entered as seen.

5.  Fire up the Virtual Machine and wait for your WUBI Ubuntu 10.04 to appear.



If you want to try this as a developer/hacker:

1.  Go here [http://dropbox.io/vboxwubi](http://dropbox.io/vboxwubi) and download make.image

2.  Beware:  the script calls various tools like GRUB and Parted and, while it would be very unlikely, there is still potential for this script to destroy your Ubuntu install, your Windows install, any other operating systems you have installed and you credit rating.

3.  Run ./make.image as the root user to build a VirtualBox virtual machine.

If the script doesn't work then run it again with "-v -v" to get more output and post back.  Enjoy...!  This should work fine for 32-bit.  This definitely won't work with 9.10 or earlier as I had to make some changes to get it to work with 10.04.  This will probably break whenever the host gets a new kernel and you will need to re-run the setup script.

Works perfectly for me, this will be extremely useful, thank-you!

---

### Post by danmiddle2 on 2010-08-21
A brief word of warning to anyone using this - it works perfectly, but my advice is always install your updates from within the REAL system. I have just installed some updates from within the VBOX version and I now can't boot into the system outside of VirtualBox.

---

### Post by larryboyadm on 2010-12-24
These links do not work does anyone have a way to get to the original files.

---

### Post by Denizen08 on 2011-06-10
I would also like to know how to get this working. TTY, this is extremely useful especially for us who have productivity tools in both Windows and Linux worlds. :)

---

### Post by Tralce on 2012-01-08
Any chance on some new links to vboxwubi? drop.io doesn't seem to exist... or something... and I'd love to tinker with this.

---

### Post by aHcVolle on 2012-12-10
Please anyone?

---

### Post by oldos2er on 2012-12-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

