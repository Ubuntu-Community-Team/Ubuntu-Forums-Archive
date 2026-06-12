---
title: "Wireless adapter won't reinitialize after suspend"
date: 2012-03-12
forum: General Help
---

### Post by brandon89 on 2012-03-12
Hey guys, so my wireless adapter won't turn back on after I resume from a suspend.  I have to manually unplug it/plug it back in for Ubuntu to recognize it.  Is there anyway to force Ubuntu to turn on the adapter or something along those lines?

I'm running Ubuntu 11.10 64-bit and this is the wireless adapter
[http://www.rosewill.com/products/1721/ProductDetail_Specifications.htm](http://www.rosewill.com/products/1721/ProductDetail_Specifications.htm)

Thanks for any help!

---

### Post by varunendra on 2012-03-14
Please post the outputs of:
```
lsusb
lsmod
```

I think we are going to do this: [http://ubuntuforums.org/showthread.php?p=11759385](http://ubuntuforums.org/showthread.php?p=11759385)

---

### Post by brandon89 on 2012-03-15
Output of lsusb:
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 046d:c03f Logitech, Inc. M-BT85 [UltraX Optical Mouse]
Bus 002 Device 004: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 002 Device 005: ID 046d:09a2 Logitech, Inc. QuickCam Communicate Deluxe/S7500
Bus 002 Device 006: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 001 Device 003: ID 05ac:1293 Apple, Inc. iPod Touch 2.Gen


Output of lsmod:
> Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
vesafb                 13809  1 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32040  1 
r8712u                189049  0 
snd_usb_audio         118122  1 
uvcvideo               72711  0 
snd_usbmidi_lib        25371  1 snd_usb_audio
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
usbhid                 47198  0 
hid                    95463  1 usbhid
ppdev                  17113  0 
snd_hda_codec_realtek   330815  1 
snd_hda_intel          33390  5 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96714  5 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
fglrx                2928969  139 
serio_raw              13166  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36962  1 
snd                    68266  23 snd_hda_codec_hdmi,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
xhci_hcd               82820  0 
atl1c                  41643  0 


---

### Post by varunendra on 2012-03-15
Let's try this first:
```
sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module 
gksu gedit /etc/pm/config.d/00sleep_module
```
The first two commands will create a file "00sleep_module" and make it executable. The third one will open it as root for editing.
Now add this line to the file:
```
SUSPEND_MODULES="$SUSPEND_MODULES r8712u"
```
Just copy-paste above line to avoid mistakes, save and close the file. Now try suspend/resuming the computer to see it the problem is gone or not.

---

### Post by brandon89 on 2012-03-15
Awesome!  I believe that worked!  What exactly does the file do?  Thanks so much

---

### Post by SystemsGO on 2012-03-15
> **varunendra said:**
> Let's try this first:
```
sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module 
gksu gedit /etc/pm/config.d/00sleep_module
```
The first two commands will create a file "00sleep_module" and make it executable. The third one will open it as root for editing.
Now add this line to the file:
```
SUSPEND_MODULES="$SUSPEND_MODULES r8712u"
```
Just copy-paste above line to avoid mistakes, save and close the file. Now try suspend/resuming the computer to see it the problem is gone or not.

Will this work for the NWA3100 adapter? I finally got mine working, and it works quite well on Ubuntu 11.10 64, it's just that once I restart it no longer works.

---

### Post by varunendra on 2012-03-15
> **brandon89 said:**
> Awesome!  I believe that worked!  What exactly does the file do?  Thanks so much
There are certain modules that cause problems with suspend/hibernate <-> resume cycle due to power management bugs in them. That file is a simple power management hack that tells the kernel to unload the r8712u module before going to sleep, then reload it after resuming. If required, other problematic modules can also be added to that line in the file to unload them before going to sleep/hibernate. An example is:
```
SUSPEND_MODULES="r8712u usbhid hid"
```As you can see in above example, there is no "$SUSPEND_MODULES" entry within the double-quotes. In your file, it was just there to make sure that if the file already existed (some drivers may do that for you) and already contained some entry in it, the "$SUSPEND_MODULES" entry would simply append those existing value(s) to the module(s) you are manually adding (in a new line).
[COLOR=DarkRed]*[Note: That is my guess based on my limited knowledge about what $ does in scripting, I may be incorrect in explaining what that '$' entry exactly does]*[/COLOR]

Some useful info about Power-Management and "pm-utils": [https://wiki.archlinux.org/index.php/Pm-utils](https://wiki.archlinux.org/index.php/Pm-utils)


@*SystemsGO*,
Looking at [this thread]("http://ubuntuforums.org/showthread.php?p=11769088"), I think you've already got your problem solved by adding **ndiswrapper** to **/etc/modules** file. If not, an easier way to do that is simply run this code in terminal:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```However, the guide that *jerome1232* linked to in the above linked post gives some more useful info for those who are using methods other than nm-applet to configure the network.

**PS:** By the way, *SystemsGO, *the pm-utils hack couldn't have worked for you, since yours is an entirely different problem.

---

