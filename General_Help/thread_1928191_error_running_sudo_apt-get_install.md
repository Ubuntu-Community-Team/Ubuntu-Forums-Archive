---
title: "error running sudo apt-get install"
date: 2012-02-19
forum: General Help
---

### Post by pwl2706 on 2012-02-19
Hi,

I got an error from the Update Manager (Package Broken)

so I opened a Terminal and ran these commands

```

[B]sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get install[/B]

```

on the last one I got this error:

[B]Error! Your kernel headers for kernel 3.0.0-16-generic cannot be found.
Please install the linux-headers-3.0.0-16-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located[/B]

any advice before I restart  or -reinstall?

thanks
Philip

PS, I got other errors too,after the above one:

run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
**/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).**
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
[B]Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-16-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

---

### Post by ajgreeny on 2012-02-19
Try using synaptic, which can fix broken package usually quite easily and quickly.

Or try ```
sudo apt-get install -f
```

---

### Post by pwl2706 on 2012-02-19
ok, I ran
```
sudo apt-get install -f
```

and it seems to be blocked - so far it's taken nearly an hour...

I don't want to restart unless advised to do so by an expert as I am worried that it won't reboot again successfully...

---

### Post by wildmanne39 on 2012-02-19
Hi, what makes you think it is blocked? when it is done you may not see any messages if there were no errors.

You should run:
```
sudo apt-get update
```
post all errors here.

If in doubt post a screenshot of what is going on in the terminal before running that command.
Thanks

---

### Post by eatabean on 2012-02-21
Same problem here. I have been scouring the internet and see this problem everywhere. I cannot get anywhere.

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jim@jim-laptop:~$ sudo fuser -v /var/cache/debconf/config.dat
                     USER        PID ACCESS COMMAND
/var/cache/debconf/config.dat:
                     root      11902 F.... frontend
jim@jim-laptop:~$ lsof /var/cache/debconf/config.dat
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /root/.gvfs
      Output information may be incomplete.
jim@jim-laptop:~$ sudo lsof /var/cache/debconf/config.dat
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/jim/.gvfs
      Output information may be incomplete.
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
frontend 11902 root    4uW  REG    8,1    37180 2367727 /var/cache/debconf/config.dat

---

