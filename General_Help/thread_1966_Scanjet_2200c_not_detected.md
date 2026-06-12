---
title: "Scanjet 2200c not detected"
date: 2004-10-24
forum: General Help
---

### Post by jcscar on 2004-10-24
I have an HP Scanjet 2200C that XSane does not detect. It is usb, and is connected through a usb hub.  Is there any hope for me to get this running?

---

### Post by sfw5000 on 2004-10-24
What have you tried to detect it? Do you have sane-utils installed? I don't have that scanner, but there is a buggy thing with getting a scanner to work, here's what I did:

1)
sam@ernie ~ $ sane-find-scanner

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8, product=0x0110) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

2) sam@ernie ~ $ sudo chmod 777 /proc/bus/usb/001/005

Basically by default only root can use the scanner. I filed a bug on this and they added the initial user to the scanner group to get it to work, but even though the initial user is now part of the scanner group I still had to change the permissions on the /proc file to get it working. Since sane-find-scanner found my scanner at libusb:001:005, that's how I know to change the permissions of /proc/bus/usb/001/005 -- those numbers change, I believe, depending on which USB port your scanner is plugged into.

If there's a better way to do this, please let me know! But this does work.

---

### Post by jcscar on 2004-10-24
[QUOTE=sfw5000]What have you tried to detect it? Do you have sane-utils installed? I don't have that scanner, but there is a buggy thing with getting a scanner to work, here's what I did:

1)
sam@ernie ~ $ sane-find-scanner

[/QUOTE]

I don't see the sane-utils in the packages to download. And that command doesn't work so I believe I don't have that package.  How do I obtain it?

---

### Post by sfw5000 on 2004-10-24
If you uncomment the universe lines in your sources.list, sane-utils should show up in synaptic. My /etc/apt/source.list is below:
####
# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Unofficial i386 Binary-1 (20040915)]/ unstable main restricted 

## Uncomment the following two lines to fetch updated software from the network
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted  
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted   

## Uncomment the following two lines to fetch updated software from the network
## and be able to use more than 12000 unsupported packages from the universe archive.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
####
In synaptic hit "reload" then search for sane-utils and it should come up.

Sam

---

### Post by jcscar on 2004-10-25
Thanks I got it to work with your help.. Also the universal packages is helping on several other things I couldn't find. ;)

---

### Post by ahawesome on 2008-05-20
> **sfw5000 said:**
> sudo chmod 777 /proc/bus/usb/001/005

This doesn't work for me. It says: chmod: cannot access `/proc/bus/usb/002/002': No such file or directory

sane-find-scanner detects the scanner, but XSane only sees it when I run it as root. I am using Hardy.

EDIT: The scanner _IS_ located at location 002:002, so the command should be right.

---

