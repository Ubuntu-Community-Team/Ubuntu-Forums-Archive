---
title: "Cant Enable Desktop Effects even With Update NVidia Drivers"
date: 2010-06-04
forum: General Help
---

### Post by dewey_daniels on 2010-06-04
Well the Screenie explains most of it.I  had trouble update my drivers but i finally did but now I cant use my compiz effects like I did Before I enabled the drivers. Any Help

---

### Post by cryptotheslow on 2010-06-04
Can you open a Terminal (Applications > Accessories > Terminal) and copy/paste back the results of these two commands?

lspci

lsmod

---

### Post by dewey_daniels on 2010-06-04
here is every hting that was in the terminal


> derek@derek-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 06f1 (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
derek@derek-laptop:~$ 
proof of thought that Ubuntu hasnt detected the Geforce 105m gpu and instead the Mobo GPU


Here is the other
> derek@derek-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   278890  1 
joydev                 11072  0 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
arc4                    1473  2 
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
iwlagn                121577  0 
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  317872  0 
iwlcore               124955  1 iwlagn
uvcvideo               62403  0 
fbcon                  39270  72 
tileblit                2487  1 fbcon
drm_kms_helper         30742  1 i915
mac80211              238128  2 iwlagn,iwlcore
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
psmouse                64608  0 
serio_raw               4918  0 
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198770  2 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
atl1c                  32975  0 
asus_laptop            20584  0 
cfg80211              148386  3 iwlagn,iwlcore,mac80211
nvidia              10799466  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
led_class               3732  2 iwlcore,asus_laptop
soundcore               8052  1 snd
intel_agp              29225  2 i915
video                  20623  1 i915
output                  2503  1 video
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   37646  2 
derek@derek-laptop:~$ 


---

### Post by llawwehttam on 2010-06-04
I guess you have a laptop with the 105m in it and also an intel intergrated graphics chip. I have the same thing. 

Go into the laptop bios and set the graphics to nvidia only instead of hybrid and then install the nvidia drivers from the nvidia site ( download these to your home folder) by pressing

Ctrl+alt+f1, log in, type ```
sudo service gdm stop
```,

 (presuming that the nvidia drivers are in your home folder type: ```
sh nvidiadrivername
``` and it should guide you through it. When you are done type```
 sudo reboot
```.

After you have pressed ctrl+ alt+f1 your gui will disappear until you've finished so print these instructions off first.

EDIT: the nvidia download site is dead atm so you may have to wait until later.

---

### Post by dewey_daniels on 2010-06-04
Thank you. But do i download the drivers first then do the rest

---

### Post by llawwehttam on 2010-06-04
> **dewey_daniels said:**
> Thank you. But do i download the drivers first then do the rest


sorry, yes. Download them to your home folder, not your downloads folder and it should make it easier.

Also when you get to 
sudo sh nvidiadrivername
you can just type sh space then the first two characters of the installer and press the tab key and it should show the entire name and save you typing it out.......... unless you rename the installer to something like nvidia.

---

### Post by llawwehttam on 2010-06-04
oh and you may want to disable the nvidia drivers you are currently running.

---

### Post by dewey_daniels on 2010-06-04
Sorry to keep bothereing you but i dont want to mess this up. 
1 Can you point me to a download link sense NVidia doesn't want to.
2 For this is the name of the download drivers?
sh nvidiadrivername

---

### Post by llawwehttam on 2010-06-04
> **dewey_daniels said:**
> Sorry to keep bothereing you but i dont want to mess this up. 
1 Can you point me to a download link sense NVidia doesn't want to.
2 For this is the name of the download drivers?
sh nvidiadrivername

1, I can't get onto the nvidia download site at the moment. Wait a few minutes and I will try to get the files for you via ftp.

2. Not sure what you mean. For me the nviia driver is named: NVIDIA-Linux-x86_64-190.53-pkg2.run

so If I want to install it I would type:

sudo sh NVIDIA-Linux-x86_64-190.53-pkg2.run

or I could rename NVIDIA-Linux-x86_64-190.53-pkg2.run to "nvidia" and then just type sudo sh nvidia.


Just before I get drivers for you are you running 32 or 64 bit ubuntu?

---

### Post by dewey_daniels on 2010-06-04
Okay that answered it.

 I think I am downloading the right one

[http://www.nvidia.com/object/linux-display-amd64-195.36.24.html](http://www.nvidia.com/object/linux-display-amd64-195.36.24.html) sense I am 64bit

---

### Post by llawwehttam on 2010-06-04
looks like the right one. If you have any questions just ask.

---

### Post by dewey_daniels on 2010-06-04
Yea thanks for all the help yu have no idea how awesome you are.

BB in 5

---

### Post by dewey_daniels on 2010-06-04
For some reason it wont let get to the command thing and there are just some random colored pixels on top so I am going to do a fresh install to see if that does anyhting.

---

### Post by cryptotheslow on 2010-06-04
Don't forget to make the BIOS change suggested further up before you do.

---

### Post by dewey_daniels on 2010-06-04
Well I am just back to square one.I did a clean install of 10.04 and a clean download of the drivers.I did all the steps in the installation but at around 30% I got this error. > Pre-Install script failed. Continue Anyway.So i just pressed yes and it kept going. Then >  Would you like to install the 32x Open GL Librarys I thought it was odd sense I thought i downloaded the 64 bit one but i just said yes.Then an even longer error came up and at the end it send something like "which is usaully cause by the installing of 32bit drivers" or somehting like that.Now when i try to start up the ubuntu logo starts up with these greens dots all around the words and logo. Then the screen goes black and it says something about the video drivers and the error is (EE) No Display attached. So then it gives me some options about modes and terminals.So i just go into safe mode and now I am here. Also how did you disable your MOBO GPU.I thought I did but I dont know. There is no graphics section or anything. 

Ps Do I need to blacklist Noveau or not (If so how sense I forgot)?

---

### Post by dewey_daniels on 2010-06-04
Also it still says that there are resticted drivers.
Was I supposed to download this file [http://www.nvidia.com/object/linux_display_ia64_1.0-5336](http://www.nvidia.com/object/linux_display_ia64_1.0-5336) or the other one.

---

### Post by dewey_daniels on 2010-06-04
bump

---

### Post by llawwehttam on 2010-06-04
Sorry I haven't replied, I went out for a while.

It will always say that there are restricted drivers available but I ignore them as the nvidia drivers tend to be more stable than the ubuntu ones.

Once you've installed the nvidia drivers have you tried ```
nvidia-xconfig
```?

oh and yes it is normal to install the x32 libraries.

EDIT: the drivers you linked don't seem to be the right ones. If your email can cope with larger files pm me your email address and I will send you the stable drivers I use.

---

### Post by dewey_daniels on 2010-06-04
Also every were i look they say there is no way to disable hybrid graphics

---

### Post by llawwehttam on 2010-06-04
If you haven't disabled hybrid graphics then the rest of my steps WILL NOT WORK!!

Usually you go into the BIOS using F2 or DEL and you will find somewhere in there an option labeled graphics mode, you need to change it from hybrid or intel hybrid to Nvidia.

If you don't do this the drivers WILL NOT WORK.

It is in my BIOS otherwise I wouldn't have been able to do this.

I am currently emailing you the drivers but it could take a while as my email server is being sluggish.

---

### Post by llawwehttam on 2010-06-04
Per your pm asking how to flash your BIOS.......Don't.

You shouldn't need to and it usually causes more problems that its worth.

Could you tell me what BIOS you have and what version. ( should be at the top of the BIOS screen)

---

### Post by dewey_daniels on 2010-06-04
Well this what i think you want.

AMIBIOS 
Version: 204
VGA Version: 1676.I12UX5.004
EC Version: 2020160001
Also when I first thought i disabled the one GPU I just Disabled the "Intel Virtualization Tech" I don't know if it has anything to do with it or not but hey. There is also the Intel VT-D.No clue what it does but by what Intel sense it  sounds kind of complicated.

---

### Post by dewey_daniels on 2010-06-04
I may have mistaken some words. How I update my bios not flash them

---

### Post by llawwehttam on 2010-06-04
I don't know why you want to update your bios, you shouldn't need to and it usually requires either a windows environment or a DOS based environment off a floppy disk.

For disabling the hybrid graphics this is what I see in my bios. I would assume you have something similar:

[IMG]http://www.legitreviews.com/images/reviews/708/hybrid_bios_settings.jpg[/IMG]

---

### Post by dewey_daniels on 2010-06-04
Ill check everything but I didnt see anything like that.

---

### Post by dewey_daniels on 2010-06-04
This is all I have for the advanced tab.The other tabs dont even hint to graphics. On the main it is only date and time that is accesible.The next is the one with the picture. 3rd is passwords for bios and hard drives. 4 is just the boot order and the order for booting cd drives and hard drives. 5 is just to save and exit.

---

### Post by llawwehttam on 2010-06-04
Sadly after a lot of googling this seems to be a problem with most ami bios's. 

Someone else may be able to help you from here but BIOS's are not my area. I have a pheonixBIOS and that has a hidden area that can be accessed vy a key combo, (not sure if ami bios has the same thing)

 Sorry I can't help more.

---

### Post by dewey_daniels on 2010-06-04
What is the key combo that you use?

---

### Post by llawwehttam on 2010-06-04
Sorry mate, I use a customized (unlocked ) BIOS. The key combo for it is Ctrl+alt+I once in the BIOS.

---

