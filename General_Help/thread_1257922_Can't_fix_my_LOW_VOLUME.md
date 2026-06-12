---
title: "Can't fix my LOW VOLUME"
date: 2009-09-04
forum: General Help
---

### Post by jschille on 2009-09-04
There have been quite a few threads about the low volume in Jaunty.
One person said he had a fix for it and it seemed that the fix worked for everyone else, but has not fixed mine.  I am probably doing something wrong.

The fix was to go into my alsa-base.conf and add the line
options snd-hda-intel model=3 stack
My sound is STILL very low and didn't change anything. =/

EDIT: just found another command that worked for some one else
[B]options snd-hda-intel model=dell-m4-1

is the command computer specific? I am using a dell xps studio 64 bit...
[/B]

---

### Post by wiremoons on 2009-09-04
I also have to edit the **/etc/modprobe.d/alsa-base.conf** file to enable the sound to work on my Dell 540 Studio PC. However I need to add the line **options snd_hda_intel probe_mask=1** to the end of the file - this line would vary of course depending on your hardware.

Once you have done the above edit, and rebooted your computer the sound should work now - but the volume may still be low. 

What I do to set the sound levels so they are louder, is open a Terminal window and run the command **alsamixer -c 0** and set the level on the outputs for the sound card to maximum.  Use the cursor/arrow keys on the keyboard to navigate around the sound level setting, press the Esc key to exit once you are done.

Hope that helps!

---

