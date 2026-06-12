---
title: "Webcam not working in Ubuntu 11.10"
date: 2012-02-18
forum: General Help
---

### Post by thestraniero on 2012-02-18
Hi,
I am new to Ubuntu, but like it a lot except for the fact that the built-in webcam on my Compaq CQ10-700SE is not working. I have followed all the fixes for laptops with webcam problems that I've found on the forums, but nothing has worked. Programs like "Cheese" do see the camera as /dev/video0, but the camera light never goes on and I get no image from it. Everything in Skype works, but I transmit no picture. Any help would be much appreciated! Thanks!

---

### Post by thestraniero on 2012-02-18
I found something interesting... I tried sudo apt-get install v4l2ucp then ran sudo v4l2ucp and the camera started working in Cheese. So, I quit programs and tried it again, but it wont work anymore. When I open v4l2ucp it says unable to open /dev/video0 but I kow that's where it is. Strange thing though... Cheese is sometimes saying /dev/video1 and sometimes /dev/video0 either way though it's not working. Please help me somebody!

---

### Post by thestraniero on 2012-02-18
So, my camera worked for all of two seconds... now when I run 
ls /dev/video*

in the terminal it says /dev/video1 in yellow text and everytime I try to run Video4Linux Control Panels it says /dev/video0 doesn't exist. This program only worked the one time for two seconds. Did it change my configuration?

---

### Post by thestraniero on 2012-02-19
How come 138 people have seen this, but nobody's got any help to offer? Am I posting in the wrong place or something? Please help!

---

### Post by koftis on 2012-02-19
if you want you can check my video in youtube **[Fix Skype webCam Problem, Ubuntu 11.10, Greek-Eng]("http://www.youtube.com/watch?v=WeaLCzB4qy8&feature=plcp&context=C3816860UDOEgsToPDskLIdMQ2avzzNiimv9IqIDhc")**

---

### Post by thestraniero on 2012-02-21
Koftis, thanks for responding! It didn't work though! I did everything just like the video but when I test video devices in Skype it says "No devices Found on /dev/video0".

I think that your solution might have worked for me before I tried to use "Video4 Linux Control Panel" because before I did that the camera was showing up as /dev/video0 but now that I tried that program (which actually worked for two seconds!) the camera shows up as /dev/video1.

Any ideas how I can get my camera back to showing up as /dev/video0 again???

&#963;&#945;&#962; &#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974;!

---

### Post by thestraniero on 2012-02-24
Nobody out there wants to give a hand? I'm dyin' here...

---

### Post by matt_symes on 2012-02-24
Hi

Run Cheese from the terminal. What messages does it display in the terminal ? Are there any error messages ?

That might give a place to start debugging the problem.

Kind regards

---

### Post by thestraniero on 2012-02-27
Hi, Thanks for replying!

When I run Cheese normally it says the same thing as all the other programs I've tried... "no such device at /dev/video0". This is what I get for everything since I tried Video 4 Linux Control Panel. Before that I could see it no problem there. Now do /dev/video* it tells me that it's on /dev/video1.

Something REALLY interesting happened the other day. I accidentally started Cheese not meaning to and it was working! It worked just fine, so I said, "OK, let's turn it off and back on again to see if it still works". It didn't... in fact it's exactly as it was before. It seems to me to just some little bug somewhere, BUT WHERE?!?

I've tried every bit of advice I've been able to find on Ubuntu Forums and nothing has worked. (Who knows if I've messed it up even worse?) 

Is there some way to change the camera's location back to /dev/video0 ??

Thanks again for your help!!!!

---

### Post by thestraniero on 2012-02-27
When I started Cheese before, I didn't do it in the terminal, but I just did it and THE CAMERA SEEMS TO BE WORKING!!! I even tried it in Skype too!

I did get this error message though
(cheese:4577): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

Did opening Cheese with the terminal actually fix it, or should I consider this to be an act of God?

Thanks!

---

### Post by nothingspecial on 2012-02-27
> **thestraniero said:**
> How come 138 people have seen this, but nobody's got any help to offer? Am I posting in the wrong place or something? Please help!

Let's try here

*Thread moved to **General Help**.*

---

### Post by thestraniero on 2012-02-27
It stopped working again for no apparent reason! I didn't do anything at all!! Now the terminal says...

libv4l2: error dequeuing buf: No such device

** (cheese:5070): WARNING **: Failed trying to get video frames from device '/dev/video1'.


** (cheese:5070): WARNING **: Internal data flow error.

---

### Post by matt_symes on 2012-02-28
Hi

Maybe it's loading an incorrect driver ? Let's have a look at your system.

What's the output of (post back)

```
ls -l /dev/video*
```

(small  after ls)

```
lsmod
```

```
lsusb
```

Kind regards

---

### Post by thestraniero on 2012-02-28
I haven't done anything and it's working intermittently now. If I quit Cheese and reopen it the webcam sometimes works, most of the time not...

---

### Post by thestraniero on 2012-03-01
Hi Matt!

Here's what you asked for below. I'd just like to add that the camera has been working like 1 in 20 times that I try it without doing anything at all between tests.

Kind regards!

/dev/video1

Module                  Size  Used by
snd_seq_dummy          12686  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
snd_hrtimer            12648  1 
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
joydev                 17393  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
brcmsmac              591864  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73673  0 
snd_seq                51567  4 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
brcmutil               16885  1 brcmsmac
i915                  509519  3 
mac80211              393421  1 brcmsmac
serio_raw              12990  0 
btusb                  18160  2 
cfg80211              172427  2 brcmsmac,mac80211
bluetooth             148839  23 rfcomm,bnep,btusb
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
snd                    55902  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
drm                   192194  4 i915,drm_kms_helper
crc_ccitt              12595  1 brcmsmac
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 027: ID 05c8:021a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 005 Device 006: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR

---

### Post by matt_symes on 2012-03-02
Hi

This is your webcam.

> Bus 001 Device 027: ID 05c8:021a Cheng Uei Precision Industry Co., Ltd (Foxlink) 

It looks like it's creating a device node video1.

> /dev/video1

I think cheese looks for /dev/video0. It's strange that it works one time in 20.

This is only a hunch but keep trying to use it and on that one time in twenty it works, open a terminal and type this again.

```
ls -l /dev/video*
```

Post back the results. It maybe that when cheese works udev has created device node /dev/video0.

If it has then we can create a udev rule to ensure the device is always called /dev/video0.

Like i said, this is only a hunch and i may be wrong but it's worth a try.

Kind regards

---

### Post by thestraniero on 2012-03-04
Matt,
I'm almost sure that you are right! However there is a law of physics that states that if you need an intermittent problem to show itself for a technician it never will. I'm trying and trying to get the webcam up on Cheese (it was working for a minute yesterday!)  but I can't get it to come up. I'll keep trying. 

When the webcam does work in Cheese, it also works in Skype... (Just so you know!)

Thanks!

---

### Post by thestraniero on 2012-03-04
I got it!

crw-rw----+ 1 root video 81, 1 2012-03-04 08:27 /dev/video1

and infact the Cheese prefrences now say "HP camera (/dev/video1)" when normally it says that Cheese is set to /dev/video0.

OK, so now what do I do?

Kind regards!

---

### Post by matt_symes on 2012-03-05
Hi

> **thestraniero said:**
> I got it!

crw-rw----+ 1 root video 81, 1 2012-03-04 08:27 /dev/video1

and infact the Cheese prefrences now say "HP camera (/dev/video1)" when normally it says that Cheese is set to /dev/video0.

OK, so now what do I do?

Kind regards!

We can certainly try to create a udev rule. It may be that cheese does no always detect /dev/video1.

I need to do a small bit of research to find out where is the best place to create the rule. I have never written a rule for a webcam before.

Please bump this thread by replying to this post so it reappears in my subscribed threads list. Otherwise i will have to trawl though my subscribed threads list looking for it or perform a search.

Kind regards

---

### Post by thestraniero on 2012-03-06
Thanks man! Sounds like a good solution to me! I'm leaving for a job in Costa Rica in 8 days and it would be really nice to Skype with my daughter. Cheers!

---

### Post by thestraniero on 2012-03-06
The camera used to show up as device 0. Is there anyway to switch it back? All the other programs (Skype and Video 4 Linux Control Panel) are looking only at Video 0. 

Before I used Video 4 Linux Control Panel the webcam did always show up as Video 0, but it wasn't working.

---

### Post by thestraniero on 2012-03-07
Hey Matt, You asked me to reply to your message. I just realized that there was this quick reply button as well. Thanks for your help in getting this webcam running! Kind regards...

---

### Post by matt_symes on 2012-03-09
Hi

Sorry for the delay. I have had a busy couple of days. Let's see if we can create a rule for your webcam.

This is taken from here.

[http://tjworld.net/wiki/Linux/Ubuntu/UdevWebcamRules](http://tjworld.net/wiki/Linux/Ubuntu/UdevWebcamRules)

Open a terminal and copy and paste this code into the terminal. It will create the file /etc/udev/rules.d/70-webcam.rules.

```
echo 'SUBSYSTEM=="video4linux", BUS=="usb", SYSFS{idVendor}=="05c8", SYSFS{idProduct}=="021a", NAME="video0"' | sudo tee /etc/udev/rules.d/70-webcam.rules
```

Reboot your PC and check it's created /dev/video0. Post back on efficacy.

Kind regards

---

### Post by thestraniero on 2012-03-09
Hi Matt,Thanks for working on this with me.

Here's what happened... I pasted that text in the terminal which then responded: SUBSYSTEM=="video4linux", BUS=="usb", SYSFS{idVendor}=="05c8", SYSFS{idProduct}=="021a", NAME="video0"

I rebooted and now when I check in the terminal it says that the device is on video0.

But... now Cheese, Video 4 and Skype all are set to video0, but the camera doesn't work!

---

### Post by matt_symes on 2012-03-09
Hi

> **thestraniero said:**
> Hi Matt,Thanks for working on this with me.

Here's what happened... I pasted that text in the terminal which then responded: SUBSYSTEM=="video4linux", BUS=="usb", SYSFS{idVendor}=="05c8", SYSFS{idProduct}=="021a", NAME="video0"

I rebooted and now when I check in the terminal it says that the device is on video0.

But... now Cheese, Video 4 and Skype all are set to video0, but the camera doesn't work!

That's a real shame it did not work. It was only a hunch though. It's odd how it sometimes works. Maybe it's not loading the driver correctly. Can you post the output of

```
lsmod
```

once for when it works and once for when it doesn't. I assume this is a V4L (UVC class) webcam. I should really check.

Kind regards

---

### Post by thestraniero on 2012-03-10
Well, last night the webcam was coming on almost 1 in 2 times which probably explains why it won't come on at all this morning! I'll have to post the working results later. Here's the "not working" results below. By the way the system calls it "HP Webcam" if that helps... Thanks again!

Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
usb_storage            44173  0 
uas                    17699  0 
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31444  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55577  2 vfat,msdos
jfs                   175084  0 
xfs                   746838  0 
reiserfs              230932  0 
snd_hrtimer            12648  1 
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
joydev                 17393  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  1 
snd_seq_midi           13132  0 
videodev               85626  2 uvcvideo
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth             148839  23 rfcomm,bnep,btusb
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393421  1 brcmsmac
binfmt_misc            17292  1 
cfg80211              172427  2 brcmsmac,mac80211
snd                    55902  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  509519  4 
crc_ccitt              12595  1 brcmsmac
soundcore              12600  1 snd
drm_kms_helper         32889  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
drm                   192194  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0

---

### Post by thestraniero on 2012-03-10
This is the result while the camera was active...

Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hrtimer            12648  1 
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  2 
mac80211              393421  1 brcmsmac
uvcvideo               67271  1 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               85626  2 uvcvideo
psmouse                73673  0 
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
bluetooth             148839  23 rfcomm,bnep,btusb
serio_raw              12990  0 
binfmt_misc            17292  1 
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
i915                  509519  4 
cfg80211              172427  2 brcmsmac,mac80211
soundcore              12600  1 snd
drm_kms_helper         32889  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm                   192194  5 i915,drm_kms_helper
crc_ccitt              12595  1 brcmsmac
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0

---

### Post by matt_symes on 2012-03-10
Hi

This has got me really scratching my head. I can see nothing wrong with the loaded drivers.

Just to get more information, what's your kernel ?

```
uname -a
```

Anybody else have any ideas ?

If i get time tomorrow, i will do some research.

Kind regards

---

### Post by thestraniero on 2012-03-11
Well, I appreciate your head scratching. I don't get it either. Why does it occasionally work and other times no without doing anything at all in between trials?

Linux mark-Compaq-Mini-CQ10-600 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux

Thanks Matt!

---

### Post by thestraniero on 2012-03-11
Now it's listing two video devices...

mark@mark-Compaq-Mini-CQ10-600:~$ ls /dev/video*
/dev/video0  /dev/video1
mark@mark-Compaq-Mini-CQ10-600:~$

---

### Post by matt_symes on 2012-03-11
Hi

Open a terminal and type

```
sudo lshw
```

Post back the entire output.

Kind regards

---

### Post by andresv on 2012-03-12
I report a similar problem, with a Genius FaceCam 310.

Cheese gives the following message:


** (cheese:8231): WARNING **: Error starting streaming on device '/dev/video0'.


** (cheese:8231): WARNING **: Could not negotiate format

Now in this case, it always looks for "video0" - there is no conflict with video1.

Now, gstreamer-properties gives [COLOR="Blue"][FONT="Garamond"]"Video for Linux 2 (v4l2): Error starting streaming on device '/dev/video0'."[/FONT][/COLOR]

I believe somehow the kernel got messed up when there was an update...

Any suggestion for a solution will be welcome!

av

---

### Post by Dreamer Fithp Apprentice on 2012-03-12
I know nothing about webcams or the 'ware in question and it looks like you have some much more sophisticated people interested in this but I can't help but wondering, since if you said so I missed it:  Have you run this same hardware under some other OS before? And if so, did it work ok then? The point being, have you absolutley excluded a HARDWARE problem? If not, are you looking at a deadline on getting repair/replacement under warranty? If so, you might want to go ahead and rule that in or out expeditously. If it has worked under other software, maybe you might want to consider trying something other than what you are presently having problems with, perhaps an earlier version of Ubuntu. You could back up the present system with partition imaging of some sort so that if that didn't work you could restore it easily enough. If it did work you might want to stick with it for a few update cycles at least or maybe until 12.04 comes out and has been updated a time or two before trying that. If nothing else getting it working under some other OS entirely, such as FreeDOS, or PC-BSD, or Windows, would at least show that the problem was NOT hardware.

---

### Post by thestraniero on 2012-03-12
Hi Matt,
PCI (sysfs) 

Cheers!

---

### Post by thestraniero on 2012-03-12
[Dreamer Fithp Apprentice]("http://ubuntuforums.org/member.php?u=1435975") Yes, when I bought the computer two months ago it had Windows 7 and worked fine. It works fine in Ubuntu as welll when it works which isn't very often.

---

### Post by matt_symes on 2012-03-12
Hi

> **thestraniero said:**
> [Dreamer Fithp Apprentice]("http://ubuntuforums.org/member.php?u=1435975") Yes, when I bought the computer two months ago it had Windows 7 and worked fine. It works fine in Ubuntu as welll when it works which isn't very often.

I'm really not sure what is going on with your webcam so lets try to get as much info as possible.

I need you to run  this again

```
sudo lshw
```

Wait for it to finish. It will spit out a lot more information. What you posted shows the command was still running.

Start cheese then type  (case is important)

```
grep uvcvideo: -B2 -A5 /var/log/syslog | tail -n 20
```

Post back that and then 

```
grep cheese ~/.xsession-errors | tail -n20
``` 

and finally from the terminal

```
gstreamer-properties
```

Post back the text on the console.

Post each results section back between code tags like this

[noparse]```
results
```[/noparse]

to get output like this.

```
results
```

---

### Post by matt_symes on 2012-03-12
Hi

> **andresv said:**
> I report a similar problem, with a Genius FaceCam 310.

Cheese gives the following message:


** (cheese:8231): WARNING **: Error starting streaming on device '/dev/video0'.


** (cheese:8231): WARNING **: Could not negotiate format

Now in this case, it always looks for "video0" - there is no conflict with video1.

Now, gstreamer-properties gives [COLOR="Blue"][FONT="Garamond"]"Video for Linux 2 (v4l2): Error starting streaming on device '/dev/video0'."[/FONT][/COLOR]

I believe somehow the kernel got messed up when there was an update...

Any suggestion for a solution will be welcome!

av

I had this exact same issue with a different camera. It needed a kernel update or rollback to fix it as it the breakage was due to a kernel regression.

Are you sure that camera is supported ? I would check that and the kernel first.

Kind regards

---

### Post by thestraniero on 2012-03-13
Hi Matt,
OK, here goes... [code]
mark-compaq-mini-cq10-600 
    description: Notebook
    version: 058D10A000202400000300100
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP X=MIN sku=LD763EA#ABV uuid=04C736D6-4165-2AE4-3B46-BF19AC0BE836
  *-core
       description: Motherboard
       product: 1584
       vendor: Hewlett-Packard
       physical id: 0
       version: 85.2B
       serial: PBSZDA57V0GHWR
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.14
          date: 11/30/2010
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: SODIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: M471B2873FHS-CH9
             vendor: Samsung
             physical id: 0
             serial: 962035AE
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
          vendor: Intel Corp.
          physical id: f
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          slot: CPU
          size: 1666MHz
          capacity: 1666MHz
          width: 64 bits
          clock: 667MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm cpufreq
          configuration: cores=1 enabledcores=1 id=0 threads=2
        *-cache:0
             description: L2 cache
             physical id: 10
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 11
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:56180000-561fffff ioport:40c0(size=8) memory:40000000-4fffffff memory:56000000-560fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:56100000-5617ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:56200000-56203fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:55000000-55ffffff ioport:50000000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: cc:52:af:55:00:25
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-16-generic firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:55000000-55003fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:54000000-54ffffff ioport:51000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=4096) memory:53000000-53ffffff ioport:52000000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 05
                serial: 98:4b:e1:f3:43:d3
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:1000(size=256) memory:52004000-52004fff memory:52000000-52003fff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:4080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:4060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:56204400-562047ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: N10/ICH7 Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:40b8(size=8) ioport:40cc(size=4) ioport:40b0(size=8) ioport:40c8(size=4) ioport:40a0(size=16) memory:56204000-562043ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEKT-6
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX71A1198096
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00065236
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: d8fc1dd1-9045-4e5f-883f-2dea921a08cd
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-02-12 10:17:24 filesystem=ext4 lastmountpoint=/ modified=2012-02-12 10:29:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,data=ordered mounted=2012-03-12 18:40:41 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1011MiB
                   capacity: 1011MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1011MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:4000(size=32)
  *-battery
       product: ED03028
       vendor: Conexant (Rockwell)
       physical id: 1
       slot: In the back
       capacity: 28000mWh
       configuration: voltage=10.8V [code/]


When I opened Cheese (which was working at he time) and pasted 
grep uvcvideo: -B2 -A5 /var/log/syslog | tail -n 20 nothing at all happened. I tried it three times.

The next one gave me grep: /var/log/.xsession-errors: No such file or directory
 The last one: [code]
gstreamer-properties

(gstreamer-properties:6857): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:6857): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
[code/]

(That doesn't look good, does it?) It also opened automatically a program called "multimedia systems selector.


Thanks as always!

---

### Post by thestraniero on 2012-03-13
Matt,
With Cheese still running and the webcam on and working I tried to test the video input in this Multimedia Systems Selector and it says... Video for Linux 2 (v4l2): Could not get buffers from device '/dev/video0'.

---

### Post by matt_symes on 2012-03-13
Hi

I was thinking this was an issue with uvcvideo but now i am beginning to  think it may be a gstreamers issue ?

To be honset, I am no expert with webcams under Linux and this one is really confusing me.

Kind regards

---

### Post by matt_symes on 2012-03-13
Hi

Acording to this site your model (not make) of webcam is not supported

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

However, it does work, as you say, so i'm not sure what to make of it :(

Anybody else with more knowledge than i have about webcams under Linux, willing to contribute to this thread ?. 

**EDIT:**

Just a thought. When cheese is not working, open a terminal with cheese still open, does this command return anything ?

```
lsof /dev/video*
```

Post back the contents if it does.

Can we also make 110% sure it's a uvcvideo device.

```
lsusb -vd 05c8:021a | grep -i "14 video"
```

The other thing i was interested in was, do you have any TV capture cards ?

The next time you see video0 and video1 in /dev at the same time, can you post the output of

```
ls -l /dev/v4l/*
```

Kind regards

---

### Post by thestraniero on 2012-03-13
Hi Matt,

lsof /dev/video*Returns nothing when Cheese isn't working. 

mark@mark-Compaq-Mini-CQ10-600:~$ lsusb -vd 05c8:021a | grep -i "14 video"
libusb couldn't open USB device /dev/bus/usb/001/013: Permission denied.
libusb requires write access to USB device nodes.
Couldn't open device, some information will be missing
      bFunctionClass         14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
(The camera wasn't working still)

I'm seeing /dev/video0  /dev/video1 Right now...
mark@mark-Compaq-Mini-CQ10-600:~$ ls -l /dev/v4l/*
/dev/v4l/by-id:
total 0
lrwxrwxrwx 1 root root 12 2012-03-13 19:49 usb-GenesysLogic_Technology_Co.__Ltd._HP_Webcam-video-index0 -> ../../video0
/dev/v4l/by-path:
total 0
lrwxrwxrwx 1 root root 12 2012-03-13 19:49 pci-0000:00:1d.7-usb-0:6:1.0-video-index0 -> ../../video0

So, I'm leaving tomorrow for this trip and would really love to straighten this up as soon as possible, but I don't know how easy it will be for me to get on line.

Thanks a lot Matt and anybody else who's got an idea!

---

### Post by matt_symes on 2012-03-13
Hi

When cheese works and does not work, are you rebooting between attempts or are you just starting and closing cheese and then reopening cheese ?

This may not be fixed before your trip :(

Kind regards

---

### Post by thestraniero on 2012-03-13
Hi Matt,

 I'm not doing anything at all between attempts except openg Cheese again or sometimes Skype. It seems to make no difference and defies all logic.

Thanks for all your concern! Kind regards!

---

### Post by matt_symes on 2012-03-13
Hi

Well i'm currently stumped :confused: I really don't understand why sometimes it will work but the majority of times it will not.

I was hoping that lsof would show something else with a lock in /dev/video0 when you started cheese. 

This is what you should be seeing with cheese running is cheese with the file open.

```
matthew@matthew-Aspire-7540:~$ ps aux | grep [c]heese
matthew   2831 11.1  1.5 786304 44728 ?        Sl   22:18   0:10 cheese
matthew@matthew-Aspire-7540:~$ lsof /dev/video0
COMMAND  PID    USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
cheese  2831 matthew  mem    CHR   81,0          2461930 /dev/video0
cheese  2831 matthew   16u   CHR   81,0      0t0 2461930 /dev/video0
matthew@matthew-Aspire-7540:~$
```

As you did not see cheese with the file open, it looks like it could not even see it.

> mark@mark-Compaq-Mini-CQ10-600:~$ lsusb -vd 05c8:021a | grep -i "14 video"
libusb couldn't open USB device /dev/bus/usb/001/013: Permission denied.
libusb requires write access to USB device nodes.
Couldn't open device, some information will be missing
bFunctionClass 14 Video
bInterfaceClass 14 Video
bInterfaceClass 14 Video
bInterfaceClass 14 Video

It is a uvc complient webcam.

The correct drivers are loaded for it.

I can see no other piece of video capture equipment that would interfere with it.

Cheese looks to be looking for /dev/video0 where we set the udev rule.

There is nothing ominous in the logs.

??

This is your  webcam device

> Bus 001 Device 027: ID [COLOR="Blue"]05c8:021a[/COLOR] Cheng Uei Precision Industry Co., Ltd (Foxlink)

```
matthew@matthew-Aspire-7540:~$ grep -A5 "^05c8" /var/lib/usbutils/usb.ids
**[COLOR="blue"]05c8[/COLOR]**  Cheng Uei Precision Industry Co., Ltd (Foxlink)
        0103  FO13FF-65 PC-CAM
        **[COLOR="blue"]021a[/COLOR]**  HP Webcam
        0318  Webcam
        0403  Webcam
05c9  Semtech Corp.
matthew@matthew-Aspire-7540:~$ 
```

Although i did have to update the usb.ids file using the script /usr/sbin/update-usbids. Before i used that script the HP webcam was not even there.

Maybe it's a new device.

Enjoy your trip and we can have another go when you get back if you wish.

Maybe inspiration will come.

Kind regards

---

### Post by thestraniero on 2012-03-13
Do you think it would be worth it to try and reinstall the system? I'd hate to have to do that, but if it might work I'd do it.

If you come up with any ideas please let me know. I'll be online when I'm online, but I'll have plenty of time to blow for sure.

Ciao!

---

### Post by matt_symes on 2012-03-13
Hi

> **thestraniero said:**
> Do you think it would be worth it to try and reinstall the system? I'd hate to have to do that, but if it might work I'd do it.

If you come up with any ideas please let me know. I'll be online when I'm online, but I'll have plenty of time to blow for sure.

Ciao!

I'm not sure a reinstall would help.

What you can do is try your webcam from a LiveCD/USB and see how that gets on.

Kind regards

---

### Post by thestraniero on 2012-03-14
Matt,

[LEFT][INDENT][INDENT]I just tried running Ubuntu from a USB drive, but then I realized that I don't know how to test the webcam when running the system from an external drive. I can't install any software and Cheese isn't bundled with the system.

I did try ```
ls /dev/video*
``` and it showed up on Video0

Is there any bundled software that Ican use to test the camera?

Kind regards!

[/INDENT][/INDENT][/LEFT]

---

### Post by matt_symes on 2012-03-14
Hi

I'm not sure if it's on the live CD but you could try

```
guvcview
```

You can install program from a LiveCD/USB. They just install to memory.

```
sudo apt-get install cheese
```

Cheese is part is Universe

```
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ apt-cache show cheese | grep -i section
Section: universe/gnome
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615
```

So you would need to enable universe repository and update your sources.

Kind regards

---

### Post by no2498 on 2012-03-15
in a terminal type dmesg click enter
look close to the bottom 20 lines
did it load a cam grabber

also in the terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin

---

### Post by no2498 on 2012-03-15
also look in your system startup programs
make sure skype & cheese is not set to auto startup
windows has control of skype now days

---

### Post by matt_symes on 2012-03-15
Hi

@no2498. These are good suggestions.

> did it load a cam grabber

You also think that something else may have open /dev/video0 exclusively ? I know that only one program can read from the camera at a time unless the second is adjusting the contrast, brightness etc. I was hoping that lsof would highlight that.

That is what it would suggest and would explain why it only works sometimes.

If anybody else has any suggestion for the OP the please also chime in.

Kind regards

---

### Post by thestraniero on 2012-03-18
Hey Matt,

I'll have to wait until I get back to try your suggestions. I have only gotten the camera to work once with Skype since starting my trip and nobody was home to take the call!

Thanks again for your help!

---

### Post by matt_symes on 2012-03-19
Hi

> **thestraniero said:**
> I'll have to wait until I get back to try your suggestions. I have only gotten the camera to work once with Skype since starting my trip and nobody was home to take the call!

Isn't that always just the way :) I hope your trip was good.

I wanted to try something else. From the terminal (might be easier to copy and paste this one into the terminal)

```
sudo modprobe -r uvcvideo && sudo modprobe -r videodev && sudo modprobe videodev && sudo modprobe uvcvideo && cheese
```

This will unload the video (not graphics card) drivers, and reload them and then start cheese.

Does this start cheese correctly with video ? 

If it does then try it at least 10 times and report back on efficacy.

Kind regards

---

### Post by thestraniero on 2012-04-05
Hi Matt,
Thanks for keeping up with this. I just bought a clip on web cam this morning that works just fine right out of the box. The built in camera worked only once in the roughly 20 times I Skyped with my daughter from Costa Rica.

I just tried your above suggestion and I got this message "FATAL: Module video is in use." So, I tried logging out and back in, but I got the same message. (No, there were no peripherals attached.)

I don't understand why there's so much trouble with this built-in web cam especially because Ubuntu claims that there's no need to download drivers. If you want to keep on fighting I'm in with you, I would still prefer to have the built-in cam working, but I have surrendered and bought a external cam...

Cheers Matt!

---

### Post by matt_symes on 2012-04-05
Hi

You webcam should not be in use if nothing is using it.

Mine is not currently in use and this is what i see.

```
matthew@matthew-Aspire-7540:~$ sudo modprobe -r uvcvideo && sudo modprobe -r videodev && sudo modprobe videodev && sudo modprobe uvcvideo && cheese
[sudo] password for matthew: 

(cheese:18761): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:18761): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:18761): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:18761): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:18761): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:18761): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel
matthew@matthew-Aspire-7540:~$ 
```

Can we break tyhe command down a bit. From the terminal type

```
sudo modprobe -r uvcvideo
```

and then type..

```
sudo modprobe -r videodev
```

If either of these commands give you "FATAL: module in use" or words to that effect, then type

```
sudo lsof /dev/video0
```

and post back results.

Kind regards.

---

### Post by thestraniero on 2012-04-05
Hey Matt,
I did as you said and the 2nd comand gave me the FATAL warning, when I ran that last command this was the result...

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mark/.gvfs
      Output information may be incomplete.
lsof: status error on /dev/video0: No such file or directory
lsof 4.81
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhlnNoOPRtUvVX] [+|-c c] [+|-d s] [+D D] [+|-f[gG]]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]] [-p s]
[+|-r [t]] [-s [p:s]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.

---

### Post by thestraniero on 2012-04-05
Matt,
I'm suddenly having some very strange behavior in my computer. I can't get the built in camera to go off. It stays on with no programs running and even if I log out, it's the same when I log back in. It works in Skype, but Cheese just shows a black screen even though the camera light is on. My preferences are no longer highlighted in Cheese and I can't access them (but I did this morning!)
Crazy, huh?

I just got the camera to go off by shuting down and restarting, but when I tried to just restart without shutting down the camera remained on all through startup!

Besides this, now I can't get the new USB camera to work. I have Video 4 Bench Test and I can't switch between the cameras. It was working this morning.

I bet this makes your day! Thanks as always... Mark

---

### Post by matt_symes on 2012-04-06
Hi

My second command should have been

```
sudo modprobe -r videodev
```

and not video. That's what i get for typing in haste. I have ammended my previous post.

Thinking about it as well

```
sudo lsof /dev/video0
```

would have failed after successfully unloading uvcvideo because it's that along with udev that creates /dev/videoX.

To be totally honest, i'm not sure what is happening to your webcams. I have never had a problem with mine and so i have never had to debug issues with them. Because of that i don't know the uvcvideo subsystem that well.

I was hoping someone else, who has had these problems and fixed them, would have spoken up by now.

I will have a ponder but...

Kind regards

---

### Post by Deeday on 2012-04-08
Sorry, no solutions from me but a similar problem. I posted this in the Multimedia forum but nobody replied:
__________________________________________________________________________
This is the only way I can get my webcam to at least turn on:

1) From gstreamer-properties, Video, Default input, I change the plugin to Custom and Pipeline to ```
v4l2src device="/dev/video0"
``` Pressing the Test button gives ```
Error running pipeline 'Custom': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(2143): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1: system error: No such device]

```

2) I change the device to video1 and I get ```
Error running pipeline 'Custom': Error starting streaming on device '/dev/video1'. [gstv4l2object.c(2143): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src2: system error: No such device]

```

3) I change back to video0 and _it works_, i.e. I get the test picture from my webcam.

The behaviour is repeatable, although sometimes it takes one additional step, so it ends up working with video1, instead of video0.

Needless to say, Skype cannot get the webcam to work (blank screen) and it's been like that for ages (over a year, I believe) but now I really would like to sort it out.

My system:
Logitech Orbicam built-in on Acer Aspire 5630 laptop
Ubuntu Oneiric 64
Kernel 3.0.0.18

---

### Post by fresnofred on 2012-04-08
go to synaptic and search for and install guvcview as it seems to work better than cheese

---

### Post by michael888 on 2012-04-11
Since a fresh install of 11.10 on my AA1 ZG5 webcam does not show as present in the top right bar and the various programs show it as not present. I have booted from my USB version of 11.10, the same result.
It did work during one session dont't know why, and then again when I flashed the BIOS although it did not hold when restarted. I do have the 11.10 on my other ZG5 and it works fine, don't know if Acer uses a different cam.

---

### Post by bmullan on 2012-05-23
By chance do you have your webcam plugged into a POWERED USB Hub or an UNPOWERED USB hub.

If UN-powered hub... that may be your problem because perhaps your Webcam draws more power than the USB port is supplying and or just on the cusp and therefore it sometime is "there" and sometimes its "not.




> **thestraniero said:**
> Well, last night the webcam was coming on almost 1 in 2 times which probably explains why it won't come on at all this morning! I'll have to post the working results later. Here's the "not working" results below. By the way the system calls it "HP Webcam" if that helps... Thanks again!

Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
usb_storage            44173  0 
uas                    17699  0 
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31444  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55577  2 vfat,msdos
jfs                   175084  0 
xfs                   746838  0 
reiserfs              230932  0 
snd_hrtimer            12648  1 
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
joydev                 17393  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  1 
snd_seq_midi           13132  0 
videodev               85626  2 uvcvideo
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth             148839  23 rfcomm,bnep,btusb
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393421  1 brcmsmac
binfmt_misc            17292  1 
cfg80211              172427  2 brcmsmac,mac80211
snd                    55902  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  509519  4 
crc_ccitt              12595  1 brcmsmac
soundcore              12600  1 snd
drm_kms_helper         32889  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
drm                   192194  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0

---

### Post by matt_symes on 2012-05-24
Hi

> **bmullan said:**
> By chance do you have your webcam plugged into a POWERED USB Hub or an UNPOWERED USB hub.

If UN-powered hub... that may be your problem because perhaps your Webcam draws more power than the USB port is supplying and or just on the cusp and therefore it sometime is "there" and sometimes its "not.

This is an excellent thing to check and never occurred to me that it may be a USB power problem.

I have had the same issue with USB powered hard drives and it makes them act intermittently.

Definitely worth checking.

Kind regards

---

### Post by jerome schatten on 2012-05-24
Hi Matt et al:

I've been following this thread with great interest. I have a somewhat different situation that I could use some guidance on:

Running Ubuntu 9.1 on a P5 dual core desktop, and trying to get my webcam Live! to run with skype. 'lsusb' reports it as: 'Bus 008 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro'.  And this is NOT in the list of supported devices.

Works fine with Cheese: -- it identifies the Video Device correctly as a
WebCam Live! using /dev/video0 and produces a video image.

In the setup for skype video, it also reports that I'm using WebCam
Live! on /dev/video0.

ls /dev/video0 -la returns
'crw-rw----+ 1 root video 81, 0 2012-05-22 15:08 /dev/video0' 

Testing in Skype produces a blank screen.  Is there anything else I can look at? My thinking was, that since it worked in Cheese, it ought to work in Skype.

Best,
Jerome

---

### Post by mörgæs on 2012-05-24
If you are on Ubuntu 9.10 I would recommend that you begin with a fresh install of 12.04.

---

### Post by matt_symes on 2012-05-24
Hi

@jerome schatten

Do you still need the compat/convert libraries for skpe now ? It's something i never use anymore.

Try this from the terminal

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

or this

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

**EDIT:** If on a 64 bit system then try

```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so skype
```

or this

```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so skype
```

Kind regards

---

### Post by jerome schatten on 2012-05-24
Thank you Matt... both worked!!!!  Both produced the same non-fatal error:

orange@orange:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
libv4l2: error allocating conversion buffer

I guess I'll put this in a little shell script and start skype with it.

Thanks again; Problem solved.!
Jerome

p.s. The suggestion that I upgrade is well taken. I will eventually do that!
j.

---

### Post by bmullan on 2012-06-05
Do a google search for "ubuntu preload webcam skype"

an example answer will go over this fix for Skype:

[http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html]("http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html")

> **jerome schatten said:**
> Hi Matt et al:

I've been following this thread with great interest. I have a somewhat different situation that I could use some guidance on:

Running Ubuntu 9.1 on a P5 dual core desktop, and trying to get my webcam Live! to run with skype. 'lsusb' reports it as: 'Bus 008 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro'.  And this is NOT in the list of supported devices.

Works fine with Cheese: -- it identifies the Video Device correctly as a
WebCam Live! using /dev/video0 and produces a video image.

In the setup for skype video, it also reports that I'm using WebCam
Live! on /dev/video0.

ls /dev/video0 -la returns
'crw-rw----+ 1 root video 81, 0 2012-05-22 15:08 /dev/video0' 

Testing in Skype produces a blank screen.  Is there anything else I can look at? My thinking was, that since it worked in Cheese, it ought to work in Skype.

Best,
Jerome

---

