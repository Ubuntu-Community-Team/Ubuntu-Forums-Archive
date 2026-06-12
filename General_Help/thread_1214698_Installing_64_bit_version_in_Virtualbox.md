---
title: "Installing 64 bit version in Virtualbox"
date: 2009-07-16
forum: General Help
---

### Post by blazemore on 2009-07-16
I have Virtualbox installed on a 64 bit Windows 7.
I try to install Ubuntu 64 bit, and it basically says no, it only detected an i686 CPU.

Is there a setting in Virtualbox that needs to be changed? I know this isn't an Ubuntu issue, but this is the best forum for any kind of computer-related help :-)

EDIT: The exact message is
> This kernel required an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.
_


---

### Post by blazemore on 2009-07-16
I checked my BIOS and can't find an option for virtualisation. My CPU supports it, so I'm going to assume it's turned on.

---

### Post by jocko on 2009-07-16
> **blazemore said:**
> I checked my BIOS and can't find an option for virtualisation. My CPU supports it, so I'm going to assume it's turned on.
I would guess that if you can't find the option, it's turned off (that's the case with my laptop).
Some bioses have hidden some advanced options (like overclocking and perhaps virtualization) that can be uncovered by pressing a key combination, but you'll need to search in your motherboard manual to find out if that's the case with yours.

---

### Post by carml on 2009-07-16
Maybe checking the options on Virtualbox will help you.
I found an option to enable the virtualization at CPU level on Intel CPU.
I hope this can help you.

---

### Post by blazemore on 2009-07-16
This checkbox is checked (in virtualbox) but also greyed out so I can't change it.

---

### Post by 3rdalbum on 2009-07-16
I think you need the absolute latest version of Virtualbox - I believe they've got 64-bit Guests on 64-bit Hosts working now.

---

### Post by sureshsaragadam on 2011-06-09
It is possible to install Ubuntu on Your System, In your case You are supposed to install **32bit version** of Ubuntu.

You need to have a VT enabled or VT hardware support to run a 64 bit guest operating system on a 64bit Virtual Kernel, Better you can try installing i386 version of guest operating system on 64bit kernel 


Because you dont have a VT 64bit hardware support you had this Error

**VirtualBox: This kernel requires an x86-64 CPU, but only detected an i686 CPU**

---

### Post by linuxinstalledfromhdd on 2011-06-09
You could try vmware:

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

---

### Post by jocko on 2011-06-09
You are trying to resurrect a long-dead thread. Look at the date of the last post by 3rdalbum...

But just to make it clear: to be able to run a 64 bit guest (in *any* virtualization solution), you need a 64 bit cpu with virtualization enabled in the bios. If you can't find the option to enable virtualization in the bios, there is nothing you can do.

---

