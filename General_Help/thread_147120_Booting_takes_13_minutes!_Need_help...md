---
title: "Booting takes 13 minutes! Need help.."
date: 2006-03-19
forum: General Help
---

### Post by haaglin on 2006-03-19
Hi. 

My sisters computer, running kubuntu, takes about 13 minutes from booting to the login screen. it doesnt hang at anything special, but everything is going really slow. "Calculating Module Dependencies" is the slowest of them all. 

I have tried to upgrade the kernel, and that didn't work, and there is no errors in the kernel log. I really don't want to reinstall. Really need some help here.. :-k

---

### Post by Mr Squiddy on 2006-03-19
What's performance like when you have booted up?

Is DMA enabled on your hard drive?  Try 'hdparm -d /dev/hda'  where '/dev/hda' is your hard drive.

---

### Post by haaglin on 2006-03-19
Yes DMA is enabled. The performance is poor for about 5 minutes after login. and i cant press anything on the kicker. but after that all is ok.

This is the specs of it: 
AMD Athlon XP2000
1024MB DDR
40GB Harddrive (about 20gb free)

---

### Post by incubus on 2006-03-19
Any different cards, like graphics or sound, that  require a special driver (module)?

incubus

PS: That's so strange. Are you really sure your hardware is fully working?
$ cat /proc/cpuinfo
$ cat /proc/meminfo
$ df -h

---

### Post by haaglin on 2006-03-20
Yes, the Atheros based Wlan card needs a module afaik. it doesnt work without the restricted modules. 

It has a nVidia gforce4 mx 440, running nvidia drivers. 

> 
vidar@monica:~$  cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Athlon(tm) XP 2000+
stepping        : 0
cpu MHz         : 1666.922
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 3309.56

vidar@monica:~$ cat /proc/meminfo
MemTotal:      1036456 kB
MemFree:        368756 kB
Buffers:         91900 kB
Cached:         301288 kB
SwapCached:          0 kB
Active:         319248 kB
Inactive:       212344 kB
HighTotal:      131008 kB
HighFree:          120 kB
LowTotal:       905448 kB
LowFree:        368636 kB
SwapTotal:      979924 kB
SwapFree:       979924 kB
Dirty:             140 kB
Writeback:           0 kB
Mapped:         206388 kB
Slab:           122344 kB
CommitLimit:   1498152 kB
Committed_AS:   356116 kB
PageTables:       1612 kB
VmallocTotal:   114680 kB
VmallocUsed:     31272 kB
VmallocChunk:    81908 kB

vidar@monica:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              19G   13G  4,5G  75% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-k7/volatile
/dev/hda5              19G  8,7G   11G  47% /media/hda5
/dev/hdb1             7,5G  580M  6,9G   8% /media/hdb1



---

### Post by haaglin on 2006-03-21
any suggestions?

---

### Post by sleepkreep on 2006-03-22
post your /boot/grub/menu.lst file here.  I think it may be calling your kernel with the wrong parameters.  Oh, and just to make sure everything matches up, post the output of *uname -r*.  If you can, make sure you're using the k7 kernel.  I imagine you'll see a great performance boost.  But maybe not :)

---

### Post by haaglin on 2006-03-23
she's using 2.6.12-10-k7

menu.lst:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash vga=792

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-k7
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by antidrugue on 2006-03-23
Do you get the same problem with the 3 different kernels you have?

You said she is using "kernel 2.6.12-10-k7". Same problem with "kernel 2.6.12-10-386" and "kernel 2.6.12-9-386"?

Do you have all the needed modules installed for that k7 kernel?
```

dpkg -l | grep k7

```

---

### Post by haaglin on 2006-03-23
I will try to use one of the other ones. I did try to update the K7 one, but the same problem with that one too. 

ii  linux-headers-2.6.12-10-k7             2.6.12-10.30                         Linux kernel headers 2.6.12 on AMD K7
ii  linux-headers-k7                       2.6.12.16.1                          Linux kernel headers on AMD K7
ii  linux-image-2.6.12-10-k7               2.6.12-10.30                         Linux kernel image for version 2.6.12 on AMD
ii  linux-restricted-modules-2.6.12-10-k7  2.6.12.4-11.1                        Non-free Linux 2.6.12 modules on AMD K7

---

### Post by otetiani on 2006-03-23
I may be on the wrong track, but I just went through something similar wwhen I changed to booting from a WD IDE HD.

Originally it was jumpered as Master and it was taking >5 minutes to boot.

I switched the jumper to CS when someone recommended and it worked!

---

### Post by sleepkreep on 2006-03-23
I hope the above works, because I'm stumped.

---

### Post by haaglin on 2006-03-25
double post.

---

### Post by haaglin on 2006-03-25
[QUOTE=otetiani]I may be on the wrong track, but I just went through something similar wwhen I changed to booting from a WD IDE HD.

Originally it was jumpered as Master and it was taking >5 minutes to boot.

I switched the jumper to CS when someone recommended and it worked![/QUOTE]

WoW! That worked! Thank you! From 13 minutes to 1! 
Thanks to everyone else who helped too.

---

### Post by xyz on 2006-03-28
[QUOTE=haaglin]WoW! That worked! Thank you! From 13 minutes to 1! 
Thanks to everyone else who helped too.[/QUOTE]

I'm having what seems like similar boot time problems.
Could someone explain what > WD IDE HD is and how to implement it?

Many thanks for your help.

Info:

> /dev/hda:
 using_dma    =  1 (on)


Also:
```
df -h
```

> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              14G  4.5G  8.6G  35% /
tmpfs                 244M     0  244M   0% /dev/shm


And:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single rootflags=data=writeback

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash
# nonaltoptions=quiet splash rootflags=data=writeback

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda3 ro quiet splash reboot=h
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-686-smp
boot

title		Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda3 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.12-10-686-smp
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Toshiba Satellite A 40
Dual boot XP/Breezy 5.10
2.6.12-10-686-smp
Intel(R) Celeron(R) CPU 2.70 GHz
128 KB L2 cache/512 RAM

---

### Post by trotski on 2006-03-28
WD IDE HD = Western Digital Hard Drive with the older wide ribbon cable interface.

---

