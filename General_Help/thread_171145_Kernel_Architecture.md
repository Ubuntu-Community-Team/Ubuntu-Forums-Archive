---
title: "Kernel Architecture"
date: 2006-05-06
forum: General Help
---

### Post by anubix on 2006-05-06
ok, so i've got an orinoco gold and trying to get kismet to work
[http://ubuntuforums.org/showthread.php?t=79160&highlight=how-to+kismet](http://ubuntuforums.org/showthread.php?t=79160&highlight=how-to+kismet)

how do i tell what kernel-arch (architecture?) i have?
" #apt-get install linux-source build-essential gcc-3.4
#apt-get install linux-headers-<arch>

where <arch> is replaced by your running kernel architechture

386
386-smp
686
686-smp
k7
k7-smp
"

as far as i know, everything else in the howto works, except i get fewked when i "sudo make" there at the end. i get:
sam@portos:~/orinoco/orinoco-0.15rc4$ sudo make
make -C /usr/src/linux-headers-2.6.12-10-386 M=/home/sam/orinoco/orinoco-0.15rc4 KERNELRELEASE=2.6.12-10-386 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/sam/orinoco/orinoco-0.15rc4/orinoco_nortel.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/sam/orinoco/orinoco-0.15rc4/orinoco_nortel.o] Error 127
make[1]: *** [_module_/home/sam/orinoco/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2


any ideas on whats going wrong? or am i already on the right track, and don't know the presumably 4 character command to check the kernel architecture.???

thanks
sam

---

### Post by tseliot on 2006-05-06
```
sudo apt-get install linux-headers-`uname -r`
```

make sure you use a ` (which is different from ' )

---

### Post by anubix on 2006-05-06
ok, so i substituted in "sudo apt-get install linux-headers-`uname -r`" and tried again, and it didn't work.
i know i know little, but to remove all doubt, i blew it all out and started from a clean install, and it still didn't work, now when i put in the first patch line i get:
sam@portos:/orinoco/orinoco-0.15rc4$ sudo patch -p1 --dry-run < orinoco-0.15rc2-dragorn-02.diff
patching file orinoco.c
Hunk #1 FAILED at 447.
Hunk #2 succeeded at 415 with fuzz 2 (offset -95 lines).
Hunk #3 succeeded at 721 with fuzz 1 (offset -455 lines).
Hunk #4 succeeded at 778 with fuzz 1 (offset -454 lines).
Hunk #5 succeeded at 798 (offset -454 lines).
Hunk #6 succeeded at 909 (offset -454 lines).
Hunk #7 succeeded at 1882 (offset -464 lines).
Hunk #8 succeeded at 2492 (offset -469 lines).
Hunk #9 succeeded at 4255 with fuzz 2 (offset -553 lines).
Hunk #10 succeeded at 4383 with fuzz 2 (offset -602 lines).
Hunk #11 FAILED at 4466.
2 out of 11 hunks FAILED -- saving rejects to file orinoco.c.rej
patching file orinoco.h
Hunk #1 succeeded at 110 (offset -30 lines).
patching file prism2header.h

second patch line goes fine, but when i sudo make, i get:
sam@portos:/orinoco/orinoco-0.15rc4$ sudo make
amake -C /usr/src/linux-headers-2.6.12-10-386 M=/orinoco/orinoco-0.15rc4 KERNELRELEASE=2.6.12-10-386 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco_nortel.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/orinoco/orinoco-0.15rc4/orinoco_nortel.o] Error 127
make[1]: *** [_module_/orinoco/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
sam@portos:/orinoco/orinoco-0.15rc4$ sudo make install
make -C /usr/src/linux-headers-2.6.12-10-386 M=/orinoco/orinoco-0.15rc4 KERNELRELEASE=2.6.12-10-386 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco_nortel.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/orinoco/orinoco-0.15rc4/orinoco_nortel.o] Error 127
make[1]: *** [_module_/orinoco/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2


what else can i do?

---

### Post by Sutekh on 2006-05-06
If you are compiling against the kernel headers (particularly the 2.6.12-...) you need gcc-3.4.

Did you install it again after the clean install?
```
sudo apt-get install build-essential gcc-3.4
```

---

### Post by anubix on 2006-05-06
OK, so i started over clean again, and did everything corectly we have figured out so far.
when i get to the first patch comand i get back:
sam@portos:/orinoco/orinoco-0.15rc4$ sudo patch -p1 --dry-run < orinoco-0.15rc2-dragorn-02.diff
patching file orinoco.c
Hunk #1 FAILED at 447.
Hunk #2 succeeded at 415 with fuzz 2 (offset -95 lines).
Hunk #3 succeeded at 721 with fuzz 1 (offset -455 lines).
Hunk #4 succeeded at 778 with fuzz 1 (offset -454 lines).
Hunk #5 succeeded at 798 (offset -454 lines).
Hunk #6 succeeded at 909 (offset -454 lines).
Hunk #7 succeeded at 1882 (offset -464 lines).
Hunk #8 succeeded at 2492 (offset -469 lines).
Hunk #9 succeeded at 4255 with fuzz 2 (offset -553 lines).
Hunk #10 succeeded at 4383 with fuzz 2 (offset -602 lines).
Hunk #11 FAILED at 4466.
2 out of 11 hunks FAILED -- saving rejects to file orinoco.c.rej
patching file orinoco.h
Hunk #1 succeeded at 110 (offset -30 lines).
patching file prism2header.h

And when i put in the second patch line:
sam@portos:/orinoco/orinoco-0.15rc4$ sudo patch -p1 < orinoco-0.15rc2-dragorn-02.diff
patching file orinoco.c
Hunk #1 FAILED at 447.
Hunk #2 succeeded at 415 with fuzz 2 (offset -95 lines).
Hunk #3 succeeded at 721 with fuzz 1 (offset -455 lines).
Hunk #4 succeeded at 778 with fuzz 1 (offset -454 lines).
Hunk #5 succeeded at 798 (offset -454 lines).
Hunk #6 succeeded at 909 (offset -454 lines).
Hunk #7 succeeded at 1882 (offset -464 lines).
Hunk #8 succeeded at 2492 (offset -469 lines).
Hunk #9 succeeded at 4255 with fuzz 2 (offset -553 lines).
Hunk #10 succeeded at 4383 with fuzz 2 (offset -602 lines).
Hunk #11 FAILED at 4466.
2 out of 11 hunks FAILED -- saving rejects to file orinoco.c.rej
patching file orinoco.h
Hunk #1 succeeded at 110 (offset -30 lines).
patching file prism2header.h

When i make i get:
sam@portos:/orinoco/orinoco-0.15rc4$ sudo make
make -C /usr/src/linux-headers-2.6.12-10-386 M=/orinoco/orinoco-0.15rc4 KERNELRELEASE=2.6.12-10-386 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco_nortel.o
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco_pci.o
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco_plx.o
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco_tmd.o
  CC [M]  /orinoco/orinoco-0.15rc4/hermes.o
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco.o
/orinoco/orinoco-0.15rc4/orinoco.c: In function `orinoco_rx_monitor':
/orinoco/orinoco-0.15rc4/orinoco.c:724: error: storage size of 'hdr' isn't known/orinoco/orinoco-0.15rc4/orinoco.c:724: warning: unused variable `hdr'
/orinoco/orinoco-0.15rc4/orinoco.c: At top level:
/orinoco/orinoco-0.15rc4/orinoco.c:4258: warning: 'orinoco_ioctl_setprism2header' defined but not used
/orinoco/orinoco-0.15rc4/orinoco.c:4292: warning: 'orinoco_ioctl_setfcsbytes' defined but not used
make[2]: *** [/orinoco/orinoco-0.15rc4/orinoco.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2
sam@portos:/orinoco/orinoco-0.15rc4$ sudo make install
make -C /usr/src/linux-headers-2.6.12-10-386 M=/orinoco/orinoco-0.15rc4 KERNELRELEASE=2.6.12-10-386 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /orinoco/orinoco-0.15rc4/orinoco.o
/orinoco/orinoco-0.15rc4/orinoco.c: In function `orinoco_rx_monitor':
/orinoco/orinoco-0.15rc4/orinoco.c:724: error: storage size of 'hdr' isn't known/orinoco/orinoco-0.15rc4/orinoco.c:724: warning: unused variable `hdr'
/orinoco/orinoco-0.15rc4/orinoco.c: At top level:
/orinoco/orinoco-0.15rc4/orinoco.c:4258: warning: 'orinoco_ioctl_setprism2header' defined but not used
/orinoco/orinoco-0.15rc4/orinoco.c:4292: warning: 'orinoco_ioctl_setfcsbytes' defined but not used
make[2]: *** [/orinoco/orinoco-0.15rc4/orinoco.o] Error 1
make[1]: *** [_module_/orinoco/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2

HAHA! never saw that comin! (j.k)
sam@portos:/orinoco/orinoco-0.15rc4$ sudo iwconfig eth0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Invalid argument.

So, there's got to be something super stupid i'm not doing or not noticing.... when i start from a clean install, i do have to download the linux source (apt-get install linux-source-2.6.12) to make this procedure work..... am i doing something wronge somewhere else? do i have to have the card deactivated to do this?

please help. i just spent alot of money (with my income at least) on this card and i really need it to work.
thanks,
Sam

---

### Post by anubix on 2006-05-06
Anyone???
I'm really stuck!
please help.

---

### Post by uberpinguin on 2006-07-24
Are you using the CVS drivers?  The orinoco project moved to SVN a couple of months ago, and all the new (functional!) code is stored at svn.sourceforge.net.  So to get the shiny new stuff: ```
svn co https://svn.sourceforge.net/svnroot/orinoco orinoco 
```  This new driver has monitor mode in it, but it is disabled by default - it doesn't work with all firmwares; so you don't need the dragorn patch.  To force-enable monitor mode for all firmwares, modify line 116 in orinoco.c (or whatever line nearby that resembles 'static int force_monitor /* = 0 */; ) to read: ```
static int force_monitor = 1;
```Note that this won't work with all firmwares!  I have a Compaq W200 Multiport with the Agere/Orinoco chipset (I don't know the firmware revision - if someone knows how to discover this let me know!), and it's not usable in monitor mode.

---

