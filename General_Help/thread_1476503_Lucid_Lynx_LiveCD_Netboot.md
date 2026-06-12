---
title: "Lucid Lynx LiveCD Netboot"
date: 2010-05-07
forum: General Help
---

### Post by thx2000 on 2010-05-07
Has anyone been able to get this running?  I just modified my working config from 9.10, however my clients instantly reboot after downloading vmlinuz and initrd.lz.

Here's my 10.04 config from pxelinux.cfg/default

```

        label ubuntu-10.04-desktop
                menu label Ubuntu 10.04 Live CD
                kernel ubuntu-10.04-desktop/vmlinuz
                append boot=casper netboot=nfs nfsroot=192.168.125.60:/srv/nfs/netboot/ubuntu-10.04-desktop initrd=ubuntu-10.04-desktop/initrd.lz --

```

Thanks!

-THX2000

---

### Post by jp107 on 2010-05-13
I can't get the 10.04 livecd to PXE netboot either, my setup works fine for 9.10 and earlier releases bug it just hangs when 10.04 boots (as if it never tries to nfs mount the root partition).

---

### Post by ameno on 2010-05-16
i have 2 pcs with a tftpboot installation (desktop + laptop)
the desktop (core2duo+g45 chipset) boots the live cd well, the laptop (i5 thinkpad t410s) does not.
it "hangs" at the logo with the progress bar.

if you switch to the first console (ctrl+alt+F1) immediately, you can see the kernel messages. the last one is "RPC: Registered tcp NFSv4.1 backchannel transport module."

after the system has booted into the kernel, it requests an ip via dhcp (again) and sends out some ipv6 stuff (router solicitation), but i dont see any tries to mount the nfs.

---

### Post by ameno on 2010-05-17
lol.
in my case the reason was pretty obvious: the ip of the nfsroot parameter was wrong. (i have copied the pxelinux.cfg to the other machine and forgot to change the ip)

---

### Post by thx2000 on 2010-05-17
Well, I feel dumb.  After tinkering around with the original iso I downloaded, I noticed a few unreadable files and a few empties.  md5sum'd the iso and found I had a bad copy of the iso.  Redownloaded the iso, recopied everything to where it was supposed to go and it fired right up.  Now I just wish that was the first thing I had tried.

-THX2000

---

### Post by Matthew.Geier on 2010-06-09
None of the things here worked for me. A configuration that worked perfectly for both 09.04 and 09.10 hangs with 10.04. I've managed to determine that it hangs when it appears to fail to bring up the network interface so that it can nfs mount the live CD image.

 The text mode installer works fine - but it boots straight out of the initrd it fetches with tftp.

 Both 10.04 32 bit and 64bit die at the same point. 

 It appears that the script that brings up and acquires an address for the Ethernet doesn't wait for the driver to initialise and link to be acquired before giving up. With no network interface active I assume the nfs mount hangs.

---

### Post by bradskins on 2010-06-11
Anything new advancements here?  I'm have the exact same problem ... As Matthew

---

### Post by bradskins on 2010-06-13
I think its our Ubuntu NFS shares.  Netbooting the LiveCD works fins with OS X NFS Shares.  I'm gonna check into it.

---

### Post by zyberwoof on 2011-02-07
I just got my 10.04 live CD to netboot properly.  I already had a working PXE environment before I tried this.  

All I did was:
[LIST=1]
[*]Mount the Ubuntu Desktop 10.04 i386 ISO.
[*]Copy all of the files on the ISO to /mnt/netboot/iso/ubuntu/desktop/10.04/i386/
[*]Appended these lines to my pxelinux.cfg/default file.  ```
LABEL Ubuntu-10.04-i386-LiveCD
	KERNEL iso/ubuntu/desktop/10.04/i386/casper/vmlinuz
	APPEND boot=casper netboot=nfs nfsroot=192.168.1.13:/mnt/netboot/iso/ubuntu/desktop/10.04/i386/ initrd=iso/ubuntu/desktop/10.04/i386/casper/initrd.lz --
```
[/LIST]

NOTE: My PXE NFS environment is setup at /mnt/netboot.  Odds are your environment is different.

---

