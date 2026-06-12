---
title: "Blank boot screen"
date: 2012-01-05
forum: General Help
---

### Post by Rehtwol on 2012-01-05
Hey,

I've been poking around for a day or two to solve this, it's time I get help. I have a newly built machine, I dropped Windows 7 onto it and made sure that Windows was happy with all its drivers before putting in a Ubuntu CD.

I made a separate partition for Ubuntu on my primary drive, and ran the installer from the LiveCD desktop. It claimed to have successfully installed, so I figured I should give it a shot. Upon booting into Ubuntu I was greeted by a flashing purplish screen that didn't respond to anything except <ctrl>+<alt>+<F1> which gave me a black completely unresponsive screen (instead of an active terminal).

After 2 failed boots I pulled up the LiveCD again and wiped the Ubuntu partition for a fresh install, this time the install claimed to fail just before completing. The installer then gave me the option to remove and replace the current Ubuntu installation on the system (presumably replace the broken install for a good install), so I figured I'd give it a chance.

And now I'm back to a flashing screen that only responds to <ctrl>+<alt>+<F1> with a black screen. My best guess is that something is up with a driver for my video card, but I have no idea how to put a good driver on when I can't get into Ubuntu.

Any ideas?

Note, through all this Windows 7 had been booting happily and running without a problem.

---

### Post by imachavel on 2012-01-05
well if windows 7 boots fine then that is awesome. windows has this thing where it doesn't like other OS booting with it. Some people deny it, but I've seen it so how is it denyable. Now, it's not a hardware problem, if it was, windows wouldn't work.

let's get redundant, which sucks, what is your model of gpu? you installed it? did you try putting the driver disk in when booting up linux? try that. Can you get into recovery mode at all? if you can get to desk top, try taking the driver off the cd. I believe with restricted drivers if the driver is recognized in the repository you can install it. If you take the file off the disk linux may think it's not a driver. I don't know if opening with wine would help at all. It's clear that wine is not a windows emulator hence it's name. Just a way to use executable files, no compatibility. 

get to the command line if possible, use these commands:

less /proc/modules
 $ lsmod

and then maybe sudo apt-get install update

for good measure of course. if you don't trust the commands, I'll prove they are safe:

lsmod
Module                  Size  Used by
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
nls_utf8               12493  0 
isofs                  39571  0 
binfmt_misc            13213  1 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  1 
snd_intel8x0           33213  2 
snd_usb_audio          91410  1 
snd_hda_intel          24113  0 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_hda_codec          90901  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
snd_pcm                80042  6 snd_hda_codec_hdmi,snd_intel8x0,snd_hda_intel,snd_usb_audio,snd_ac97_codec,snd_hda_codec
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
fglrx                2434640  295 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
gspca_sonixj           32443  0 
gspca_main             27894  1 gspca_sonixj
psmouse                73312  0 
snd_timer              28659  2 snd_pcm,snd_seq
r8712u                281937  0 
dcdbas                 14054  0 
usblp                  17827  0 
joydev                 17322  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  1 gspca_main
parport_pc             32111  1 
serio_raw              12990  0 
snd                    55295  19 snd_hda_codec_hdmi,snd_intel8x0,snd_hda_intel,snd_usb_audio,snd_ac97_codec,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_intel8x0,snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 
floppy                 60032  0 
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs



sudo apt-get install upgate for me of course says nothing to install, I've been doing it all day. It's better then crack

---

### Post by alphaamanitin on 2012-01-05
Are you using an UEFI motherboard?

AlphaA

---

### Post by Rehtwol on 2012-01-05
> **imachavel said:**
> let's get redundant, which sucks, what is your model of gpu? you installed it? did you try putting the driver disk in when booting up linux? try that. Can you get into recovery mode at all? if you can get to desk top, try taking the driver off the cd. I believe with restricted drivers if the driver is recognized in the repository you can install it. If you take the file off the disk linux may think it's not a driver. I don't know if opening with wine would help at all. It's clear that wine is not a windows emulator hence it's name. Just a way to use executable files, no compatibility. 

get to the command line if possible, use these commands:

less /proc/modules
 $ lsmod

and then maybe sudo apt-get install update

Here goes, the card is a Sapphire HD6850. I built the entire machine myself only a a few days ago. I tried to boot Ubuntu with the driver disk (the one supplied by Sapphire) in the drive, for a moment it looked like it was going well (didn't go to the crap screen immediately), but in the end I got stuck at the same point.

I can get into recovery mode, but I'm pretty sure something is up with it. If I move the selector around I can see the options, but when it first loads I get a bunch of messages about some hardware in some port or another covering my options.

I can't get to the desktop at all, I can keep trying things (like if I can get a command line screen up) when I next get a shot. For now I'll have to wait and see if anyone else has any suggestions as I'm away from the computer until the weekend...

---

### Post by imachavel on 2012-01-05
well at least you know it's an OS issue and not a hard ware issue. Have you considered actually putting gparted in, booting from it, deleting the partition, creating a new one(careful, leave the size the same, you don't want to break the contiguous pattern) then reinstalling ubuntu? Maybe this is the only solution? However, when you get into recovery mode, do you choose start x ever?

try that from the command line, or try and option that says 'boot into low resolution mode'

well, good luck. If you solve it, let everybody know. sapphire hd 6850, not bad. One more time, did you get the driver to install only in windows, or also in linux? That card is probably brand new, you may want to to allow linux to use a generic driver until the driver support for the card is debugged(it may take awhile and no information will be released, but the linux team will surely debug support for newer hardware)

Anyone find this advice bad? If so please state why, I'm just giving out what is from the best of my knowledge.

---

### Post by Rehtwol on 2012-01-05
> **imachavel said:**
> well at least you know it's an OS issue and not a hard ware issue. Have you considered actually putting gparted in, booting from it, deleting the partition, creating a new one(careful, leave the size the same, you don't want to break the contiguous pattern) then reinstalling ubuntu? Maybe this is the only solution? However, when you get into recovery mode, do you choose start x ever?

try that from the command line, or try and option that says 'boot into low resolution mode'

well, good luck. If you solve it, let everybody know. sapphire hd 6850, not bad. One more time, did you get the driver to install only in windows, or also in linux? That card is probably brand new, you may want to to allow linux to use a generic driver until the driver support for the card is debugged(it may take awhile and no information will be released, but the linux team will surely debug support for newer hardware)

Anyone find this advice bad? If so please state why, I'm just giving out what is from the best of my knowledge.

The first time I tried to re-install Ubuntu I did it by booting from the CD, using GParted to completely wipe the partition I had Ubuntu on, then tried to re-install it. Is that what you mean? 

"Start X"? As in the one that says "resume"? If so, yes, that one leads to a black screen that's unresponsive.

I don't have a "boot into low resolution mode" option, at least not that I've seen. The 5 options given to me from the bootloader are Ubuntu, Ubuntu in recovery mode, Memtest, Memtest command line, and Windows 7.

What's bugging me is that when I boot off my Ubuntu CD it runs happily displaying a desktop and all, it's just when I'm booting off the hard drive that it gets unhappy...

---

### Post by Rehtwol on 2012-01-08
> **imachavel said:**
> well if windows 7 boots fine then that is awesome. windows has this thing where it doesn't like other OS booting with it. Some people deny it, but I've seen it so how is it denyable. Now, it's not a hardware problem, if it was, windows wouldn't work.

let's get redundant, which sucks, what is your model of gpu? you installed it? did you try putting the driver disk in when booting up linux? try that. Can you get into recovery mode at all? if you can get to desk top, try taking the driver off the cd. I believe with restricted drivers if the driver is recognized in the repository you can install it. If you take the file off the disk linux may think it's not a driver. I don't know if opening with wine would help at all. It's clear that wine is not a windows emulator hence it's name. Just a way to use executable files, no compatibility. 

get to the command line if possible, use these commands:

less /proc/modules
 $ lsmod

and then maybe sudo apt-get install update

sudo apt-get install upgate for me of course says nothing to install, I've been doing it all day. It's better then crack

I have access to the machine again, and nothing has changed, it still boots into stubborn mode. On the plus side, after a little poking around, I got into recovery mode. I told it to do a fsck (file system check), grub update, dpkg (broken package repair), and clean (try to make free space). All ran happily and most claimed not to do much if anything (except dpkg, but that was innocent enough). I then proceeded to "resume normal boot".

I got a screen that looked very console-like, but wasn't responding to inputs. by clicking <ctrl>+<alt>+<F1> I got into a proper console which claimed Ubuntu had booted and was running, took my password and let me play a bit. I ran lsmod which just ran out a listing like it did for you (not sure what you expected to be looking for), and sudo apt-get install update, which (with the driver CD in the machine) claimed to find no updates.

Any suggestion where to go from here? I can't seem to get to the desktop, but Ubuntu seems to be installed and running, which is a step in the right direction.

---

### Post by Rehtwol on 2012-01-08
A little more messing around and I think I have the problem figured out, just no idea how to go about a solution.

I've rebooted a few times now, and once in a few I actually get a log in screen (though I have yet to have it display correctly). Every time it's wrapped around or shifted vertically and flashing like mad. I presume that this is caused by some nasty bugged video driver.

Now, presuming I have a driver CD that came with the video card, and access on another machine to the internet to download any necessary driver files, how do I go about installing a good driver? Or does a working driver for the HD6850 exist within Ubuntu somewhere?

Either way, it seems easiest for me to get a console screen and thus a way to activate/install a driver that way would be best...

---

### Post by Rehtwol on 2012-01-09
Solved!

So as suspected, the driver that Ubuntu used by default was acting up. It turned out to be a simple matter of retrieving the latest closed driver from ATI and installing it properly (took 2 tries, but I got it)...

Thanks for all the help!

---

