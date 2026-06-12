---
title: "Unable to upgrade kernel package"
date: 2012-07-29
forum: General Help
---

### Post by Ansowi on 2012-07-29
I checked for updates on my fresh Xubuntu install, got about 200 however one installed to fail.

```

bui@bluefly:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-generic : Depends: linux-image-3.2.0-27-generic but it is not installed
E: Unmet dependencies. Try using -f.
bui@bluefly:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.2.0-27-generic
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed
  linux-image-3.2.0-27-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/38.0 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 151271 files and directories currently installed.)
Unpacking linux-image-3.2.0-27-generic (from .../linux-image-3.2.0-27-generic_3.2.0-27.43_i386.deb) ...
Done.
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb (subprocess): data: internal bzip2 read error 'UNEXPECTED_EOF'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-27-generic_3.2.0-27.43_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./lib/modules/3.2.0-27-generic/kernel/drivers/staging/comedi/drivers/multiq3.ko'
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-27-generic_3.2.0-27.43_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bui@bluefly:~$ 

```

Any ideas on how to fix this? Thanks.

---

### Post by svrkispm on 2012-07-29
Afaik this means the downloaded files were corrupted. Try to run
```

sudo apt-get clean

```
and try to install them again.

If this happens again there is a good chance your hard drive might be corrupted, i would look in
```

dmesg | tail

```
for more info on this.

If this doesnt help try to post more info, maybe output of
```

df
df -i
mount

```

---

### Post by Ansowi on 2012-07-30
Eh, well, after I rebooted it seems I messed up the kernel. Had to re-install.

This time I'm updating manually using apt from the command line, and it seems the kernel related packages are kept back.

I'm not sure if I should upgrade them as it might break my installation again, any suggestions on what to do?

```

bui@bluefly:~$ uname -r
3.2.0-23-generic

```

---

