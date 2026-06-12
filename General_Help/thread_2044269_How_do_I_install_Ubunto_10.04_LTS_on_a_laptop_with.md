---
title: "How do I install Ubunto 10.04 LTS on a laptop without a CD/DVD and No Network"
date: 2012-08-19
forum: General Help
---

### Post by Nap_BlownApart on 2012-08-19
Hi,
  This is not a duplicate thread.
  I think I was taking the wrong approach before.

  What I would like to do is install Ubuntu 10.04 LTS Server onto a Laptop I have.  The problem is that my laptop does not have a CD Drive, so I cannot use the CD.

  To overcome this, I want to install it from a USB Drive.  I don't want a Live USB Install, I actually want to install the OS on the Laptop.

  I am having a lot of difficulty finding a guide that explains how to do this.  I've tried Unetbootin-windows and USB-creator but can't get them to work for me. I've even mounted the ubuntu-10.04.4-server-i386.iso on my laptop (which currently has windows 7 on it) as a drive using PowerISO but it won't let me autoplay it.

  My BIOS is able to boot from a USB drive, so that is not a problem.

  Can someone PLEASE point me to a guide that is WELL written that I can follow.

Best regards,
Nap

---

### Post by Zukaro on 2012-08-19
You use a LiveUSB to install Ubuntu.  On a CD it's a LiveCD.  All that means is you can use the OS from the USB or CD before you install the full OS.

Without Internet connection pretty much the only thing you wont have is the MP3 codec and a few other things like that (and updates).  You can install those later though if you need them.


You can use this to get the ISO onto a USB:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by Nap_BlownApart on 2012-08-19
@Zukaro,  thnx for trying.  But I'm having the same problem I had when I tried unetbootin. (Just like the other thread I started.)

Why is UBUNTU so STUPID.  I don't have a CD, that's why it is not able to find one.  I don't consider this a FATAL problem, why does the INSTALL think it is??????????????????  Not to mention that the install location is the USB drive.

---

### Post by Nap_BlownApart on 2012-08-19
I understand that I can set an option "cdrom-detect/try-usb=true" in the Kernel boot line.  I'm guessing that is the prompt **boot:**. When I type it there, it returns "Could not find Kernel image: cdrom-detect/try-usb=true"
I looked at the help screens, and while there are lots of other parameters I can enter, none mention the CD.

A frustrated Ubuntu user,
Nap

---

### Post by Nap_BlownApart on 2012-08-19
When at the main menu of the installer, I pressed TAB while the "Install Ubuntu Server" option was highlighted.
This produced a message at the bottom of the screen as follows:
```
> /install/vmlinuz noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu/install/vmlinuz noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu-server.seed initrd=/install/initrd.gz quiet --
```
It looks like the switch is already there, so no need to type it anywhere.

So, what is wrong?  Why is the installer still looking for the CDROM?

Nap

---

### Post by cwsnyder on 2012-08-19
The Live CD does not have the server packages to install.  Your option from the 'Install Ubuntu Server' lists **file=/cdrom/preseed/ubuntu-server.seed**.  That option would have to be changed to point to your USB, as in **file=/dev/sdb1/preseed/ubuntu-server.seed** or wherever the seed file is found.

---

### Post by Nap_BlownApart on 2012-08-19
ic.  thnx cwsnyder.
I used the Universal-USB-Installer-1.9.0.7 to create the Live CD.  Strange that it's left it as /cdrom  ....
I have sda, sda1, sda2, sda3, sda4, sda5, and sdb in my /dev folder.  I tried using **dmesg** to find out the device file name, but don't know enough to figure it out.
I can try each one until it works, but is there a quicker way?

Cheers
Nap

---

### Post by Nap_BlownApart on 2012-08-20
This is becoming a rather bad nightmare.  I have a VPS running this version of Ubuntu and want to setup a mirror on my local machine.

Is there a log file created during the install process?  If so, where would it be located? (does **dmesg** display the log?)
Also, can I get some help figuring out what device file is my USB?

---

### Post by mastablasta on 2012-08-20
/var/log
 
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
 
sda = first disk drive
/sda1= first partition on first disk, /sda2= second partition on first disk...
sdb = second disk

---

### Post by mastablasta on 2012-08-20
> **Nap_BlownApart said:**
>  
To overcome this, I want to install it from a USB Drive. I don't want a Live USB Install, I actually **want to install the OS on the Laptop.**

 
> **Nap_BlownApart said:**
>  I don't have a CD, that's why it is not able to find one. I don't consider this a FATAL problem, why does the INSTALL think it is?????????????????? Not to mention that the **install location is the USB drive**.
 
is final install location USB drive or laptop hard disk? 
 
are you maybe running wubi to install it? that one needs an image fille or CD. USB does not need a CD drive.
 
perhaps you can document it with a couple of pics so we can really see what happens and at what point exaclty it get's stuck.
 
another option is to use mini iso and then use your friends internet connection to download necessary packages. [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Nap_BlownApart on 2012-08-25
> **mastablasta said:**
> is final install location USB drive or laptop hard disk?
Final destination is on the local hard disk of the laptop so I won't need the usb anymore.  As per my next answer, conceptually, I'm using a usb key instead of a CD.   I would prefer installing to partition 0, but I don't really care TBH.
 
> **mastablasta said:**
> are you maybe running wubi to install it? No.  I'm trying to use the USB instead of a CD Drive.  From my point of view, it is actually that simple.
 
> **mastablasta said:**
> perhaps you can document it with a couple of pics so we can really see what happens and at what point exaclty it get's stuck.
Good idea.  I will use my iPhone to take some photos of the screens, infact I might make a movie of the process.
 
> **mastablasta said:**
> another option is to use mini iso and then use your friends internet connection to download necessary packages. [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)  Thnx for the suggestion.  I'll do the movie first to see what feedback I get.  I'm also going to try using **rescatux_cdrom_usb_hybrid_i386_486-amd64_0.30b7_sg2d.iso** as well.  I've been advised elsewhere that this is a possible way to overcome my problem.  But the movie will be 1st as I rather get it going via a USB as it's the most logical and straight forward way of getting the result I desire.  Make it easier for others at the same time.

Cheers,
Nap

---

### Post by Nap_BlownApart on 2012-08-25
I've uploaded some visual media to my server.
A picture of how I created the PenDrive is [here]("http://www.abms.net.au/Study/Create_Pendrive.png")
Movie of the install on the laptop from the USB is [_here in FLV format_]("http://abms.net.au/Study/USB_Install_Fail.flv") and [_here in AVI format_]("http://abms.net.au/Study/USB_Install_Fail.avi")

Hope this helps.

Cheers,
Nap

---

### Post by oldfred on 2012-08-25
I do not have an answer, and cannot find notes that might help.

I install desktop versions using ISO on either hard drive or USB and loopmount with grub. But alternative & later I found server do not loopmount correctly as it does have the issue of remounting something part way thru install and wants the cd location.

Someone had posted notes on going to terminal and adding a mount command, but cannot find that link now.

Grub does not loopmount alternate
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926)

I did find this in my notes, use alt f1  or f2 to get to terminal and try to mount your install to what ever location it seems to be asking for.
> With Debian Installer(Which is text/ncurses based) ,it asks to Mount Ubuntu CD when booted from hard disk iso.What I did was ,to symlink(symbolic Linking) Lucid Alternate cd ISO to /dev/sr0(Which is the device file for dvd drive) .Then If I ask debian-installer to retry to mount cd ,it got mounted!
Code:
ln -sf /yourubuntuisodirectory/ubuntu.iso /dev/sr0



---

### Post by Nap_BlownApart on 2012-08-25
OldFred,
  Thank you.

dmesg shows the following new entries, after I plug my usb in:
(I'm assuming the number within the square brackets is a timestamp, so I started pasting them when I got to the 8:0:0:0 lines
```

[14728.828073] usb 1-3: new highspeed USB device using ehci_hcd and address 7
[14728.962534] usb 1-3: configuration #1 chosen from 1 choice
[14728.963450] scsi8 : SCSI emulation for Mass Storage devices
[14728.963752] usb-storage: device found at 7
[14728.963758] usb-storage: waiting for device to settle before scanning
[13733.960352] usb-storage: device scan complete
[14733.961290] scsi 8:0:0:0 Direct-Access    Ut165     USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[14733.962615] sd 8:0:0:0 Attached scsi generic sg1 type 0
[14733.962615] sd 8:0:0:0 [sdb] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[14733.962615] sd 8:0:0:0 [sdb] Write Protect is off
[14733.962615] sd 8:0:0:0 [sdb] Mode Sense: 00 00 00 00
[14733.962615] sd 8:0:0:0 [sdb] Assuming drive cache: write through
[14733.962615] sd 8:0:0:0 [sdb] Assuming drive cache: write through
[14733.967992]  sdb:
[14733.962615] sd 8:0:0:0 [sdb] Assuming drive cache: write through
[14733.962615] sd 8:0:0:0 [sdb] Attached SCSI removable disk
```

Later, when I remove it, dmesg added a line: ```
[14733.962615] usb 1-3: USB disconnect, address 7
```

With the help **mastablasta** gave earlier, I think the usb is either device **sdb**, or **sg1** but I can't figure out how to mount the usb and list its directory.  I'm looking for a directory listing similar to what I can see on my windows machine when I created the Pendrive.

It would be nice if I could figure out how to access the usb pendrive because I would be able to transfer output from the laptop to this computer without typing it out, or making movies.  Any help on how to do this would be much appreciated.

**cwsnyder** suggested I change the installers references to **cd-rom** to the usb device id.  I agree with his logic, and want to try that.  But without getting the above done, I'm stuck.

What you mentioned concerning the symlink is a great idea if Ubuntu can be tricked like that. I'm a windows person, and short-cuts are not as useful there.  In order to do this, I would need to know the device id of the cd-rom too.

Here is my /etc/fstab file:
```
none          /dev/pts          devpts   defaults    0     0
none          /proc             proc     defaults    0     0
none          /sys              sysfs    noauto      0     0
```

Do I need to add anything here?

What about GRUB?  The laptop came with 3 partitions (Win7, Data, and Samsung Rescue).
This computer I'm using atm runs Vista (as supplied by ASUS) and I installed Win7 later.  I used EasyBCD to create the boot menu so I could install Win7.  I used EasyBCD on the laptop to create the boot menu, but later removed it as it didn't help.  Could this have some effect?  That's one of the reasons I'm thinking of using **rescatux** as I think it will fix/overwrite the MBR and set it up correctly.


Cheers,
Nap

---

### Post by Cheesemill on 2012-08-25
I know it's not really a proper solution but do you have another machine with a CD drive?

If so you could always plug your laptop HD into another machine to do the installation and then put it back in the laptop afterwards.

---

### Post by Nap_BlownApart on 2012-08-25
> **Cheesemill said:**
> I know it's not really a proper solution but do you have another machine with a CD drive?

If so you could always plug your laptop HD into another machine to do the installation and then put it back in the laptop afterwards.

What a cheesy idea....  lol.
It is possible.  I took the back off the laptop to see the HD interface, and I think it will work.  Only question is concerning other hardware differences b/w the two machines and how Ubuntu manages device driver software.  In Windows, that would virtually render this method impossible.

For the moment, I'ld like to follow the more normal method to get a solution that doesn't require an extra machine, and others could follow.

Cheers,
Nap

---

### Post by Cheesemill on 2012-08-25
> **Nap_BlownApart said:**
> Only question is concerning other hardware differences b/w the two machines and how Ubuntu manages device driver software.  In Windows, that would virtually render this method impossible.

It's not a problem at all, I do it all the time.

Unlike Windows which probes for hardware and sets up specific drivers when you install, the Linux kernel probes the hardware and loads the correct drivers on each boot (this is why it's possible to have a Live CD).

I have a full installation of Ubuntu on a USB stick which has worked on every machine I've every tried it on (more than 50 machines at last count).

---

### Post by Nap_BlownApart on 2012-08-25
Cheesemill,
  I will buy you a coffee plantation if I ever get to meet you in person, you will never run out of beans!  But I'm going to have to start saving in the meantime.

I'm sorted now, at least with respect to installing.  Now I have to get drivers for the hardware etc.

As far as the USB key install, I'm still keen, don't want to have to dismantle to computers if I ever need to reinstall.  There are other reasons; warranty as well as in situations where the above option isn't available.

Cheers,
Nap

Might have a coffee myself now.

---

