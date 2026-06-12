---
title: "Ubuntu 9.10 on HP Pavilion dv6 series (for beginners)"
date: 2010-04-01
forum: General Help
---

### Post by Cephiro on 2010-04-01
Hi folks, dunno if this is the right place to post something like this, but I'd like to write rhis in the forum just for the record. Moderators, please move this thread if you think it's in the wrong place.

I am an absolute beginner, and have only started to try Linux, and as such I don't have any technical knowledge about it.

I had been trying to get Ubuntu working on this HP Pavilion dv6 laptop, but it for some reason it won't recognize the sound card. Which is weird, because OpenSUSE has no problem with it whatsoever.

There are many topics on this, and all of them try to address the issue in different manners, making you download lots of stuff and edit tons of files. It does work, but it seems like too much for absolute beginners to handle.

So, I had to reinstall Linux, and as I had to get the sound working again, I found a simpler sure-fire (as far as I know) way to get it working. 

Just open the terminal and type this: > gksudo gedit /etc/modprobe.d/alsa.confIn the alsa.conf file, add this as the last entry in the file: > options snd-hda-intel model=hp-dv5

Save the file and close gedit.

Then, go to System>Preferences>Sound. Open the tab 'Hardware', select 'Internal Audio', and set the profile to 'Analog Audio Output'. Open the tab 'Output' and select 'Internal Analog Audio Stereo'.

Reboot the computer, and sound should be working on the next boot. The quality is not the best, but at least it works.

From them on, go to Synaptic and download the flash plugin, the restricted extras, and voila, you have a fully working system ready to handle anything.

Hope this helps someone. This problem seems to be quite common with this model of laptop, and I justed wanted to share the solution I've found.

---

### Post by egbertdevries on 2010-04-16
Dear Cephiro,

Thanks for this input.
The laptop of an colleague had this problem and it worked like a charm
Could you mention the model DV6 you made this solution for?

for instance I've got the HP Pavilion dv6-2130ed

Which is almost fully intel based, except the broadcom wireless which works with 3rd party drivers out of the box. Just had to connect once to lan with the "old" cable and ran a check via System > Administration > Hardware drivers.
Even my webcam, HDMI and remote control worked nicely out of the box without a hitch.

I've been running on 9.04 9.10 and Lucid beta1 without much fuss and also Lucids beta2 seems to work fine now. But i know HP makes more than one type DV6 which can be entirely different machines all together.

Regards
__[]("http://ubuntuforums.org/member.php?u=1041965")

---

### Post by Cephiro on 2010-05-17
Hi there.

Sorry for the late reply, I've been away from the forums for a while.

I'm not really sure of which model I have. I got it custom-made by HP, but I guess the soundcard they use is common to all their laptops.
Mine is a Turion X2 machine, so it's AMD-based.

Sound worked fine on karmic, and since I upgraded to Lucid it is still working. I think I'll try to do a clean install of Lucid and see how it handles the hardware

---

