---
title: "kexec-tools"
date: 2010-12-19
forum: General Help
---

### Post by katykat on 2010-12-19
I get a consistent eroor when installing programs from Synaptic or Apt. 

kexec-tools is generating an error, and in reference to /boot/device.map which is:
   
(hd0)    /dev/sda
(hd0)    /dev/sdb
/dev/sdc    

This iis a triple boot system whuch works fine, and the packages do install normally inspite of the error. Kecec-tools is alsoi listed as installed (not broken). 

Do I *need* this utility?
If not I would just as simply remove it if uneccessary, but it is clear as mud exactly what it does.

A typical error message is:

```

```Reading state information... Done
The following NEW packages will be installed:
  zsh-dev
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
1 not fully installed or removed.
Need to get 80.5kB of archives.
After this operation, 356kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main zsh-dev i386 4.3.10-14ubuntu1 [80.5kB]
Fetched 80.5kB in 0s (111kB/s) 
Selecting previously deselected package zsh-dev.
(Reading database ... 1549024 files and directories currently installed.)
Unpacking zsh-dev (from .../zsh-dev_4.3.10-14ubuntu1_i386.deb) ...
Setting up kexec-tools (1:2.0.1-2ubuntu2.1) ...
/usr/sbin/grub-probe: error: /boot/grub/device.map:4: No open parenthesis found.
dpkg: error processing kexec-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up zsh-dev (4.3.10-14ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic-pae
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
.: 6: Can't open /scripts/casper-functions
Errors were encountered while processing:
 kexec-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```

---

### Post by katykat on 2010-12-20
Well.... 

Here goes ...................

[COLOR=Red]**BUMP**[/COLOR]

---

### Post by katykat on 2010-12-20
How do I delete accidentally duplicated posts???

---

