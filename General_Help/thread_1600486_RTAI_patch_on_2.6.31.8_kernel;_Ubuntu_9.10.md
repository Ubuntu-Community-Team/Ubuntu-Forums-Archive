---
title: "RTAI patch on 2.6.31.8 kernel; Ubuntu 9.10"
date: 2010-10-19
forum: General Help
---

### Post by Mecasickle on 2010-10-19
Hey guys, 

I;m installing RTAI and I get this message. I can't seem to find the solution, because I really don't know exactly what the main problem is. There are a list of error,s and warnings that I 'm not sure from where should I tackle the problem:

Here is what I get when I boot my 2.6.31.8 kernel with GRUB. (I used the RTAI x86 compatible patch):

---

Warning: unable to finf a suitable fs in  /proc/mounts , is it mounted?
Use --subdomain fs to override.
init: ureadahread main process (324) terminated with status 5 fsck from util-linux-ng 2.16
/dev/sda5: clean, 499838/1859584 files, 4399494/7434070 blocks
[5.635400] EXT4-fs (sda5): Filesystem with huge files cannot be mounter RDWR without CONFIG_LBDAF
mount: cannot remount block device /dev/sda5 read-write, is write-protected
mountall: mount / [345] terminated with status 32
mountall: Filesystem could not be mounted: /
init: mountall main process(327) terminated with status 4
Mount of root filesystem dailed.
A maintence shell will be started.
Control-D witll termiante this shell and reboot the system
root@myusername-laptop:~#[10.315752] uvcvideo: Failed to query (129) UVC probe control: -32 (exp.26)
[10.315882] uvcvideo: Failed to initialize the device(-5)

---

After that system does NOT boot. Any ideas? Am I missing something?

Thanks!

---

### Post by dino99 on 2010-10-19
wonder why you need this thing, but here is an old howto:

[http://www.captain.at/programming/rtai/kernel-2.4.php](http://www.captain.at/programming/rtai/kernel-2.4.php)

or a more recent:

[http://wiki.linuxcnc.org/emcinfo.pl?Debian_Lenny_Compile_RTAI](http://wiki.linuxcnc.org/emcinfo.pl?Debian_Lenny_Compile_RTAI)

and one more:

[https://www.rtai.org/RTAILAB/RTAI-TARGET-HOWTO.txt](https://www.rtai.org/RTAILAB/RTAI-TARGET-HOWTO.txt)

---

### Post by Mecasickle on 2010-10-19
Thanks a lot man! 

I actually used this link:

[http://www.linuxforums.org/forum/kernel/161029-solved-rtai-patched-kernel-compiling-irq-error.html](http://www.linuxforums.org/forum/kernel/161029-solved-rtai-patched-kernel-compiling-irq-error.html)

and it solved my problem!

I now have RTAI 3.8 with the 2.6.31.8 kernel (x86 arch) on Ubuntu 9.10. I will be uploading a installation manual soon !

---

### Post by Mecasickle on 2010-10-20
Guys! I just finished the complete tutorial!

Check it out on my webpage:

[http://arturodeza.wikidot.com/data-log](http://arturodeza.wikidot.com/data-log)

---

