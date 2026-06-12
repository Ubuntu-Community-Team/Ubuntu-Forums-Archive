---
title: "Live CD won't run"
date: 2011-03-08
forum: General Help
---

### Post by nscherneck on 2011-03-08
Hello all,
 
I'm a Windows user interested in Linux and Ubuntu and was excited to see that I can test drive the OS before installing. I'm a complete newb to Ubuntu. 
 
I followed the directions on the site, downloaded the ISO, and burned it to CD using InfraRecorder. When I plugged th CD back into the drive and booted to it I got the Ubuntu logo but experienced the following eror:
 
**(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error**
 
**Can not mount /dev/loop (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs**
 
I read a few posts on this forum and found that bruning another CD at a slower speed might resolve this but it did not. Same error. 
 
Any help is much appreciated.
 
 
Intel Core 2 Duo T9400 2.53GHz
4Gb RAM
Windows Vista Ultimate 32-Bit installed

---

### Post by kukker32 on 2011-03-08
If you have an empty usb key try run it from there.
theres a guide how to setup a live usb  here
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

please let me know if that gives the same error..

---

### Post by anglican on 2011-03-08
> **nscherneck said:**
> Hello all,
 
I'm a Windows user interested in Linux and Ubuntu and was excited to see that I can test drive the OS before installing. I'm a complete newb to Ubuntu. 
 
I followed the directions on the site, downloaded the ISO, and burned it to CD using InfraRecorder. When I plugged th CD back into the drive and booted to it I got the Ubuntu logo but experienced the following eror:
 
**(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error**
 
**Can not mount /dev/loop (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs**
 
I read a few posts on this forum and found that bruning another CD at a slower speed might resolve this but it did not. Same error. Have you checked that your original iso is OK (md5sum). If not it wont matter what speed you burn it at!
> **nscherneck said:**
>  
Any help is much appreciated.
 
 
Intel Core 2 Duo T9400 2.53GHz
4Gb RAM
Windows Vista Ultimate 32-Bit installedThat configuration should be fine for ubuntu.

H

---

### Post by nscherneck on 2011-03-08
> **anglican said:**
> Have you checked that your original iso is OK (md5sum). If not it wont matter what speed you burn it at!
 
H 
 
Just read up on how to check the md5sum (didn't know how to before) and it didn't match (used the winMd5Sum program).  I'm re-downloading the .ISO file now.

---

### Post by nscherneck on 2011-03-08
Download was good.  Checked the md5sum and it was good.  Burned new CD at slowest rate and checked for errors once I booted to the CD.  No errors and LiveCD operated.  Thank you!

---

