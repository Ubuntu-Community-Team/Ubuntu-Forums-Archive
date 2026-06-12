---
title: "Sound crackling in meerkat"
date: 2010-11-25
forum: General Help
---

### Post by s0dium on 2010-11-25
For some reason when I listen to audio on my panasonic toughbook CF 52 I get a crackling sound coming from my speakers. However with my sony vaio this is not the case. Has anyone else en-counted this problem? 

Thanks for any help.

---

### Post by kanishkdudeja on 2010-11-25
in your sound settings, keep the output at 100 %..not beyond that..then check

---

### Post by s0dium on 2010-11-25
Thanks, it was below 100%, I have put it to 100% and it seems to have cured it :)

---

### Post by kanishkdudeja on 2010-11-25
no problem. Please mark the thread as Solved.

---

### Post by s0dium on 2010-11-28
Sorry the problem seems to have come back, any other suggestions?

---

### Post by kanishkdudeja on 2010-11-28
check if exclusive linux drivers are available for ur audio card.

mayb the wire connecting the lappy to the speakers has a problem or the audio port is damaged.

wen i keep my audio ouput above 100% only den the sound seems to crackle.

---

### Post by edwardoclese on 2011-03-11
My CF-51 is doing the same thing under Maverick. I have seen a thread that reports this as an issue involving Intel video and Flash, but I can't seem to find it. 

Note that this problem didn't exist under Lucid, but another problem did. It involved my wireless stalling. It was solved by adding a command to my startup grubfile, something to the effect of "radeon-modeset=0". (Don't quote me on that, I have to look it up again.) Seems that Flash running on fullscreen strained resources to the point of kicking an error to the wireless chipset (Intel 3945 a/b/g).

---

### Post by edwardoclese on 2011-03-12
I've done quite a bit of looking through the forums and tried many things, and am beginning to think I am stuck with this. 

Modifying [FONT=Courier New]/etc/pulsemod.d/alsa-base.conf [FONT=Arial]with [FONT=Courier New]option-hda-intel model=panasonic [FONT=Arial]did not fix, nor did any of the remove/replace Adobe flash  with Gnash or notfree schemes.

Checking alsamixer settings does not help, nor does configuring any of the options on the Gnome default sound settings.

As I said in the title, I get audio crackle distortion during Flash playback only during fullscreen operation.
[/FONT][/FONT][/FONT][/FONT]

---

### Post by edwardoclese on 2011-03-13
I've been a busy Meerkat, studying the forums, and have found some relief!

Major changes: Purged the old ATI driver [FONT=Courier New]fglrx [FONT=Verdana], reload the current ATI stuff and then chased down newer video drivers. Added commands to the [FONT=Courier New]alsa-base.conf [/FONT]and to the grub bootloader,  following these various pages:[/FONT][/FONT]

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)**HdaIntel**SoundHowto

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)


These pages pointed to some Launchpad pages with xorg edgers drivers, and I added the repository via a terminal window command.

I used update manager to update my system with the new packages.

I used Terminal window:
[FONT=Courier New]sudo nano /etc/modprobe.d/alsa-base.conf
[FONT=Verdana]to add the following line at the bottom
[FONT=Courier New]options snd-hda-intel model=panasonic
[FONT=Verdana]and
[FONT=Courier New]sudo nano /boot/grub/grub.cfg
[FONT=Verdana]to add the command to the first instance of linux near the end of that line:
[FONT=Courier New]radeon.modeset=0

I now have beautiful flash video, no audio crackle, and my wireless is happy too!

[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by edwardoclese on 2011-05-16
Well, I was far too pleased with myself earlier. 

I posted a lot of patches that seemed to be required to repair the crackle from Flash video running at fullscreen 1600x1200.

The only one that seems to have truly affected the situation is [FONT=Courier New]radeon modeset=0 [FONT=Verdana]which has the unfortunate side effect of disabling 3d GL hardware acceleration.

I've reverted to the standard ubuntu distro drivers, and am tolerating the crackles and occasional system crashes, which persist even under the most recent Flash updates.

Sorry for any confusion.
[/FONT][/FONT]

---

