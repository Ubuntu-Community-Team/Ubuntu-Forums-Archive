---
title: "Boot up crashes after latest xorg update on Karmic"
date: 2010-01-21
forum: General Help
---

### Post by battlecyborg on 2010-01-21
My system is a Gigabyte GA-P35-DQ6 with Radeon 5770. The system was rock solid and everything working fine until the latest update I applied 30 minutes ago.  The system is stuck on the little circle icon before the login screen.

I'm not able to ssh or telnet to the machine to check the log files.  I edited my grub.conf a while back and I don't seem to be able to call up the recovery kernel.  I can read up on the grub options, but I was wondering if others seen this issue already and know of a workaround.

---

### Post by amsterdamharu on 2010-01-21
You can go to command in grub by pressing c at the menu, then see if any of your old kernels are still arround:

```

find /boot/grub/stage1

```
results in (hd?,?)

```

find (hd?,?)/boot/vmlin(press tab here)

```

results in:
Possible files are: vmlinuz-2.6.24-24-generic vmlinuz-2.6.24-25-generic vmlinu
z-2.6.24-26-generic vmlinuz-boot

```

root (hd?,?)
kernel vmlinuz-2.6.24-24-generic

```

Now you have your kernel, see if it has the right initrd:

```

 find (hd0,4)/boot/initrd(press tab)

```

results in
Possible files are: initrd.img-2.6.24-24-generic. ...

```

initrd  /boot/initrd.img-2.6.24-26-generic
boot

```

That should boot an older kernel (if still there).

You can try to press control alt F1 to go to non graphic login and see if renaming your xorg.conf has any affect (it will go to xorg.fallback if conf is not there I think).

---

### Post by ddrevensek on 2010-01-21
I would like to report similar case. After updating my 64 bit karmic machine (ASUS P7P55D PRO, Intel i7 860, HD5770) that was running stable some 12 hours ago, machine could not start gnome on reboot. 
I was able to use recovery kernel and I tried to reconfigure X11, but with no success.
Is there  a way to undo last xorg update from console to get my system working again?

---

### Post by amsterdamharu on 2010-01-21
```

sudo  mv /etc/X11/xorg.conf /etc/X11/xorg.old
startx

```

Not sure if this is a messed up xorg.conf but with no xorg it will fall back and use some default values (lo res no specific driver) in the gui you can try to change some settings.

---

### Post by ddrevensek on 2010-01-21
> **amsterdamharu said:**
> ```

sudo  mv /etc/X11/xorg.conf /etc/X11/xorg.old
startx

```Not sure if this is a messed up xorg.conf but with no xorg it will fall back and use some default values (lo res no specific driver) in the gui you can try to change some settings.

Thank you for helping me, but I have already tried to modify xorg.conf, because there was error report that  BusID "PCI_1:0:0" was incorrect ( that computer is not accessible for me right now to check exact message).
I have tried to remove (rename) xorg.conf as you suggest and restart, but the same problem was still there. 
So my idea was, there was something wrong with the last update, because I think xorg update was included in the list of updates.
I have just started fine working ubuntu yesterday, done some browsing with firefox, confirmed updates and restarted computer, when troubles started:(.

---

### Post by amsterdamharu on 2010-01-21
Yes, looks like changing xorg cannot do anything for you
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
"This method **does not** work with *Hardy Heron* and probably all versions to follow (including Intrepid Ibex).  This method seems to ONLY work with *Gutsy Gibbon* and older.
I think this is because the newer versions of xserver-xorg rely more on auto-detecting the configuration during runtime rather than looking at xorg.conf."

The funny thing is that when I quickly read through this site (and some other docs on help.ubuntu.com):
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)
all the trouble shooting is done with editing xorg.

Did you try stopping gnome, reconfigure and then starting it (use vesa in reconfig)?
sudo /etc/init.d/gdm stop #(for gnome)
sudo /etc/init.d/kdm stop #(for kde)
sudo /etc/init.d/xdm stop #(for xfce)
sudo dpkg-reconfigure xserver-xorg

---

### Post by ddrevensek on 2010-01-21
Yes, I have tried to reconfigure xserver to use at least vesa, but this action has finished with an error (something about troubles with BusID "PCI:1:0:0", that was previously mentioned in xorg.conf - but xorg.conf was already removed! ).
In the evening I'm going to check hardware (it's a double boot machine), but I doubt it is a hardware.
[]("http://ubuntuforums.org/member.php?u=898154")

---

### Post by amsterdamharu on 2010-01-21
There must be some automatic way that ubuntu configures x or we are missing something. Since changing xorg.conf doesn't seem to do much.

Maybe booting an older kernel / initrd will help in combination with using vesa (driver might be updated too but vesa should work).

---

### Post by battlecyborg on 2010-01-21
I used the recovery disk to mount my root directory to extract the last log messages.

dpkg.log
```

2010-01-20 22:03:32 startup archives unpack
2010-01-20 22:03:49 upgrade bzr 2.0.0-0ubuntu1 2.0.2-0ubuntu1
2010-01-20 22:03:49 status half-configured bzr 2.0.0-0ubuntu1
2010-01-20 22:03:52 status unpacked bzr 2.0.0-0ubuntu1
2010-01-20 22:03:52 status half-installed bzr 2.0.0-0ubuntu1
2010-01-20 22:03:52 status triggers-pending man-db 2.5.6-2
2010-01-20 22:03:52 status half-installed bzr 2.0.0-0ubuntu1
2010-01-20 22:03:53 status triggers-pending doc-base 0.9.3
2010-01-20 22:03:53 status half-installed bzr 2.0.0-0ubuntu1
2010-01-20 22:03:53 status half-installed bzr 2.0.0-0ubuntu1
2010-01-20 22:03:53 status unpacked bzr 2.0.2-0ubuntu1
2010-01-20 22:03:54 status unpacked bzr 2.0.2-0ubuntu1
2010-01-20 22:03:54 upgrade xserver-common 2:1.6.4-2ubuntu4 2:1.6.4-2ubuntu4.1
2010-01-20 22:03:54 status half-configured xserver-common 2:1.6.4-2ubuntu4
2010-01-20 22:03:54 status unpacked xserver-common 2:1.6.4-2ubuntu4
2010-01-20 22:03:54 status half-installed xserver-common 2:1.6.4-2ubuntu4
2010-01-20 22:03:54 status half-installed xserver-common 2:1.6.4-2ubuntu4
2010-01-20 22:03:54 status half-installed xserver-common 2:1.6.4-2ubuntu4
2010-01-20 22:03:54 status unpacked xserver-common 2:1.6.4-2ubuntu4.1
2010-01-20 22:03:54 status unpacked xserver-common 2:1.6.4-2ubuntu4.1
2010-01-20 22:03:54 upgrade xserver-xorg-core 2:1.6.4-2ubuntu4 2:1.6.4-2ubuntu4.1
2010-01-20 22:03:54 status half-configured xserver-xorg-core 2:1.6.4-2ubuntu4
2010-01-20 22:03:54 status unpacked xserver-xorg-core 2:1.6.4-2ubuntu4
2010-01-20 22:03:54 status half-installed xserver-xorg-core 2:1.6.4-2ubuntu4
2010-01-20 22:03:55 status half-installed xserver-xorg-core 2:1.6.4-2ubuntu4
2010-01-20 22:03:55 status half-installed xserver-xorg-core 2:1.6.4-2ubuntu4
2010-01-20 22:03:55 status unpacked xserver-xorg-core 2:1.6.4-2ubuntu4.1
2010-01-20 22:03:55 status unpacked xserver-xorg-core 2:1.6.4-2ubuntu4.1
2010-01-20 22:03:55 trigproc man-db 2.5.6-2 2.5.6-2
2010-01-20 22:03:55 status half-configured man-db 2.5.6-2
2010-01-20 22:03:57 status installed man-db 2.5.6-2
2010-01-20 22:03:57 trigproc doc-base 0.9.3 0.9.3
2010-01-20 22:03:57 status half-configured doc-base 0.9.3
2010-01-20 22:03:58 status installed doc-base 0.9.3
2010-01-20 22:03:59 startup packages configure
2010-01-20 22:03:59 configure bzr 2.0.2-0ubuntu1 2.0.2-0ubuntu1
2010-01-20 22:03:59 status unpacked bzr 2.0.2-0ubuntu1
2010-01-20 22:03:59 status unpacked bzr 2.0.2-0ubuntu1
2010-01-20 22:03:59 status unpacked bzr 2.0.2-0ubuntu1
2010-01-20 22:03:59 status half-configured bzr 2.0.2-0ubuntu1
2010-01-20 22:04:05 status installed bzr 2.0.2-0ubuntu1
2010-01-20 22:04:05 configure xserver-common 2:1.6.4-2ubuntu4.1 2:1.6.4-2ubuntu4.1
2010-01-20 22:04:05 status unpacked xserver-common 2:1.6.4-2ubuntu4.1
2010-01-20 22:04:05 status half-configured xserver-common 2:1.6.4-2ubuntu4.1
2010-01-20 22:04:05 status installed xserver-common 2:1.6.4-2ubuntu4.1

```

messages:
```

Jan 20 22:45:03 akira-ub kernel: [   24.621118] EXT3-fs: recovery complete.
Jan 20 22:45:03 akira-ub kernel: [   24.621122] EXT3-fs: mounted filesystem with writeback data mode.
@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^C^@^Kõ^O¶^@]^[Z^[9^[^]^Zñ^ZÒ^Z®^Z<90>^Yä^YÅ^Y§^Y<88>^Yj^Y=^Y^\^Xü^XÝ^XÁ^X¥^X\^X9^X^V^W÷^WÚ^W¼^W<9e>^W<82>^Wd^WJ^V¹^V<9d>^V|^V]^V^Y^Uú^Uª^U<8c>^Up^Q^M^PÒ^UO^LR^Lk^L^Z^Kü^Kâ^KÈ^K¬^K<8f>^Kh^KH^K(^Fl^FO^F1^F^O^Eì^EÌ^E¦^E<8a>^Ej^EL^E^M^Dð^DÒ^D¡^D<83>^Df^D9^D^]^Cú^CÝ^CÀ^C¦^C<89>^Ck^C^T^Bð^B¸^B<9a>^Bz^Bz^L6^L^X^K^@^[

```

The last thing in messages is a ton of garbled output.  I used fsck to check all my disks.  They look ok, while I was at it, I fixed my grub file as well.  I will try to boot an older kernel or single user mode.  

if you guys know how I can revert the latest xorg package back to the older one, that would be what I'd like to do.  Please advise.
[code]

---

### Post by battlecyborg on 2010-01-21
Also, to add, there doesn't seem any changes in Xorg.conf on my system since 12/27.

Also, I don't see anything unusual in the xorg.log either.  So, its possible its not specifically a X problem.

---

### Post by bazik on 2010-01-21
i have the exact same problem, seems to be something to do with ATI, i have a Radeon HD4850.

I see the ubuntu symbol in the boot, then the screen goes black and shutsdown

anyone got this solved?

---

### Post by ddrevensek on 2010-01-21
It seems I have solved my graphics issue.

Here it is what I have done.

1. In /etc/X11/xorg.conf under section Device I have replaced "fglrx" with "vesa" and was able to start graphics under vesa.
2. I followed instructions in [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat912-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat912-inst.pdf) to remove ati driver
3. I downloaded new driver [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run) and installed it following instructions from the previous pdf.
4. After restarting the machine graphics was alive again

---

### Post by bazik on 2010-01-21
> **ddrevensek said:**
> It seems I have solved my graphics issue.

Here it is what I have done.

1. In /etc/X11/xorg.conf under section Device I have replaced "fglrx" with "vesa" and was able to start graphics under vesa.
2. I followed instructions in [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat912-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat912-inst.pdf) to remove ati driver
3. I downloaded new driver [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run) and installed it following instructions from the previous pdf.
4. After restarting the machine graphics was alive again


Many thanks, you can just uninstall the driver and the boot works again.

From the pdf: 
1) Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux 
driver download. 
2) Enter the command sh ./ati-driver-installer-9-12-x86.x86_64.run to launch the ATI 
Proprietary Linux driver installer.

---

### Post by battlecyborg on 2010-01-21
I had independantly gone that route too once I was able to boot in safe mode.  I edited xorg.conf and also reinstalled core x11 packages.  Also removed any unneeded xorg drivers.  I used to have nvidia card in the machine, so I removed all references to that as well.

After reinstall of ATI proprietary installer, things look ok again.  I think update notes should have bold warning about these issues if they are already known.

---

