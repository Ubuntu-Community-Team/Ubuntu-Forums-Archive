---
title: "Low resolution in framebuffer"
date: 2010-05-01
forum: General Help
---

### Post by miromiro on 2010-05-01
My grub menu (I dual boot with another Linux OS) displays at the correct 1680x1050 but then when Plymouth starts, it reverts to a much lower resolution. I don't particularly care about the splash screen, but if I switch to TTY1-6, the low resolution (800x600?) means that I only get about a dozen lines on the screen.

I have had this problem since 7.10, but thanks to [this helpful post]("http://newyork.ubuntuforums.org/showpost.php?p=8632103&postcount=8") I solved it in 9.10 - only to have it reappear now.

Details: Nvidia 9600GT using the nouveau driver. /etc/default/grub:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="ro quiet splash vga=0x0369"
#GRUB_CMDLINE_LINUX="gfxpayload=true"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1680x1050x24

```

My understanding of KMS was that it would take care of the framebuffer resolution - is there any way to make that happen?

---

### Post by BrokeMahPC on 2010-05-01
Sorry can't help with Nvidia - I'm an ATI man but did notice:
#GRUB_CMDLINE_LINUX="gfxpayload=true"
If you want that to work you need to remove the #.

GRUB_GFXMODE=1680x1050x24
Do you really need to set the colour bit depth? if so, what does the following do?
GRUB_GFXMODE=1680x1050x32

---

### Post by miromiro on 2010-05-01
Thanks BrokeMahPC,

I commented out the payload line to see if that made any difference (it didn't). I'll reinstate and reboot just to confirm though.

I set the bit depth after running hwinfo; I'll see if 32 makes a difference.

---

### Post by miromiro on 2010-05-01
32 bit depth doesn't have any effect.

I also removed "vga=0x0369" from the grub line as I understand this is deprecated in KMS. That had no impact either...

---

### Post by BrokeMahPC on 2010-05-01
Other one to try is from the plymouth readme
Try the last 2 lines of code - it forces the higher resolution into the framebuffer earlier in the boot:

Changing Themes
---------------

Plymouth themes are installed into sub-directories of /lib/plymouth/themes,
some themes may require plugins installed (as .so files) into /lib/plymouth.

Search the archive for packages named plymouth-theme-*

To change the current theme:

  sudo update-alternatives --config default.plymouth
  sudo update-initramfs -u

To restore the default theme:

  sudo update-alternatives --auto default.plymouth
  sudo update-initramfs -u


Disabling the splash screen
---------------------------

There are two methods to disable the splash screen.  Both have the
same effect.  Your boot will show such messages as are emitted by
the starting services, and will still be able to prompt if needs be.

 1) Remove all of the plymouth-theme-* packages from your system,
    including the text ones.  Plymouth will remain installed to
    permit boot-time prompts.

 2) Remove "splash" from the kernel command-line.  You can do this
    per-boot, or make it permanent by changing the
    GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub


High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

    For nVidia and ATI users, the default "nouveau" and "radeon"
    drivers are Kernel Mode Setting enabled, but do not always
    provide 3D capability at the current time.  By switching to
    using the restricted/non-free nvidia-glx or fglrx drivers,
    you will gain 3D capability at the loss of a high-color
    splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 ```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```
```
 sudo update-initramfs -u
```

---

### Post by miromiro on 2010-05-01
Thanks for the additional pointer BrokeMahPC - but, apart from a slightly changed splash, the framebuffer is still very low resolution...

---

### Post by miromiro on 2010-05-02
This is a hack, but it works. In /etc/default/grub remove 'splash' from the default line and add a new line:
```

GRUB_GFXPAYLOAD_LINUX=1680x1050
```

You don't get any fancy splash screen - which is fine by me, but you **do** get a nice, crisp widescreen frambuffer to work in.

My full grub file looks like this:
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"

GRUB_GFXMODE=1680x1050x24

# Hack to force higher framebuffer resolution
GRUB_GFXPAYLOAD_LINUX=1680x1050 
```

This is still a hack as switching between X and the framebuffer (TTY1-6) is still quite slow, whereas under KMS working properly it should be virtually instantaneous...

I found this stuff [in this post]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/"). Hope it helps others...

---

### Post by dino99 on 2010-05-02
> **miromiro said:**
> This is a hack, but it works. In /etc/default/grub remove 'splash' from the default line and add a new line:
```

GRUB_GFXPAYLOAD_LINUX=1680x1050
```

You don't get any fancy splash screen - which is fine by me, but you **do** get a nice, crisp widescreen frambuffer to work in.

My full grub file looks like this:
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"

GRUB_GFXMODE=1680x1050x24

# Hack to force higher framebuffer resolution
GRUB_GFXPAYLOAD_LINUX=1680x1050 
```

This is still a hack as switching between X and the framebuffer (TTY1-6) is still quite slow, whereas under KMS working properly it should be virtually instantaneous...

I found this stuff [in this post]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/"). Hope it helps others...

yeah, someone need to report this bug about grub-pc on launchpad

---

### Post by BrokeMahPC on 2010-05-02
Only other thing I can think of is that you are conflicting with KMS in some way - try and get grub and anything that interferes with the boot process back to the default. They are making the kernel responsible for setting everything and editing grub or your xorg.conf can conflict. Xorg.conf is now largely redundant.
If KMS is off or suffers a conflict it seems to = low res splash in Plymouth.

EG - I was trying to get dynamic power management to work - typed radeon.dynpm=0 in the grub boot. That does not work with the current kernel and KMS - result was low resolution Plymouth.

The FGLRX driver causes a bad effect as it does not work with KMS - not sure about the effects of different nvidia drivers tho.

That Grub hack above looks interesting!  not seen that one yet.

---

### Post by darmok47 on 2010-09-25
hi,
i have the same problem, tried almost everything with original drivers from ATI... and nothing! Sometimes ubuntu doesn't start neither and i have to fix the problem from previous kernel in the grub.

now i'm trying with UVESAFB and after the subsequent changes in etc/default/grub
...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap"
...
GRUB_GFXMODE=1440x900

and etc/initramfs-tools/modules
...
uvesafb mode_option=1440x900-24 mtrr=3 scroll=ywrap

and in etc/initramfs-tools/conf.d/splash
framebuffer=y

and off course after update
sudo update-grub2
sudo update-initramfs -u

the situation is unchanged. I think the problem is that framebuffer see the wrong resolution for my monitor (acer p223W) that is a 16:10 instead of 4:3 monitor, but framebuffer as only 4:3 res

hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.eq_W9lnvNEF
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  RV770"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "RV770"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 24 bits
  Mode 0x0383: 1792x1344 (+1792), 8 bits
  Mode 0x0385: 1792x1344 (+3584), 16 bits
  Mode 0x0386: 1792x1344 (+7168), 24 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 24 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

i'm getting really frustated now. Someone can help me, perhaps telling me how tell to framebuffer that i have a 16:10 screen?

p.s. now my tty is a 1600x1200 resolution, that is over res of my monitor

i have set 1440x900 but is still at 1600x1200 and dmesg return this

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=368b3ab9-c35e-4b4e-95e3-838973ed2d63 ro splash quiet quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=368b3ab9-c35e-4b4e-95e3-838973ed2d63 ro splash quiet quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap
[    0.526441] uvesafb: (C) 1988-2005, ATI Technologies Inc. , RV770, 01.00, OEM: ATI ATOMBIOS, VBE v3.0
[    0.533005] uvesafb: VBIOS/hardware supports DDC2 transfers
[    0.578089] uvesafb: monitor limits: vf = 77 Hz, hf = 84 kHz, clk = 170 MHz
[    0.578154] uvesafb: scrolling: redraw
[    0.579577] uvesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011100000, using 16384k, total 16384k
[   13.246118] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   13.626910] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   13.863722] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   14.118597] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   14.363813] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   35.787891] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   36.304396] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.

please help me or i go crazy

---

### Post by mvs1207 on 2010-10-14
I think your card is not capable of 1440x900 resolution in framebuffer mode.  The output from "hwinfo --framebuffer" does not list 1440x900.  You may want to choose a resolution from the list.  May be 1400x1050x24.  I am assuming you already have installed "v86d".

Hope this helps

---

### Post by kc8hr on 2010-12-03
I have the reverse problem to the original poster: My virtual screen resolution is ridiculously high, and the font is so small as to be almost unreadable.

Here is /etc/default/grub:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

# GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


I am running Maverick on a Dell, 2.6GHz Intel with an onboard Intel i915 video adapter.

How can I get a reasonable virtual terminal screen resolution?

Thanks,
Tim

---

### Post by miromiro on 2010-12-03
And your monitor's resolution is?

---

### Post by kc8hr on 2010-12-03
> **miromiro said:**
> And your monitor's resolution is?

The normal graphical desktop is set to 1024x768. I do not know how to find the virtual console screen resolution.

On installation, the desktop resolution was set to 1400x1050--far to high for my eyes--but that is easily changed in Gnome.

However, that has no effect upon the virtual consoles/terminals (<ctrl-alt-F1 to F6>)

Thanks,
Tim

---

### Post by miromiro on 2010-12-03
You could try using:
```

GRUB_CMDLINE_LINUX="gfxpayload=true"
GRUB_GFXMODE=1024x768x24
GRUB_GFXPAYLOAD_LINUX=1024x768

```

---

### Post by kc8hr on 2010-12-03
> **miromiro said:**
> You could try using:
```

GRUB_CMDLINE_LINUX="gfxpayload=true"
GRUB_GFXMODE=1024x768x24
GRUB_GFXPAYLOAD_LINUX=1024x768

```

Tried that still no joy.

Spotted an interesting line in dmesg:

```
fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
```

I think there is a problem with the i915 driver. What do you think?

Thanks,
Tim

---

### Post by miromiro on 2010-12-03
Probably not:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/609044](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/609044)

I think your best bet is, if you haven't already, use vbeinfo to determine what resolutions your card supports, and then try applying those...

---

### Post by pluxon on 2010-12-05
Hey, I've got the very same problem. After installing the driver for my card I had no splash screeen, only a purple screen with some dots on the top edge, also no display for tty console. (My display is 1680x1050 and my video card is ATI HD3850 1Gb)
I've found this that helped me: [http://www.namanb.com/2010/05/changing-bootup-resolution-plymouth-in-ubuntu-10-04-lucid-lynx.html](http://www.namanb.com/2010/05/changing-bootup-resolution-plymouth-in-ubuntu-10-04-lucid-lynx.html)
When I se up the configuration with the native resolution of my display it says "out of range".
```
sudo hwinfo --framebuffer
``` 
displays :
```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.tMTgUOhmAoF
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  RV670"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "RV670"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 24 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 24 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
I don't have the 1680x1050 option so I set it up to 1400x1050 and VGA 0x0346. This is the grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX="splash vga=0x0346"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1400x1050

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"
```

So basically I've went with a lower res to get the damn thing working.
I don't know if I can add a line with my favorite res to framebuffer. (I'm kinda of a noob here:p)

---

### Post by kc8hr on 2010-12-05
> **pluxon said:**
> Hey, I've got the very same problem. After installing the driver for my card I had no splash screeen, only a purple screen with some dots on the top edge, also no display for tty console. (My display is 1680x1050 and my video card is ATI HD3850 1Gb)
I've found this that helped me: [http://www.namanb.com/2010/05/changing-bootup-resolution-plymouth-in-ubuntu-10-04-lucid-lynx.html](http://www.namanb.com/2010/05/changing-bootup-resolution-plymouth-in-ubuntu-10-04-lucid-lynx.html)
When I se up the configuration with the native resolution of my display it says "out of range".
```
sudo hwinfo --framebuffer
``` 
displays :
```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.tMTgUOhmAoF
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  RV670"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "RV670"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 24 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 24 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
I don't have the 1680x1050 option so I set it up to 1400x1050 and VGA 0x0346. This is the grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX="splash vga=0x0346"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1400x1050

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"
```

So basically I've went with a lower res to get the damn thing working.
I don't know if I can add a line with my favorite res to framebuffer. (I'm kinda of a noob here:p)

Tried that, too--again, it didn't work.

I have searched Google, followed dozens of links, and still nothing seems to work. I installed fbset, which reports the following:

```
root@dojo ~> fbset

mode "1600x1200"
    geometry 1600 1200 1600 1200 32
    timings 0 0 0 0 0 0 0
    rgba 8/16,8/8,8/0,0/0
endmode
```
It is possible to set the framebuffer resolution with this command, but it is only temporary.

I wonder where in the boot process the default framebuffer mode is set, anyway?

---

### Post by dcstar on 2010-12-06
> **kc8hr said:**
> 
.........
I wonder where in the boot process the default framebuffer mode is set, anyway?

Try adding this to **/etc/default/grub** and then do a **sudo update-grub**:

```
GRUB_GFXPAYLOAD_LINUX=1600x1200
```

FYI I gave up on trying to get Grub to behave in this way, so I have now installed **Burg** and all of this works as it should (and it is much better than standard Grub).

---

### Post by kc8hr on 2010-12-06
> **dcstar said:**
> Try adding this to **/etc/default/grub** and then do a **sudo update-grub**:

```
GRUB_GFXPAYLOAD_LINUX=1600x1200
```

FYI I gave up on trying to get Grub to behave in this way, so I have now installed **Burg** and all of this works as it should (and it is much better than standard Grub).

Thanks, but STILL nothing--the same ridiculously high screen resolution--1600x1200. Let me explain again: I want a resolution of no higher than 1024x768. Any higher, and I cannot read the screen.

BTW, I tried Burg, but it worked no better than grub2.

Thanks,
Tim

---

### Post by kc8hr on 2010-12-09
> **kc8hr said:**
> Thanks, but STILL nothing--the same ridiculously high screen resolution--1600x1200. Let me explain again: I want a resolution of no higher than 1024x768. Any higher, and I cannot read the screen.

BTW, I tried Burg, but it worked no better than grub2.

Thanks,
Tim
Well, guys--I give up.

No matter how hard I try, I cannot get the correct screen resolution in my virtual terminals/consoles. I believe that, in some part of the boot process, something decided during installation that my default screen resolution should be 1600x1200, and there seems to be no way to change it.

Guess I'd better learn to live with it. This isn't how Linux is supposed to be--we should have choices.

Thanks,
Tim

---

### Post by kc8hr on 2011-02-07
Hi Guys,

All fixed--the magic words are:

GRUB_CMDLINE_LINUX="video=VGA-1:640x480"

I found the solution here [http://lkml.indiana.edu/hypermail/linux/kernel/1001.2/01874.html]("http://lkml.indiana.edu/hypermail/linux/kernel/1001.2/01874.html")

---

