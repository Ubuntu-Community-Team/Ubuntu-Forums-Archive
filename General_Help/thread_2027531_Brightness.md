---
title: "Brightness"
date: 2012-07-16
forum: General Help
---

### Post by kurci2 on 2012-07-16
Hi everyone!
I have a problem with Kubuntu 12.04
Brightness control doesn't work at all. I am waiting and searching for a fix for the last two months but nothing...

Fn+F6/F7 keys doesn't work and also that slider in power manager does nothing.

Does anyone have same problem, because i really like kde and dont want to switch...

Just for information: I have Toshiba a660 laptop with Nvidia m330 graphic card and i also have nvidia drivers installed.

Please help! =)

---

### Post by Redblade20XX on 2012-07-16
Try pushing this boot parameter:
```
acpi_backlight=vendor
```

See here on how to actually do it:
[http://askubuntu.com/questions/19486/how-do-i-add-a-boot-parameter](http://askubuntu.com/questions/19486/how-do-i-add-a-boot-parameter)

Post what happens afterwards!

- Red

---

### Post by kurci2 on 2012-07-17
Well, i have already done that, but nothing happened.
Everything remained just the same.

---

### Post by kurci2 on 2012-07-17
i have just discovered something really weird today.
I found that tutorial: [http://askubuntu.com/questions/57236/unable-to-change-brightness-in-a-lenovo-laptop/57610#57610](http://askubuntu.com/questions/57236/unable-to-change-brightness-in-a-lenovo-laptop/57610#57610)

And when i run command: ```
ls /sys/class/backlight/*/brightness
``` i get two options: ```
/sys/class/backlight/acpi_video0/brightness
/sys/class/backlight/toshiba/brightness
```
Now, if i use command for example: ```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
``` it changes my brightness, but if i use ```
echo 5 | sudo tee /sys/class/backlight/toshiba/brightness
``` nothing happens. Max value is 7.

So now i thing that my system uses wrong command... Is this possible?

---

### Post by sideshowAnthony on 2012-07-17
I had this problem with my Fujitsu Esprimo V6555 laptop, with nvidia graphics, and Ubuntu 12.04.

The solution was (and in detail for newbies reading this):

Press Ctrl + Alt + T to open the terminal

Type this to copy this file to your desktop as a safety measure
```
cp /etc/rc.local ~/Desktop/rc.local
```Type this to edit the original file using gedit (is it gkedit on Kubuntu? I dunno).
```
sudo gedit /etc/rc.local
```If you are asked for a password, enter the password of the root user.

When the editor opens add this line before 'exit 0'
```
echo 7 > /sys/class/backlight/acpi_video0/brightness
```'7' is the brightness level. Save and close this file.

Now reboot your laptop.



If this causes problems, you can always undo the change by copying the file back:
```
 sudo cp ~/Desktop/rc.local /etc/rc.local
``` If you are asked for a password, enter the password of the root user.


Source: [http://media3000.co.uk/2012/06/fujitsu-esprimo-and-ubuntu-12/](http://media3000.co.uk/2012/06/fujitsu-esprimo-and-ubuntu-12/)

---

### Post by kurci2 on 2012-07-17
well that made no difference.
But i discovered that when change brightness using keyboard od power manager, it changes value in /sys/class/backlight/toshiba/brightness but as i sad nothing happens on computer.

So if i could make my computer to use acpi_video0 everything would work (i suppose...)

---

### Post by Cheesemill on 2012-07-17
> **sideshowAnthony said:**
> Type this to edit the original file using gedit (is it gkedit on Kubuntu? I dunno).
```
sudo gedit /etc/rc.local
```If you are asked for a password, enter the password of the root user.[]("http://media3000.co.uk/2012/06/fujitsu-esprimo-and-ubuntu-12/")
Don't use sudo. You should always use gksudo for graphical applications.
Also the password you are asked for is your user password, there isn't a root password in Ubuntu.

---

### Post by kurci2 on 2012-07-17
yes, i know that. but it does not help...
but don't forget that i have this problem on Kubuntu 12.04 (Ubuntu 12.04 works fine, i tried)
so command is: ```
gksudo kate /etc/rc.local
```
i think...

---

### Post by kurci2 on 2012-07-17
I think the question is if it is possible to remove that "toshiba" folder in /sys/class/backlight/ and use acpi_video0 instead...

---

### Post by kurci2 on 2012-07-17
i discovered also this:
Ubuntu 12.04 uses acpi_video0 to control brigtness
Kubuntu 12.04 uses toshiba in /sys/class/backlight/ to control brightness

In Ubuntu everything works, but in Kubuntu it does NOT.

How could i change Kubuntu to use acpi_video0??

---

### Post by Redblade20XX on 2012-07-17
> **kurci2 said:**
> i discovered also this:
Ubuntu 12.04 uses acpi_video0 to control brigtness
Kubuntu 12.04 uses toshiba in /sys/class/backlight/ to control brightness

In Ubuntu everything works, but in Kubuntu it does NOT.

How could i change Kubuntu to use acpi_video0??

Maybe you can symbolic link the acpi_video0 to the toshiba file.

Must be in the /sys/class/backlight/ directory,

```
ln -s toshiba acpi_video0
```- Red

---

### Post by kurci2 on 2012-07-17
I have don what you suggested, but it is all the same...

---

### Post by kurci2 on 2012-07-17
well, there is surely a way to fix this issue...
i am just wondering who knows the fix :popcorn:

---

### Post by kurci2 on 2012-07-17
bump

---

### Post by Cheesemill on 2012-07-17
Please wait 24 hours before bumping your thread.

---

### Post by Redblade20XX on 2012-07-17
> **kurci2 said:**
> bump

Try these two boot parameters:
```
acpi_osi=Linux acpi_backlight=vendor
```- Red

---

### Post by Toz on 2012-07-17
In addition to the above, also post back the results of:
```
lsmod
```
...maybe if we blacklisted the toshiba video module...

And since you have an nvidia card, you could try:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...in /usr/share/X11/xorg.conf.d:
```
# /usr/share/X11/xorg.conf.d/20-nvidia.conf 
Section "Device"
        Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

---

### Post by kurci2 on 2012-07-18
I have tride what was suggested and here are the results:

1.Adding ```
acpi_osi=Linux acpi_backlight=vendor
``` in /etc/default/grub did nothing

2. The second suggestion: ```
# /usr/share/X11/xorg.conf.d/20-nvidia.conf 
Section "Device"
        Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
``` broke my computer and it didn't boot anymore. I had to remove the file...

3. Here is the output of lsmod:```
marko@ToShiba:~$ lsmod
Module                  Size  Used by
joydev                 17693  0
snd_hda_codec_hdmi     32474  4
parport_pc             32866  0
rfcomm                 47604  16
bnep                   18281  2
ppdev                  17113  0
snd_hda_codec_realtek   223867  1
snd_hda_intel          33773  5
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
psmouse                87692  0
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
rc_rc6_mce             12502  0
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              12319264  42
toshiba_acpi           18582  0
serio_raw              13211  0
sparse_keymap          13890  1 toshiba_acpi
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
btusb                  18288  2
bluetooth             180104  23 rfcomm,bnep,btusb
lib80211_crypt_tkip    17390  0
wl                   2568210  0
uvcvideo               72627  0
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
ir_lirc_codec          12859  0
lirc_dev               19204  1 ir_lirc_codec
ir_mce_kbd_decoder     12777  0
ir_sony_decoder        12510  0
ir_jvc_decoder         12507  0
ir_rc6_decoder         12507  0
jmb38x_ms              17646  0
ir_rc5_decoder         12507  0
memstick               16569  1 jmb38x_ms
lib80211               14381  2 lib80211_crypt_tkip,wl
ir_nec_decoder         12507  0
intel_ips              18089  0
ene_ir                 18457  0
rc_core                26412  10 rc_rc6_mce,ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ene_ir
mei                    41616  0
wmi                    19256  1 toshiba_acpi
toshiba_bluetooth      12807  0
mac_hid                13253  0
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1
sdhci_pci              18826  0
sdhci                  33205  1 sdhci_pci
r8169                  62099  0
video                  19596  0
marko@ToShiba:~$

```

Well i also think that idea about blaklisting "toshiba" would be great =)

---

### Post by Toz on 2012-07-18
Do you have an /etc/X11/xorg.conf file? If so, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device section there instead.

As for blacklisting the module, can you also post back the results of the following commands:
```
modinfo toshiba_acpi
modinfo uvcvideo
modinfo videodev 
modinfo v4l2_compat_ioctl32 
modinfo video
```

---

### Post by kurci2 on 2012-07-18
i have added this line ```
Option "RegistryDwords" "EnableBrightnessControl=1"
```, but it doesn't help.
So I just hope it is possible to blacklist toshiba, so system would use acpi_video0

Outputs:
```
marko@ToShiba:~$ modinfo toshiba_acpi
filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/platform/x86/toshiba_acpi.ko
license:        GPL
description:    Toshiba Laptop ACPI Extras Driver
author:         John Belmonte
srcversion:     512C27DCE3EAE790E566A94
alias:          acpi*:TOS1900:*
alias:          acpi*:TOS6208:*
alias:          acpi*:TOS6200:*
depends:        wmi,sparse-keymap
intree:         Y
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
marko@ToShiba:~$ 

```
```
marko@ToShiba:~$ modinfo uvcvideo
filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
version:        1.1.1
license:        GPL
description:    USB Video Class driver
author:         Laurent Pinchart <laurent.pinchart@ideasonboard.com>
srcversion:     447D142EA57EFAAC38234E3
alias:          usb:v*p*d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v1C4Fp3000d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v1B3Bp2951d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d00*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d01[0-1]*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d012[0-6]dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v199Ep8102d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v18ECp3290d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18ECp3288d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18ECp3188d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18CDpCAFEd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v1871p0306d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v17EFp480Bd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v17DCp0202d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A34d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A33d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A31d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A12d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp5931d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp5212d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v152Dp0310d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v13D3p5103d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0E8Dp0004d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0AC8p3420d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0AC8p3410d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0AC8p332Dd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v06F8p300Cd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v05E3p0505d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v05C8p0403d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v05ACp8501d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v058Fp3820d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v04F2pB071d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v046Dp08C7d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C6d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C5d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C3d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C2d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C1d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v045Ep0723d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v045Ep00F8d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0458p706Ed*dc*dsc*dp*ic0Eisc01ip00*
depends:        videodev
intree:         Y
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           clock:Video buffers timestamp clock
parm:           nodrop:Don't drop incomplete frames (uint)
parm:           quirks:Forced device quirks (uint)
parm:           trace:Trace level bitmask (uint)
parm:           timeout:Streaming control requests timeout (uint)
marko@ToShiba:~$ 

```
```
marko@ToShiba:~$ modinfo videodev 
filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/videodev.ko
alias:          char-major-81-*
license:        GPL
description:    Device registrar for Video4Linux drivers v2
author:         Alan Cox, Mauro Carvalho Chehab <mchehab@infradead.org>
srcversion:     711C5DF28C34C226FE1EF67
depends:        v4l2-compat-ioctl32
intree:         Y
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
marko@ToShiba:~$ 

```
```
marko@ToShiba:~$ modinfo v4l2_compat_ioctl32 
filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko
license:        GPL
srcversion:     7C3B7F7853A1E59DF92C1C3
depends:        
intree:         Y
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
marko@ToShiba:~$ 

```
```
marko@ToShiba:~$ modinfo video
filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/acpi/video.ko
license:        GPL
description:    ACPI Video Driver
author:         Bruno Ducrot
srcversion:     2154B010E258883188737B6
alias:          acpi*:LNXVIDEO:*
depends:        
intree:         Y
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           brightness_switch_enabled:bool
parm:           brightness_autoswitch_via_bios:bool
parm:           allow_duplicates:bool
parm:           use_bios_initial_backlight:bool
marko@ToShiba:~$ 

```
Hope it helps =)

---

### Post by Toz on 2012-07-18
I'm tempted to suggest blacklisting the toshiba_acpi module, but I'm worried about what other negative effects it might have (function keys, fans, battery, etc). Plus I'm not sure if it will remove the toshiba interface.

Have you tried the combination of **acpi_backlight=vendor** and **Option "RegistryDwords" "EnableBrightnessControl=1"**?

And a bit of a long shot - bios update?

---

### Post by kurci2 on 2012-07-19
Now, my /etc/default/grub file look like this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
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
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
an my /etc/X11/xorg.conf like this:
```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
	Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

```
I have restarted my computer and run sudo update-grub, but my brightness still doesn't work...
And my BIOS is updated to the latest version.

I am wondering why Ubuntu uses acpi_video0 and Kubuntu uses toshiba... If only i could make Kubuntu to use acpi_video0

---

### Post by Toz on 2012-07-19
> **kurci2 said:**
> 
I am wondering why Ubuntu uses acpi_video0 and Kubuntu uses toshiba... If only i could make Kubuntu to use acpi_video0

Sorry but I don't use KDE. After some brief googling, it looks like powerdevil controls the backlight interface in KDE. Maybe there is an issue with powerdevil?

---

### Post by kurci2 on 2012-07-19
Well, this might be the last thing i tried which might help

I have tried Linux Mint 12 KDE and everything worked there. Even in /sys/class/backlight was only folder acpi_video0 and no toshiba.
So it is Kubuntu problem, not KDE...
Or maybe it is the difference between KDE 4.7 and KDE 4.8?

---

### Post by kurci2 on 2012-07-19
More information.
I have tried Linux Mint 13 KDE RC with KDE 4.8 and guess what: brightness DOES NOT work and folder toshiba IS present

So my conclusion: It is issue with KDE 4.8, so i can just gor back to Ubuntu and wait for fix =) (i guess...)

Edit:
Yes, it is KDE 4.8 issue.
I have updated KDE on Kubuntu 12.04 to 4.8.90 and brightness works there. And KDE uses acpi_video0 =)
So i guess that i will just use that version of KDE =)

---

