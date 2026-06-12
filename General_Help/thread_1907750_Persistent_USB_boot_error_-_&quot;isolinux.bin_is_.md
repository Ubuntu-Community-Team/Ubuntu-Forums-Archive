---
title: "Persistent USB boot error - &quot;isolinux.bin is missing or corrupt&quot;"
date: 2012-01-12
forum: General Help
---

### Post by rextor on 2012-01-12
I referred to Method 3 in the following link to create a live USB with persistent storage:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

After having followed all steps, i get the following error on booting with the USB drive:
```
isolinux.bin is missing or corrupt
```

How do i get around this?

Note: I am preparing this USB on an OpenSUSE 11.4 system

---

### Post by C.S.Cameron on 2012-01-12
You could try the MultiBootUSB script to boot Open SUSE on USB.

---

### Post by Double.J on 2012-01-12
> **rextor said:**
> I referred to Method 3 in the following link to create a live USB with persistent storage:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

After having followed all steps, i get the following error on booting with the USB drive:
```
isolinux.bin is missing or corrupt
```

How do i get around this?

Note: I am preparing this USB on an OpenSUSE 11.4 system
Hi there, 

Have you tried this from  the build service?

[usb-creator]("https://build.opensuse.org/package/show?package=usb-creator&project=home%3Ariddell%3Ausb-creator")

I've never had cause to do more than make installers in SUSE so I can't testify to persistence but it looks like it does it? Does unetbootin on SUSE not do persistence? I'm on a windows machine at the mo [:(] so can't check? but I've never had problems with making ubuntu with persistence in windows/ubuntu using unetbootin

---

### Post by rextor on 2012-01-12
Apologies.. i missed out on mentioning that i am actually trying to create a Ubuntu USB and not an OpenSUSE one(because i am interested in trying out Ubuntu over the next few weeks). OpenSUSE only happens to be my current OS installed on the laptop.

---

### Post by C.S.Cameron on 2012-01-12
+1 usb-creator

---

### Post by rextor on 2012-01-13
Thanks. I used usb-creator to create the live USB.. after some initial hiccups I could create a successful USB drive using 'kdesu usb-creator-gtk'

However, when i boot using this USB, the screen would not go past the Syslinux copyright line on the console!! :(

---

### Post by Zukaro Travon on 2012-01-13
The same thing happens to me when I try to make a live-USB with persistent storage.

What you could do, is reinstall the iso to the USB but not make it persistent.  Then, boot into that and go through the normal setup, but rather than choosing your hard drive choose your USB and manual partitioning.  Then just make some partitions (probably best to have made those first) and install it to those.

When you're done just delete the partition that contained the live-USB files.

You should be able to do this through the Windows installer (not sure as I haven't tested it, but it'd certainly make it easier than the other way I mentioned).



Not sure if this is really what you're looking for though, but it'd at least let you test out Ubuntu without installing it to your hard drive while still allowing you to save files and download packages.
(did something similar awhile ago; the way that involves booting off the USB then installing to it)

---

### Post by C.S.Cameron on 2012-01-13
Suggest you check the iso's MD5SUM.

---

### Post by rextor on 2012-01-14
> **C.S.Cameron said:**
> Suggest you check the iso's MD5SUM.

MD5SUM seems correct.

```
njathan@sooseh:~/software/distros/ubuntu> md5sum -c MD5SUMS.txt 
md5sum: ubuntu-11.10-alternate-amd64.iso: No such file or directory
ubuntu-11.10-alternate-amd64.iso: FAILED open or read
md5sum: ubuntu-11.10-alternate-i386.iso: No such file or directory
ubuntu-11.10-alternate-i386.iso: FAILED open or read
md5sum: ubuntu-11.10-desktop-amd64.iso: No such file or directory
ubuntu-11.10-desktop-amd64.iso: FAILED open or read
**ubuntu-11.10-desktop-i386.iso: OK**
md5sum: ubuntu-11.10-server-amd64.iso: No such file or directory
ubuntu-11.10-server-amd64.iso: FAILED open or read
md5sum: ubuntu-11.10-server-i386.iso: No such file or directory
ubuntu-11.10-server-i386.iso: FAILED open or read
md5sum: ubuntu-11.10-wubi-amd64.tar.xz: No such file or directory
ubuntu-11.10-wubi-amd64.tar.xz: FAILED open or read
md5sum: ubuntu-11.10-wubi-i386.tar.xz: No such file or directory
ubuntu-11.10-wubi-i386.tar.xz: FAILED open or read
md5sum: wubi.exe: No such file or directory
wubi.exe: FAILED open or read
md5sum: WARNING: 8 listed files could not be read
njathan@sooseh:~/software/distros/ubuntu>
```

---

### Post by C.S.Cameron on 2012-01-14
Can you burn the Ubuntu iso to CD and use the usb-creator from there?

---

### Post by varunendra on 2012-01-15
> **C.S.Cameron said:**
> Can you burn the Ubuntu iso to CD and use the usb-creator from there?
Or,

install virtualbox > boot the VM with the downloaded iso > press any key during boot-up to get advance boot menu > select "Check Disk for defects"

If disc (iso) passes the check, reboot with the same iso again > start a live session (Try Ubuntu option) > connect the USB to the VM and use live session's inbuilt usb-creator to make it live persistent.

You may have to install the 'PUEL' version of virtualbox if USB support is not found in the default version (OSE).

I keep doing it all the time (although with VMware) and it never failed me.

---

