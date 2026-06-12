---
title: "Speed up Ubuntu 11.04"
date: 2011-06-01
forum: General Help
---

### Post by 8jwong14 on 2011-06-01
Ubuntu 11.04 is already quite fast.  But is there any way to speed it up even more.  In general, what are ways to speed up Ubuntu.  I want to compile a list of things to do and such be it as easy as removing unnecessary programs or as hard (For some) as some messing around with the terminal.

Any suggestions would be appreciated.   Want to speed up Ubuntu as much as possible.

List ( Credit given to those who recommended something on here.  If possible, credit will also be given to the creator of the idea of tip.
-Use a SSD as the boot drive for faster boot speeds than normal HDDs.

-Remove unnecessary stuff from startup to improve boot speeds.  Go to "Startup Applications" and uncheck any unneeded stuff 
"Bluetooth Manager" if you don't use bluetooth.
"Remote Desktop" if you don't use remote desktops

-Dustin2128
Replace GNOME with another desktop environment such as XFCE, Openbox, KDE, etc.

-sbraz
Compile a custom kernel WARNING: Keep at least one stock kernel or you may have to chroot or install the entire OS again!  A custom kernel boots faster, and might perform better for various reasons.
Back to 10.04 my network card didn't work on my desktop but with the latest stable release from kernel.org solved my issue.  Once you've mastered how to do it it's just a matter of reading the matrix. 
some other reasons and how-tos.
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

-sbraz
For computers with 2+ ram, one can mount a volatile ramdisk to /tmp or another path.  
"There are still old laptops/pcs and even new netbooks around which are  limited to 1GB ram maxed, so yes unfortunately there is some swapping  around the globe. For example, sometimes at work i swap a little even with 4GB ram on my netbook. Hibernation takes time to write and then read like 1-2gb ram (if you  close all the apps before pressing "hibernate" there's no point in  hibernation in the first place). since hibernation utilities uses the  swap partition to store ram's data, and that improving swap's  performance is free of charge... why not?"

---

### Post by collisionystm on 2011-06-01
Search for startup applications. Uncheck unnecessary.

---

### Post by Dustin2128 on 2011-06-01
Use a lighter DE, like xfce or openbox. Should really improve performance.

---

### Post by 8jwong14 on 2011-06-01
> **Dustin2128 said:**
> Use a lighter DE, like xfce or openbox. Should really improve performance.
Are those DEs called desktop environments?  And are they to replace GNOME?

---

### Post by collisionystm on 2011-06-01
> **8jwong14 said:**
> Are those DEs called desktop environments?  And are they to replace GNOME?


Yes.

---

### Post by sbraz on 2011-06-01
-compile a customized kernel

-if you plan on swapping because you have low ram (oh boy..) and/or frequently use hibernation, move/place the swap partition between "/" and "/home" partitions. traditional hdds are faster at the beginning (outer rings = faster linear speed)

-move temp files on a ramdrive (tweak often used with ssd)

---

### Post by 8jwong14 on 2011-06-01
> **sbraz said:**
> -compile a customized kernel

-if you plan on swapping because you have low ram (oh boy..) and/or frequently use hibernation, move/place the swap partition between "/" and "/home" partitions. traditional hdds are faster at the beginning (outer rings = faster linear speed)

-move temp files on a ramdrive (tweak often used with ssd)
Coudl you elaborate?  Maybe give some links to information about how to do those or provide how to do them yourself?

---

### Post by Dustin2128 on 2011-06-01
> **8jwong14 said:**
> Coudl you elaborate?  Maybe give some links to information about how to do those or provide how to do them yourself?
No idea what he's talking about on the swap partition, but I suspect it is unnecessary as most computers today have enough ram as to never need to access the swap. I think a custom kernel is overkill, personally.

---

### Post by linuxinstalledfromhdd on 2011-06-01
> **8jwong14 said:**
> Ubuntu 11.04 is already quite fast.  But is there any way to speed it up even more.  In general, what are ways to speed up Ubuntu.  I want to compile a list of things to do and such be it as easy as removing unnecessary programs or as hard (For some) as some messing around with the terminal.

Any suggestions would be appreciated.   Want to speed up Ubuntu as much as possible.

List:
-Use a SSD as the boot drive for faster boot speeds than normal HDDs.

-Remove unnecessary stuff from startup to improve boot speeds.  Go to "Startup Applications" and uncheck any unneeded stuff 
"Bluetooth Manager" if you don't use bluetooth.
"Remote Desktop" if you don;t use remote desktops

-Replace GNOME with another desktop environment.
XFCE, Openbox, KDE, etc

Try Madbox with a live disc or USB Flash Drive. You can install it to your flash drive with Ubuntu Startup Disc Creator.

[http://madbox.tuxfamily.org/](http://madbox.tuxfamily.org/)

Save yourself some time. :)

---

### Post by sbraz on 2011-06-02
> **8jwong14 said:**
> Coudl you elaborate?  Maybe give some links to information about how to do those or provide how to do them yourself?
oh cool sure thing! i've used this guide when i first tried:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

my advice: when you mess with kernels, [COLOR="Red"]DO KEEP AT LEAST ONE STOCK KERNEL[/COLOR] or you might end up like me chrooting in live mode or worse reinstalling the whole os.... not cool. :(


and here's how to mount a volatile ramdisk to /tmp (or any path btw) check post 5 and 6:
[http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-general-questions/359159-mounting-tmp-ram.html](http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-general-questions/359159-mounting-tmp-ram.html)

> **Dustin2128 said:**
> No idea what he's talking about on the swap partition, but I suspect it is unnecessary as most computers today have enough ram as to never need to access the swap.
-there are still old laptops/pcs and even new netbooks around which are limited to 1GB ram maxed, so yes unfortunately there is some swapping around the globe. :)
for example, sometimes at work i swap a little even with 4GB ram on my netbook. :D

-hibernation takes time to write and then read like 1-2gb ram (if you close all the apps before pressing "hibernate" there's no point in hibernation in the first place). since hibernation utilities uses the swap partition to store ram's data, and that improving swap's performance is free of charge... why not?

here's a typical graphic of a traditional hdd read performance vs head position (i can't do any write tests, it's my system disk):
[[IMG]http://img171.imageshack.us/img171/3345/disk.th.png[/IMG]](http://img171.imageshack.us/i/disk.png/)
as you can see performance is not constant at all. this happens because platter's linear speed diminishes in direct relation to cylinder position (hdd reads/writes from the outermost to the innermost cylinder).

the easiest way to have a faster swap partition is done by thinking ahead and setting the partitions properly while installing the os.

alternatively, **maybe after a backup of your personal documents**, you can boot from a live distro and use your favourite partitioning utility to resize, move, cut, paste, undo, no wait reboot, read some more info about which size root should be, thinking about converting your /home to another filesystem, then think again, stop thinking and finally APPLY to achieve something like this:
[[IMG]http://img263.imageshack.us/img263/6409/screenshotdevsdagpartedy.th.png[/IMG]](http://img263.imageshack.us/i/screenshotdevsdagpartedy.png/)

you need to edit /etc/fstab to let linux know about your changes on your disk, like this:
```
sbraz@sbraz-netbook:~$ cat /etc/fstab
proc      /proc           proc     nodev,noexec,nosuid            0       0
/dev/sda1 /               reiserfs defaults                       0       1
/dev/sda3 /home           reiserfs defaults                       0       2
/dev/sda2 none            swap     sw                             0       0
```

Done! :popcorn:

some distros uses this "optimized" layout by default, i don't get why some others choose to go default in opposition of some simple laws of physics confirmed by measurements still consistent since the invention of the first hard drive ever, but it's okay: *fact until proven wrong*.

incidentally, we were discussing about another aspect of optimizing ram/swapping/caching performance on another topic, you might want to check it out:
[http://ubuntuforums.org/showthread.php?t=1768421](http://ubuntuforums.org/showthread.php?t=1768421) - post 40, 41.

> **Dustin2128 said:**
> I think a custom kernel is overkill, personally.
a custom kernel boots faster, and might perform better for various reasons.
back to 10.04 my network card didn't work on my desktop but with the latest stable release from kernel.org solved my issue.
once you've mastered how to do it it's just a matter of reading the matrix. :)

oh it's also instructional, funny, and more importantly VERY satisfactory in the long run.

some other reasons and howtos
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by 8jwong14 on 2011-06-02
> **linuxinstalledfromhdd said:**
> Try Madbox with a live disc or USB Flash Drive. You can install it to your flash drive with Ubuntu Startup Disc Creator.

[http://madbox.tuxfamily.org/](http://madbox.tuxfamily.org/)

Save yourself some time. :)
What are the benefits of Madbox over Ubuntu or other environments?

---

### Post by 8jwong14 on 2011-06-02
Never mind

---

