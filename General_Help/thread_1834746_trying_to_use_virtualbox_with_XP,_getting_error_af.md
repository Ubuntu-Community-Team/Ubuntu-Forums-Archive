---
title: "trying to use virtualbox with XP, getting error after error"
date: 2011-08-28
forum: General Help
---

### Post by hiatusland on 2011-08-28
I need to install Windows using VirtualBox. I am pretty new to Ubuntu and its wiley ways (having used Windows for long enough) but I managed to get VirtualBox installed. I put the XP disc into the CD drive (which was unmounted, apparently..I figured out how to mount it eventually) and started the vm. I then get a black screen that says FATAL: No bootable medium found! System halted.

I have been tinkering with this for hours now and, since I can't figure out the coding to get the VPN server (for the college newspaper I help edit) to work on here, I need to be able to at least boot Windows so that I can access that server and, well, do my job. I don't want to switch back completely because I hate Windows but I have been scouring Google and forums and everyone's problems that are similar to mine have been easily solved. I have tried "allowing passthrough" and mounting the cd drive and switching out boot discs but NOTHING is working.

Does ANYONE have a solution? PLEASE??

---

### Post by itsferny on 2011-08-28
had the same problem
use a usb stick 
put windows as .iso in a usb and run it on that 
that fixed my probelm
hope it help

---

### Post by YesWeCan on 2011-08-28
What version of Ubuntu and VB are you using?
What Do you mean the CD was umounted? It should automount when you put a disc in it, in Ubuntu. Whst did you do to fix this?
If Ubuntu sees the XP disc then VB will because it operates via Ubuntu. Check on the VB config window under Storage that the CD drive is selected.

---

### Post by haqking on 2011-08-28
> **hiatusland said:**
> I need to install Windows using VirtualBox. I am pretty new to Ubuntu and its wiley ways (having used Windows for long enough) but I managed to get VirtualBox installed. I put the XP disc into the CD drive (which was unmounted, apparently..I figured out how to mount it eventually) and started the vm. I then get a black screen that says FATAL: No bootable medium found! System halted.

I have been tinkering with this for hours now and, since I can't figure out the coding to get the VPN server (for the college newspaper I help edit) to work on here, I need to be able to at least boot Windows so that I can access that server and, well, do my job. I don't want to switch back completely because I hate Windows but I have been scouring Google and forums and everyone's problems that are similar to mine have been easily solved. I have tried "allowing passthrough" and mounting the cd drive and switching out boot discs but NOTHING is working.

Does ANYONE have a solution? PLEASE??

Sounds like either a dodgy disc or a problem with your VM settings.

Can you post some images of your VM settings including the storage and system sections

it will make support easier.

is the boot order set correctly ?

---

### Post by coldraven on 2011-08-28
Go to System>Admin>Users and Groups
Click on "manage groups"
Make sure that you are in the "vboxusers" group
If not, add yourself then either log-out and back in or re-boot your PC.
This probably will not fix your problem but you will need to do it eventually if you want USB to work in your VM.
Check the boot order in VirtualBox settings, see the screenshot

---

### Post by hiatusland on 2011-08-28
Hey guys, I already have the CDROM set as priority. That was one of the first things I did.

How do I boot from USB? I don't have a jump drive bigger than 2gb, so would I be able to use my external?

---

### Post by hiatusland on 2011-08-28
I got the USB, so I just need to know how to boot from it. I even tried burning a new disc from which to boot and it's not working still, so I know it's not a problem with the disc.

---

### Post by hiatusland on 2011-08-28
Update: I tried booting from the CDROM right when my computer booted up and when I clicked on it in the sidebar. Neither SETUP.EXE files on either the USB or CD would boot, they gave me the same error (screenshot below). I'm thinking this is a problem which will never be solved :sad:

---

### Post by ktmom on 2011-08-28
YesWeCan was right, you need to post what VB you are using.  Did you install from the Ubuntu repositories using synaptic?  Or did you download and install the VirtualBox packaged version from virtualbox.org directly?  It matters in trying to help you.

If you installed from the Ubuntu repositories, did you follow [these instructions]("https://help.ubuntu.com/community/VirtualBox/FirstVM") from the community help pages?

---

### Post by hiatusland on 2011-08-28
I used [http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html](http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html) to download VirtualBox.

I can see on the file list that there is a disc in the drive, as well as that the USB drive is connected. Restarting and hitting F2 then selecting boot from CDROM or USB (which has an .iso on it of XP), alternately, produces an error with the USB and absolutely nothing from the CDROM (the disc spins up and hums then spins down).

I think VirtualBox is running fine, there is just a problem with recognizing the CD?

---

### Post by SeijiSensei on 2011-08-28
Can you boot the computer directly from the Windows disk if it's in the CD/DVD drive?  If not, your Windows disk doesn't have a boot loader.  VirtualBox won't be able to boot it either.

Is this an honest-to-goodness Windows disk or "something else?"

---

### Post by coldraven on 2011-08-30
Have you tried booting your computer with the CD?
If it won't boot, the CD is no good.
A "Restore" CD from one manufacturer will not work in another brands PC although it should boot and give you a warning message.

---

