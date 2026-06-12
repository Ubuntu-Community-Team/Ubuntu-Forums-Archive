---
title: "Another alsa-related audio problem... not working"
date: 2011-05-06
forum: General Help
---

### Post by 3 frags left on 2011-05-06
Hello, I've followed the proper instructions from this thread:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I did all it was told, yet when I tried to compile the driver the following error appeared: (last lines of the "make" process)
```
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,   
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:      
 &#9474; /usr/src/modules/alsa-driver/include/linux/pci_ids.h:2:58: fatal error:     
 &#9474; @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: Arquivo ou diretório não    
 &#9474; encontrado                                                                  
 &#9474; compilation terminated.                                                     
 &#9474; make[5]: ** [/usr/src/modules/alsa-driver/acore/memalloc.o] Erro 1          
 &#9474; make[4]: ** [/usr/src/modules/alsa-driver/acore] Erro 2                     
 &#9474; make[3]: ** [_module_/usr/src/modules/alsa-driver] Erro 2                   
 &#9474; make[3]: Saindo do diretório `/usr/src/linux-headers-2.6.38-8-generic'      
 &#9474; make[2]: ** [compile] Erro 2                                                
 &#9474; make[2]: Saindo do diretório `/usr/src/modules/alsa-driver'                 
 &#9474; make[1]: ** [build-stamp] Erro 2                                            
 &#9474; make[1]: Saindo do diretório `/usr/src/modules/alsa-driver'                 
 &#9474; make: ** [kdist_image] Erro 2     
```

In case you need more info, here is the *lspci* result on the audio driver;
```
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

```
as well as lshw info:
```
  *-multimedia UNCLAIMED  
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dc440000-dc443fff

```

It worked till yesterday, when it stopped working. I don't know what else to do, if I cannot solve this I'll have to reinstall Xubuntu. Anyone?

---

### Post by 3 frags left on 2011-05-06
Sorry for the bump, but it's kinda urgent.

---

### Post by kumoshk on 2012-02-22
I was having a problem with just my microphone, at first. I installed a bunch of OSS stuff and uninstalled it. Then it all stopped working (before the uninstall, but it continued to not work after), similar to yours.

Here's my output of sudo lshw -C multimedia

```

*-multimedia UNCLAIMED  
       description: Audio device
       product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
       resources: memory:c0000000-c0003fff
```

It acts like my soundcard isn't set up with a driver or something. Any idea how to associate it?

I'm running 64-bit Xubuntu with the other windows managers installed, too. It doesn't recognize sound on any of them.

---

### Post by kumoshk on 2012-02-22
I fixed my sound. My microphone still doesn't work, though.

Here's my output, now:

```
 *-multimedia            
       description: Audio device
       product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:20 memory:c0000000-c0003fff
```

I don't know what fixed it, but here's what I did:

* Installed the following packages: Linux, linux-headers-lbm-3.0.0-12-generic, linux-backports-modules-headers-oneiric-generic, linux-headers-lbm-3.0.0-12-generic, linux-base, linux-image, linux-libc-dev, linux-generic, linux-headers-generic, linux-headers-3.0.0-16, linux-headers-3.0.0-12, linux-image-generic, linux-headers-3.0.0-16-generic and maybe a few other things like that)
* Uninstalled all my alsa stuff (including config files). These are dependencies for such as Kubuntu-desktop, Ubuntu-desktop and all that (so, they're not selected anymore. Installed alsa-base_1.0.24+dfsg-0ubuntu2_all.deb and alsa-utils_1.0.24.2-0ubuntu8_amd64.deb from the deb files with gdebi (not from synaptic or apt-get). Then I reinstalled all my -desktop things (since I have Edubuntu, KDE, Gnome, Xfce and Lxde). These reinstalled the rest of the sound files.
* Uninstalled ia32-libs
* Restarted my computer (didn't work before a restart)

So, now I'm back to where I was after a fresh install. Sound works, but my microphone doesn't.

---

### Post by kumoshk on 2012-02-22
Here's more system information.

Here's how it was before my sound stopped working:
[http://www.alsa-project.org/db/?f=1760d31ed41173a10f4d60d7d374d7a647e4a267](http://www.alsa-project.org/db/?f=1760d31ed41173a10f4d60d7d374d7a647e4a267)

Here's how it is now (after it stopped working and I fixed it):
[http://www.alsa-project.org/db/?f=d4b18bcddd9b13ffb01e2c9f37ac4abec5602580](http://www.alsa-project.org/db/?f=d4b18bcddd9b13ffb01e2c9f37ac4abec5602580)

There are a few differences&#8212;mostly with the modules loaded and a few things are enabled that weren't before. But, it acts the same. Well, I guess my headphones work normally now. Before, sound would still come out of the speakers, and the headphones. Now, it just comes out of the headphones.

I can actually adjust my microphone volume, now, at least. It still doesn't work, though.

---

