---
title: "Mounting /tmp as tmpfs causing segfaults in wine"
date: 2011-10-09
forum: General Help
---

### Post by J V on 2011-10-09
The following entry in my fstab is responsible for segfaults in wine.

```
# /tmp as tmpfs
#tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0
```

When I boot with /tmp normally (as in when I have the line commented out) wine works fine.

If I boot with the line uncommented (Which is a requirement to stop encrypted data leaking to disc when I set it up) wine throws a bunch of errors followed by a segfault and a wine error dialogue to do with "RtlpWaitForCriticalSection"

Something in wine or ubuntu is messing with memory in such a way as to stop my program from running, anyone know what?

---

### Post by matt_symes on 2011-10-09
Hi

Not quite sure what is going wrong on your system

Take a look at this....

```
matthew@matthew-laptop:~$ mount | grep /tmp
matthew@matthew-laptop:~$ sudo mount -t tmpfs -o size=1000M,mode=1777 tmpfs /tmp
matthew@matthew-laptop:~$ mount | grep /tmp
tmpfs on /tmp type tmpfs (rw,size=1000M,mode=1777)
matthew@matthew-laptop:~$ wine notepad
matthew@matthew-laptop:~$ wine --version
wine-1.3.28
matthew@matthew-laptop:~$ uname -a
Linux matthew-laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
matthew@matthew-laptop:~$ 
```

Notepad ran correctly.

Kind regards

---

### Post by J V on 2011-10-09
Using mount command manually as you did worked fine, but if it's in fstab as put above it won't work. Perhaps should I have specifically set the size rather than leaving it at the default half of total ram?

---

### Post by matt_symes on 2011-10-09
Hi

> **J V said:**
> Using mount command manually as you did worked fine, but if it's in fstab as put above it won't work. Perhaps should I have specifically set the size rather than leaving it at the default half of total ram?

Yes...

Try setting up a size for the filesystem. It is quite possible that is the reason why it is segfaulting when using the default.

Out of interest, what is the program you are running in wine ?

Kind regards

---

### Post by J V on 2011-10-09
Guild wars, but it didn't even get to the launcher/updater never mind the main deal. Looked like it segfaulted just trying to start wine (But winecfg worked and it output an error message so it got just past that)

---

### Post by matt_symes on 2011-10-09
Hi

What version os wine are you using ? What version of Ubuntu ?

I will add you fstab line to my fstab and see how i get on.

Kind regards

---

### Post by matt_symes on 2011-10-09
Hi

I added it to fstab and ran notepad with no problems. 

It may well be a issue with not enough memory. That is just speculation though as i don't own guildwars.

Take a look at this.

```
matthew@matthew-laptop:~$ grep "/tmp" /etc/fstab
tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0
matthew@matthew-laptop:~$ mount -a
mount: only root can do that
matthew@matthew-laptop:~$ sudo !!
sudo mount -a
matthew@matthew-laptop:~$ mount | grep /tmp
tmpfs on /tmp type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
matthew@matthew-laptop:~$ wine notepad
matthew@matthew-laptop:~$ 
```

Does Notepad through wine work for you?

Kind regards

---

### Post by J V on 2011-10-09
Mounting with a fixed size didn't work either, same error:
```
err:ntdll:RtlpWaitForCriticalSection section 0x7e41c7a0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0022, blocked by 0009, retrying (60 sec)
```With fstab: (Could encrypted swap be the problem?)
```
# swap was on /dev/sda6 during installation
#UUID=1e851c77-e02f-40b4-9931-f93ea2fdfb16 none            swap    sw          $
/dev/mapper/cryptswap1 none swap sw 0 0
# /tmp as tmpfs
tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777,size=500m 0 0
```Lucid minimal install openbox and whatnot, different versions of wine (Tried 1.3.24 and 1.3.18, same problem with both)

It worked with even less ram on debian with gnome, encryption and tmpfs /tmp, so that's not the problem.

---

### Post by matt_symes on 2011-10-09
Hi

```
x11drv_critsection wait timed out
```

Isn't this an xorg problem ?

What version of Ubuntu are you using ? What version of xorg ?
What version of Debian where you using ? What version of xorg under debian ?

```
matthew@matthew-laptop:~$ Xorg -version

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux matthew-laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-34-generic root=UUID=dffbd026-c151-45c6-9c94-c6625200f01b ro quiet splash
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
matthew@matthew-laptop:~$ 
```

I don't understand why it should work when /tmp is on the hard drive and not in memory.

Can you increase the memory set aside for the game to run even more ? 

Run it with /tmp on the hard drive and find out how large the temporary file space is it using and compare it to the amount of memory you have set aside for it when mounted in memory. That would be something i would check.

Kind regards

---

### Post by J V on 2011-10-09
```
$ Xorg -version
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux jonux 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=27dda285-4081-4719-b12d-da66c4cdbc33 ro quiet splash
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

$ df -h | grep tmp
tmpfs                1004M   68K 1004M   1% /tmp

$ free -m # You will note below that minus firefox I'm only using 150mb of 2g ram, this game ran happily when over 40% was used on debian with gnome
             total       used       free     shared    buffers     cached
Mem:          2006        760       1245          0         32        379
-/+ buffers/cache:        348       1658
Swap:         1906          0       1906

$ ps aux | grep firefox
j          587  0.0  0.0   7624   916 pts/0    R+   16:48   0:00 grep --color=auto firefox
j         3893  6.1 10.1 714064 207964 tty1    Sl   16:40   0:29 /usr/lib/firefox-7.0.1/firefox
```On lucid linx, 1.850m ram free. Besides, how would lack of ram result in a segfault?

Below is the **full** segfault information:```
err:ntdll:RtlpWaitForCriticalSection section 0x7e42e7a0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0022, blocked by 0009, retrying (60 sec)
wine: Unhandled page fault on write access to 0x04362c96 at address 0x400007 (thread 0022), starting debugger...
Unhandled exception: page fault on write access to 0x04362c96 in 32-bit code (0x00400007).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00400007 ESP:014ddad4 EBP:ffffffff EFLAGS:00210206(  R- --  I   - -P- )
 EAX:021b164b EBX:014ddaf4 ECX:0000000a EDX:014ddd00
 ESI:014dde18 EDI:021b0000
Stack dump:
0x014ddad4:  021b0000 014ddaf4 014ddc2c 00401a01
0x014ddae4:  fffffffe 00a2463c 014dde18 00000001
0x014ddaf4:  f576004b ffffffff 014ddb1c 505c3a43
0x014ddb04:  72676f72 46206d61 73656c69 6975475c
0x014ddb14:  5720646c 00737261 652e7747 00006578
0x014ddb24:  00000000 00000000 00000000 30303063
Backtrace:
0x00400007: addb    %al,0x0(%eax,%eax,1)
Modules:
Module    Address            Debug info    Name (95 modules)
PE      400000-  fb2000    Export          gw
ELF    7b800000-7b8f0000    Deferred        kernel32<elf>
  \-PE    7b810000-7b8f0000    \               kernel32
ELF    7bc00000-7bcc0000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc0000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7e180000-7e1b3000    Deferred        uxtheme<elf>
  \-PE    7e190000-7e1b3000    \               uxtheme
ELF    7e1b3000-7e1bd000    Deferred        libxcursor.so.1
ELF    7e1bd000-7e1cb000    Deferred        libxi.so.6
ELF    7e1cb000-7e1d1000    Deferred        libxfixes.so.3
ELF    7e1d1000-7e1d5000    Deferred        libxcomposite.so.1
ELF    7e1d5000-7e1dd000    Deferred        libxrandr.so.2
ELF    7e1dd000-7e1e7000    Deferred        libxrender.so.1
ELF    7e1e7000-7e1ed000    Deferred        libxxf86vm.so.1
ELF    7e1ed000-7e20e000    Deferred        imm32<elf>
  \-PE    7e1f0000-7e20e000    \               imm32
ELF    7e20e000-7e228000    Deferred        libxcb.so.1
ELF    7e228000-7e345000    Deferred        libx11.so.6
ELF    7e345000-7e355000    Deferred        libxext.so.6
ELF    7e355000-7e36e000    Deferred        libice.so.6
ELF    7e38a000-7e433000    Deferred        winex11<elf>
  \-PE    7e3a0000-7e433000    \               winex11
ELF    7e455000-7e47c000    Deferred        libexpat.so.1
ELF    7e47c000-7e4ac000    Deferred        libfontconfig.so.1
ELF    7e4ac000-7e4c1000    Deferred        libz.so.1
ELF    7e4c1000-7e537000    Deferred        libfreetype.so.6
ELF    7e537000-7e56e000    Deferred        libncurses.so.5
ELF    7e570000-7e576000    Deferred        libxdmcp.so.6
ELF    7e576000-7e57b000    Deferred        libuuid.so.1
ELF    7e57b000-7e584000    Deferred        libsm.so.6
ELF    7e58a000-7e5b0000    Deferred        msacm32<elf>
  \-PE    7e590000-7e5b0000    \               msacm32
ELF    7e5b0000-7e5ee000    Deferred        winmm<elf>
  \-PE    7e5c0000-7e5ee000    \               winmm
ELF    7e5ee000-7e6de000    Deferred        oleaut32<elf>
  \-PE    7e610000-7e6de000    \               oleaut32
ELF    7e6de000-7e754000    Deferred        rpcrt4<elf>
  \-PE    7e6f0000-7e754000    \               rpcrt4
ELF    7e754000-7e858000    Deferred        ole32<elf>
  \-PE    7e770000-7e858000    \               ole32
ELF    7e858000-7e944000    Deferred        comctl32<elf>
  \-PE    7e860000-7e944000    \               comctl32
ELF    7e944000-7e9ab000    Deferred        shlwapi<elf>
  \-PE    7e950000-7e9ab000    \               shlwapi
ELF    7e9ab000-7eb72000    Deferred        shell32<elf>
  \-PE    7e9c0000-7eb72000    \               shell32
ELF    7eb72000-7ec10000    Deferred        gdi32<elf>
  \-PE    7eb80000-7ec10000    \               gdi32
ELF    7ec10000-7ed46000    Deferred        user32<elf>
  \-PE    7ec20000-7ed46000    \               user32
ELF    7ed46000-7eda5000    Deferred        advapi32<elf>
  \-PE    7ed50000-7eda5000    \               advapi32
ELF    7eda5000-7edb9000    Deferred        libresolv.so.2
ELF    7edb9000-7edbd000    Deferred        libxinerama.so.1
ELF    7edbd000-7edd5000    Deferred        version<elf>
  \-PE    7edc0000-7edd5000    \               version
ELF    7edd5000-7edf5000    Deferred        iphlpapi<elf>
  \-PE    7ede0000-7edf5000    \               iphlpapi
ELF    7edf5000-7ee24000    Deferred        ws2_32<elf>
  \-PE    7ee00000-7ee24000    \               ws2_32
ELF    7ee24000-7ee3e000    Deferred        wsock32<elf>
  \-PE    7ee30000-7ee3e000    \               wsock32
ELF    7ef9b000-7efa7000    Deferred        libnss_files.so.2
ELF    7efa7000-7efbe000    Deferred        libnsl.so.1
ELF    7efbe000-7efe4000    Deferred        libm.so.6
ELF    7efe4000-7efe8000    Deferred        libxau.so.6
ELF    f5074000-f5100000    Deferred        msvcrt<elf>
  \-PE    f5090000-f5100000    \               msvcrt
ELF    f52ee000-f5349000    Deferred        dbghelp<elf>
  \-PE    f5300000-f5349000    \               dbghelp
ELF    f5349000-f5368000    Deferred        libgcc_s.so.1
ELF    f5747000-f575a000    Deferred        psapi<elf>
  \-PE    f5750000-f575a000    \               psapi
ELF    f575a000-f5773000    Deferred        imagehlp<elf>
  \-PE    f5760000-f5773000    \               imagehlp
ELF    f5773000-f57a4000    Deferred        d3d8<elf>
  \-PE    f5780000-f57a4000    \               d3d8
ELF    f5892000-f71a3000    Deferred        libnvidia-glcore.so.280.13
ELF    f71a3000-f7275000    Deferred        libgl.so.1
ELF    f727f000-f7285000    Deferred        libnss_dns.so.2
ELF    f7291000-f73c9000    Deferred        wined3d<elf>
  \-PE    f72a0000-f73c9000    \               wined3d
ELF    f73c9000-f7400000    Deferred        d3d9<elf>
  \-PE    f73d0000-f7400000    \               d3d9
ELF    f7403000-f740d000    Deferred        libnss_nis.so.2
ELF    f740e000-f7412000    Deferred        libdl.so.2
ELF    f7412000-f756c000    Deferred        libc.so.6
ELF    f756c000-f7585000    Deferred        libpthread.so.0
ELF    f7588000-f7590000    Deferred        libnss_compat.so.2
ELF    f7593000-f759c000    Deferred        librt.so.1
ELF    f759c000-f759f000    Deferred        libnvidia-tls.so.280.13
ELF    f75a2000-f76e3000    Dwarf           libwine.so.1
ELF    f76e5000-f7703000    Deferred        ld-linux.so.2
ELF    f7703000-f7704000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Guild Wars\Gw.exe
    00000031    0
    00000024    0
    00000023    0
    00000022    0 <==
    00000021    0
    00000020    2
    00000009    0
0000000e services.exe
    0000001b    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000016    0
    00000013    0
    00000012    0
00000018 plugplay.exe
    0000001f    0
    0000001a    0
    00000019    0
0000001c explorer.exe
    0000001d    0
Backtrace:
```I tried using a simpler fstab entry: ```
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0

```No dice. This is all the useful information I can think of.

---

### Post by J V on 2011-10-09
This is no longer limited to wine, xscreensaver showed that child process (The screensaver in question) was terminated by signal 11, a quick google and? Segmentation fault

I'm going back to my earlier supposition (Supported by [bug reports](http://bugs.winehq.org/show_bug.cgi?id=19025)) that this is a kernel problem, has anyone heard of this?

---

### Post by matt_symes on 2011-10-09
Hi

> I'm going back to my earlier supposition that this is a kernel problem, has anyone heard of this?You could well be right if you are seeing this outside of wine.

That may also explain why is seems to work on my laptop if my kernel is different.

I will spend the next couple of hours running with an in memory tmpfs and see if i can replicate it.

> Besides, how would lack of ram result in a segfault?

I understand this, however it is a ram issue so i discounted nothing. Knowing that it is happening to you outside of wine with an in memory /tmp would tend to point to something else.

Kind regards

---

### Post by J V on 2011-10-09
I'm installing 2.6.38-11 as that's the newest version in the repositories, I installed the video driver manually, I guess I'll see if I need to do that again won't I?...

Edit: Yep, kernel problem. I now have a brand new kernel and a brand new nvidia driver and wine is starting properly, screensaver working normally with tmpfs up and running. Something went wrong with sound but we're getting there... (Fixed it, just conky being a pain)

---

