---
title: "Help getting Wacom Intuos 2 working again"
date: 2012-07-06
forum: General Help
---

### Post by LADmaticCA on 2012-07-06
My Wacom tablet recently stopped working with precise 64 bit. It worked fine for weeks since this new install. I believe I had problems even before the recent kernel update.

The wacom module loads in the lsmod:

```
Module                  Size  Used by
des_generic            21415  0 
md4                    12595  0 
vesafb                 13844  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
nls_utf8               12557  4 
cifs                  287317  8 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  4 
nvidia              12319264  40 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
usbhid                 47199  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
hid                    99559  1 usbhid
psmouse                87692  0 
sp5100_tco             13791  0 
snd_timer              29990  2 snd_pcm,snd_seq
edac_core              53746  0 
i2c_piix4              13301  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
edac_mce_amd           23709  0 
k10temp                13166  0 
fam15h_power           13115  0 
mxm_wmi                12979  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 mxm_wmi
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
wacom                  48145  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
atl1c                  41717  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13204  0 
```

But there's no device using it...it seems. The gnome wacom utility sees the device, but I cannot configure buttons.

Yesterday I tried the wacom-dkms from a ppa and after rebooting the tablet was working. But today once again, it has stopped. Anyone have any other ideas? 

Oh and it works fine in Windows.

---

### Post by Favux on 2012-07-06
Hi LADmaticCA,

What PPA did you use?  Did you check how recent the wacom.ko it installs was?  Likely the one native to your Precise kernel is newer.  You may actually want to uninstall that PPA.

Have you tried plugging it into another usb port?  If it is in a hub try plugging it in directly.  Does it start working if you hotplug?  Boot with it plugged?

What is the output of running the following command in a terminal?
```
xinput list
```

---

### Post by LADmaticCA on 2012-07-06
Thanks for replying.

I tried this ppa: [https://launchpad.net/~lekensteyn/+archive/wacom-tablet](https://launchpad.net/~lekensteyn/+archive/wacom-tablet)

It actually made my wacom work after reboot. But since restarting again it has stopped. 

I have tried different usb ports and it is plugged directly into the motherboard. It usually stays plugged into my computer so I'm not sure if it'll hotplug.

xinput list output:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 6x8 stylus                	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Digital Media Pro Keyboard	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 6x8 eraser                	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 6x8 cursor                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Digital Media Pro Keyboard	id=10	[slave  keyboard (3)]
```

I appreciate any help you can offer.

---

### Post by Favux on 2012-07-06
OK, Lekenstyn keeps his PPA pretty up to date, it has input-wacom-0.13.0.  But there shouldn't be anything in that wacom.ko that would make a difference to your tablet.  That I'm aware of anyway.

So this might be tricky, given it is an ittermittent problem.  That's why I thought of hardware.  But since it works in Windows that doesn't seem very likely.

Alright xinput is seeing the tablet.  Let's check if the Wacom X driver is.  What's the output of the following command run in a terminal?
```
xsetwacom list
```
It seems to me there was another usb Intuos2 with problems in the last month or three.  I'll see if I can find that thread.

---

### Post by LADmaticCA on 2012-07-06
```
xsetwacom list
Wacom Intuos2 6x8 stylus        	id: 11	type: STYLUS    
Wacom Intuos2 6x8 eraser        	id: 12	type: ERASER    
Wacom Intuos2 6x8 cursor        	id: 13	type: CURSOR
```

Yeah this is an odd one. I removed the ppa and wacom-dkms just to see if it'd make any difference, nope still the same.

---

### Post by Favux on 2012-07-06
Good removing the PPA/dkms removes a variable which we don't need right now.

Well it looks like the Wacom driver recognizes the tablet too.

Right now the problem looks to be with your stylus.  Do you have a Wacom tablet puck/mouse?  Does it work or did it stop working?  Can you boot into Windows right now a verify your stylus works?  Or do you have another compatible stylus to test with?

---

### Post by LADmaticCA on 2012-07-07
Alright back from Windows stylus works fine. Check this out...I'm writing from my Ubuntu live usb and the tablet works perfect.:???: Same one I used to do the install.

---

### Post by Favux on 2012-07-07
That is just weird.

What we probably need to do then is to look at your Xorg.0.log from /var/log when it is working and when it isn't.  Hope that tells us something useful.  If you can capture the tablet's Xorg.0.log in both states right click on them and compress them (they're big) and attach them to your next post.

---

### Post by LADmaticCA on 2012-07-07
There I have attached them. The working one is from the Live CD/USB where it's using basic vesa drivers. The non-working one is from a re-install (yes I tried a re-install) but the issue remains. 

On the fresh install pre-updates/extras the wacom works. But after updating and adding other software it breaks again.

This section is interesting from the "not working" file

```
 6.448] (**) Wacom Intuos2 6x8: Applying InputClass "evdev tablet catchall"
[     6.449] (**) Wacom Intuos2 6x8: Applying InputClass "Wacom class"
[     6.449] (II) Using input driver 'wacom' for 'Wacom Intuos2 6x8'
[     6.449] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[     6.449] (**) Wacom Intuos2 6x8: always reports core events
[     6.449] (**) Option "Device" "/dev/input/event12"
[     6.449] (WW) Wacom Intuos2 6x8: device file already in use by stylus. Ignoring.
[     6.449] (EE) PreInit returned 8 for "Wacom Intuos2 6x8"
[     6.449] (II) UnloadModule: "wacom"
[     6.449] (II) Unloading wacom
[     6.449] (II) config/udev: Adding input device Wacom Intuos2 6x8 (/dev/input/mouse0)
[     6.449] (II) No input driver specified, ignoring this device.
[     6.449] (II) This device may have been added with another device file.
```

---

### Post by Favux on 2012-07-07
That's interesting in that you seem to have confirmed the updates break it.  That kind of leans me to thinking this might be a Ubuntu specific problem.  In which case we aren't likely to get much help from the Linux Wacom Project developers on linuxwacom-discuss.  Their attitude is Distro bugs are the Distro's problem.

I'll look at them.  I'm not too worried yet about evdev looking at /dev/input/mouse0.  That's a spurious event the kernel throws up.  Although I'm not sure we should be seeing that.  The 50-wacom.conf runs after the 10-evdev.conf and what runs last controlls.

You don't have a tablet mouse, correct?

The other thing is we should consider running evtest for the stylus:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Evtest](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Evtest)  If that output seemed normal that would tell us the hardware is working correctly as well as the usb communication with it.  And the problem is elsewhere.

---

### Post by LADmaticCA on 2012-07-07
Hey I have found a work around! The isssue seems to be with the start-up or initial load of the module. 

If I blacklist the wacom driver by adding it to my /etc/modprobe.d/blacklist.conf and manually probe it after start-up:
```

sudo modprobe wacom
```

It works everytime!:p 

So I guess I have to add a startup script or something for it to perform this automatically.

---

### Post by Favux on 2012-07-07
Hey, outstanding find!  :)

OK.  A couple of things to try.  With it blacklisted add **wacom** to the bottom of the modules file in etc/, i.e. /etc/modules.  See if maybe it is a delay that is needed.

Another thing to try is after you modprobe wacom.ko to a working state run:
```
sudo depmod -a
```
Maybe one of the updates screwed up the module dependencies.

By any chance did you install a PPA that had a wacom.ko dkms at some point in your updating?

---

### Post by LADmaticCA on 2012-07-07
Okay. I tried adding wacom to the bottom of /etc/modules with it blacklisted, but the tablet wasn't functional on boot.

I ran depmod -a after manually probing the wacom module, but it still wasn't function on boot.

Since re-installing last night I haven't added any ppa's.

I guess I still have to make a start-up script of some kind. Thanks again for all your help! 

At least I have something that works. Maybe this thread will help someone in the future.

---

### Post by Favux on 2012-07-07
Alright.  Thanks for trying.

Sure wish we had a handle on why things were working this way.  Obviously something ain't right.  If you think of something let me know.

One thing I should mention.  The Intuos and Cintiq's are the professional or Protocol 5 models.  What that means is their input tools have serial numbers.  That allows you to configure each stylus or airbrush etc. differently.  And they also have other fancy features like Tilt.  Consumer grade tablets (Protocol 4) don't have serial numbers associated with their input tools.

What the non-working Xorg.0.log seemed to be saying is something went wrong with the cursor's (the puck or mouse) serial number and xf86-input-wacom was no longer seeing a valid one.  At least that's what I got from the repeating error message.

---

