---
title: "how to burn live cd on USB pendrive"
date: 2012-06-13
forum: General Help
---

### Post by satimis on 2012-06-13
Hi all,

How to burn a live CD on USB pendrive making the latter bootable.

I tried;
su -c 'dd if=/path_to/Live_cd.iso of=/dev/sdb1''X'' bs=8M'

/dev/sdb1 is the pendrive.

It burnt the live cd on the pendrive.  But latter won't boot.  

Pls help.  TIA

B.R.
satimis

---

### Post by zero2xiii on 2012-06-13
Hay,

Please use google or some forum searches. A LOT of information is available to do this in EVERY way imaginable.

But. Just to save you the time, trouble and a few other things:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Read THROUGH them. Step by step. THEN after you read them and still don't get your answer, USE [GOOGLE]("http://www.google.com") and after that, and you have tried a few of the other options that exist and you still do not have the desired effect. Then ask here for further assistance, with more details as to EXACTLY what the task is you wish to accomplish.

I am doing this cause you can not "burn" an ISO file to a USB stick. You "burn" an ISO file to a CD/DVD.

Cherz

---

### Post by satimis on 2012-06-13
> **zero2xiii said:**
> Hay,

Please use google or some forum searches. A LOT of information is available to do this in EVERY way imaginable.

But. Just to save you the time, trouble and a few other things:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Read THROUGH them. Step by step. THEN after you read them and still don't get your answer, USE [GOOGLE]("http://www.google.com") and after that, and you have tried a few of the other options that exist and you still do not have the desired effect. Then ask here for further assistance, with more details as to EXACTLY what the task is you wish to accomplish.

I am doing this cause you can not "burn" an ISO file to a USB stick. You "burn" an ISO file to a CD/DVD.

Cherz

Lot of thanks for your advice.  

Several years back I did many times using live CD to create bootable pendrive.  No additional software was needed, only command lines and no need burning the *.iso on CD.  Unfortunately I forgot the steps.  I spent almost 2 days searching around my database as well as googling Internet without result.

The steps on;
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/#more-4080](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/#more-4080)

solved part of my problem.  The live USB thus created couldn't boot.  I suppose it needs the *.iso image burned on CD.

I played around with ubuntu-12.04-cloud-live-amd64.iso download on;
[http://cdimage.ubuntu.com/ubuntu-cloud-live/releases/12.04/](http://cdimage.ubuntu.com/ubuntu-cloud-live/releases/12.04/)

without burning it on CD.  I booted it on VM of VirtualBox without problem.  I could play around the live cloud on VM.  Then I ran the steps of "pendrivelinux" creating a live USB, also on the same VM.  The steps went through without complaint.  Unforturnately the live USB created can't boot on physical PC.  I must complete this step making sure the live USB can boot a physical PC before going further to make it boot on VM.  It is a different approach.

That is the complete story.

B.R.
satimis

---

### Post by zero2xiii on 2012-06-14
> **satimis said:**
> Lot of thanks for your advice.  

Several years back I did many times using live CD to create bootable pendrive.  No additional software was needed, only command lines and no need burning the *.iso on CD.  Unfortunately I forgot the steps.  I spent almost 2 days searching around my database as well as googling Internet without result.

The steps on;
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/#more-4080](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/#more-4080)

solved part of my problem.  The live USB thus created couldn't boot.  I suppose it needs the *.iso image burned on CD.

I played around with ubuntu-12.04-cloud-live-amd64.iso download on;
[http://cdimage.ubuntu.com/ubuntu-cloud-live/releases/12.04/](http://cdimage.ubuntu.com/ubuntu-cloud-live/releases/12.04/)

without burning it on CD.  I booted it on VM of VirtualBox without problem.  I could play around the live cloud on VM.  Then I ran the steps of "pendrivelinux" creating a live USB, also on the same VM.  The steps went through without complaint.  Unforturnately the live USB created can't boot on physical PC.  I must complete this step making sure the live USB can boot a physical PC before going further to make it boot on VM.  It is a different approach.

That is the complete story.

B.R.
satimis

I am guessing it is because you are not using the correct terms, Seems like english is not your first language aswell, just a guess though.

Have a look at [Unetbootin]("http://unetbootin.sourceforge.net/") as this automates a huge part of the process. It is also in the ubuntu repositories so you can install it via the software centre.

Cherz

---

### Post by C.S.Cameron on 2012-06-14
I have made physical Ubuntu pendrives using VBox.
From the Ubuntu VM, run Startup Disk Creator, pointing it to your USB drive. Select amount of "Reserved Extra Space" for persistence
I think you need Guest Additions installed.

Edit:
Versions previous to 12.04 have usb-creator.exe, a Windows executable file, in the iso.
This can be used to make a Ubuntu Live USB from a Windows machine.

---

### Post by satimis on 2012-06-14
Hi all,

Thanks for your advice.

I already have a live USB pendrive created according to;

How to install Linux Mint via USB
[http://community.linuxmint.com/tutorial/view/744](http://community.linuxmint.com/tutorial/view/744)

The steps worked seamlessly.  Now the USB pendrive can boot physical PC.  However it can't boot VM.  I created a raw disk to do the job.

B.R.
satimis

---

### Post by zero2xiii on 2012-06-16
> **satimis said:**
> Hi all,

Thanks for your advice.

I already have a live USB pendrive created according to;

How to install Linux Mint via USB
[http://community.linuxmint.com/tutorial/view/744](http://community.linuxmint.com/tutorial/view/744)

The steps worked seamlessly.  Now the USB pendrive can boot physical PC.  However it can't boot VM.  I created a raw disk to do the job.

B.R.
satimis

Why do you need a VM to boot from a usb? Just point the VM HOST SOFTWARE to the ISO on the host system's filesystem and it will use it. In VMware you can use an ISO file as a cdrom drive. No need to create a bootable CD/DVD/USB

Cherz

---

### Post by meathdeath on 2012-06-16
try this

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by Cheesemill on 2012-06-16
VirtualBox won't boot from a USB, it doesn't have the option to.

As others have mentioned if you are trying to install a VM just point it to the .iso file on your hard drive.

---

### Post by satimis on 2012-06-17
Hi all,

Thanks for your advice.

This is ONLY a test.

On host I ran following command creating a raw disk

$ sudo VBoxManage internalcommands createrawvmdk -filename /home/user/.VirtualBox/HardDisks/usbdisk.vmdk -rawdisk /dev/sdb

But I can't make usedisk.vmdk to work.  On creating a new VM I couldn't select this raw disk.  However to my surprise another raw disk with the same name, usbdisk.vmdk, was created on /root/.VirtualBox/HardDisks/usbdisk.vmdk

If I start VBox Manager as root and create a new VM.  I can select it.  The new VM can be started with a working Live Cloud.  But it is NOT correct running VBox Manager as root.  I'm still googling around how to make /home/user/.VirtualBox/HardDisks/usbdisk.vmdk to work.

B.R.
satimis

---

### Post by Cheesemill on 2012-06-17
I would be very interested if you could find a solution to this.

I played around with this several months ago and could never get it to work for the same reason as you, using a raw disk vmdk will only work if you run VirtualBox as root.

The method I eventually used was to passthrough the USB device to the VM, and then boot the VM from a PLOP boot manager .iso and chainload GRUB on the USB stick through that.

---

### Post by satimis on 2012-06-17
> **Cheesemill said:**
>  - snip -

The method I eventually used was to passthrough the USB device to the VM, and then boot the VM from a PLOP boot manager .iso and chainload GRUB on the USB stick through that.
Could you please explain in more detail?

What did you mean "passthrough the USB device to the VM"?  It couldn't be selected by a VM.

TIA

B.R.
satimis

---

### Post by Cheesemill on 2012-06-17
How to pass through a USB device to a VM:
[http://www.faqforge.com/linux/enable-usb-support-in-virtualbox-ubuntu/](http://www.faqforge.com/linux/enable-usb-support-in-virtualbox-ubuntu/)

This will let the VM access your USB stick, but you still won't be able to boot directly from it as VirtualBox doesn't support booting from USB. To get round this you can use PLOP bootloader from an .iso to chainload the USB boot:
[http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/](http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/)

---

### Post by zero2xiii on 2012-06-17
> **Cheesemill said:**
> 
This will let the VM access your USB stick, but you still won't be able to boot directly from it as VirtualBox doesn't support booting from USB. To get round this you can use PLOP bootloader from an .iso to chanlaid the USB boot:


Still don't get why the OP wants to create a bootable usb, and then boot a VM from it? Why not just put the ISO on the usb then and assign the usb for persistance if persistance is what is needed to carry usb from one VM to another for example (only reason I can think of why one would want to boot a vm from a usb - even then there is easier ways)

Hmmmm:confused:

---

### Post by Cheesemill on 2012-06-17
> **zero2xiii said:**
> Still don't get why the OP wants to create a bootable usb, and then boot a VM from it? Why not just put the ISO on the usb then and assign the usb for persistance if persistance is what is needed to carry usb from one VM to another for example (only reason I can think of why one would want to boot a vm from a usb - even then there is easier ways)

Hmmmm:confused:

I don't get it either.

The only time I use this method is to boot my USB which has a full Ubuntu installation on it as a VM when I need to make changes or update it and I can't be bothered to reboot my workstation.

This is the only case I can think of where it is of any use.

If the OP can clarify exactly what they are trying to achieve and why it would definatley help us recomend a better method of doing things.

---

### Post by satimis on 2012-06-17
Hi Cheesemill,

Before testing your suggestion may I clarify my attempt.  This is a test.

No doublt I can boot the live CD without problem playing around openstack.  I expect to install live CD on VM.  On googling I found that it is possible using a raw disk which can be created via a live USB.  For such a reason I created a workable live USB.  But the raw disk created can't work as user.  To run it I must start Vbox Manager as root.

That is my present situation.  I can mount the USB but enable to boot it.

Actually my final goal is to install the live CD on VM.  I have been googling around for sometimes without result.  Is there any suggestion?

B.R.
satimis

---

### Post by Cheesemill on 2012-06-17
If you want to install a Live CD on a VM just point the VM to either the .iso file or the physical drive.

There is absolutely no reason to be messing around with USB at all, it just adds extra unneeded complexity to an otherwise straightforward task.

---

### Post by satimis on 2012-06-17
> **Cheesemill said:**
> If you want to install a Live CD on a VM just point the VM to either the .iso file or the physical drive.
- snip - 

I tried many time.  There is no options on this live CD; to play the live CD or to install it on HD as other installers do.  It boots straight to openstack.

satimis

---

### Post by Cheesemill on 2012-06-17
> **satimis said:**
> I tried many time.  There is no options on this  live CD; to play the live CD or to install it on HD as other installers  do.  It boots straight to openstack.
Well if you do manage to create a bootable USB it will have exactly the same options as the Live CD, you are achieving nothing by using USB instead of CD.


If you want to install OpenStack just follow the instructions on their website:
[http://docs.openstack.org/](http://docs.openstack.org/)

---

### Post by satimis on 2012-06-17
> **Cheesemill said:**
> Well if you do manage to create a bootable USB it will have exactly the same options as the Live CD, you are achieving nothing by using USB instead of CD.

On searching there are threads suggesting creating raw disk via USB.  I have spent almost 2 days playing around it without result.  The raw disk only works as root.  

VBox forum didn't give support on raw disk.  They said if I can make raw disk to work I won't need their support.

> 
If you want to install OpenStack just follow the instructions on their website:
[http://docs.openstack.org/](http://docs.openstack.org/)
Thanks.

I have openstack running on other VMs.  I'm a beginner on openstack.  I just play around it in order to learn.

B.R.
satimis

---

