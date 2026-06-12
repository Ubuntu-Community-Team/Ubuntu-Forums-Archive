---
title: "Screen resolution stuck at 800x600"
date: 2010-08-04
forum: General Help
---

### Post by Cilionelle on 2010-08-04
Hey guys,

I've been using Ubuntu for some time, currently running 9.10 on my old(ish) Dell desktop.  I've recently plugged in my 32" TV as a monitor and for some reason, the display is stuck inside Ubuntu at 800x600 or lower (4:3 ratio).  I say inside Ubuntu, because the black and white splash screen before the brown one with the loading bar displays at 1280x1024, and Windows XP (which I keep for iTunes) runs quite happily at higher resolutions.  The TV itself is designed for 1920x1080 and so that shouldn't be a problem.

I followed the steps of [this thread here](http://ubuntuforums.org/showthread.php?t=1370258&highlight=1545+resolution) but at Step 5, the terminal tells me that the max resolution is 800x600 and will not proceed further.  I'm not confident enough to craft an entirely new xorg.conf file, and would really like some help getting my display back to where it should be.

Many thanks in advance,
Cilionelle

---

### Post by Cilionelle on 2010-08-05
Bumping this...:p

Or not... is bumping disabled?

---

### Post by Cilionelle on 2010-08-06
Could anyone out there please help me?

---

### Post by TimEnid on 2010-08-06
dvi or hdmi? what type of graphics card do you have?

---

### Post by badbradmx on 2010-08-06
you could back up your xorg.conf file and try some configuring. if it goes wrong you can always revert back to the backup, through windows if need be. afterall you are dual booting.

thats all i have to offer :/

---

### Post by Cilionelle on 2010-08-07
> **TimEnid said:**
> dvi or hdmi? what type of graphics card do you have?

Just VGA (regular monitor input).  I'm not using the HD stuff.  Even getting to the next step up, or a  16:9 ratio, would be a boon.

I'm using an old Nvidia GeForce 5200, with 128MB on board.  Not really much of an issue though since Windows runs it happily.

---

### Post by davidmohammed on 2010-08-07
are you using the proprietary driver or the standard driver that comes with ubuntu (Administration - Hardware Drivers)?  If its the former - use "nvidia-settings" to change your screen resolution.  If its the latter - you probably cant change the screen resolution...

---

### Post by Cilionelle on 2010-08-10
I've tried both.

The standard driver lets me do 800x600, 640x480 and 320x240.
The nVidia one lets me do only 640x480 and 320x240.

If it is a case of not being able to change to a higher resolution, then that will be the end of my Ubuntu usage.  It seems like a flaw that will ultimately kill a great product.

---

### Post by mortrca on 2010-08-10
When I first started using Ubuntu, I had problems getting my NVIDIA graphics card to work. A friend of mine provided this fix:

"using synaptic package manager install the following:"
(note: I was unable to find all of these packages, but I installed the ones I found and it worked fine."
"nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

Then open System-->Administration-->Hardware Drivers.
If there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 180 driver
click Activate.
click Close.
Reboot."

---

### Post by ST3ALTHPSYCH0 on 2010-08-10
You might try the link in my sig.... your mileage may vary.

---

### Post by elricscripts on 2010-08-12
What helped me when i changed my monitor was to activate the 'screens and graphics' app Under Applications -> Other.  If it's not there edit the menu and add it (hopefully it applies to 9.10 as well).  It helps to match your graphics card to your monitor and make custom settings.

---

### Post by ST3ALTHPSYCH0 on 2010-08-12
They took "screens and graphics" out in 8.10 or 9.04. That's the tool used in my method. It requires an 8.04 LTS CD, but it worked, and I didn't have to manually build an xorg.conf!

---

### Post by elricscripts on 2010-08-13
Too bad it's been removed :(.  I wouldn't have known how to setup my widescreen monitor without it.

---

### Post by ST3ALTHPSYCH0 on 2010-08-13
+1, but apparently there are issues with that app and the newer versions of X.

---

### Post by Cilionelle on 2010-08-18
Sigh.

Why?  Why would this happen?  What's the point of taking out perfectly helpful options?  I don't get it.

So, the only option now is to get a copy of 8.10 and do an xorg.conf file from there (as per your instructions, ST3ALTHPSYCH0) and hope for the best... so much for forward momentum.

---

### Post by ST3ALTHPSYCH0 on 2010-08-19
I REALLY think that it was gone by 8.10.  I know it was still available in 8.04 LTS. I'm sure it's still available via torrent (a couple of months ago I was able to get most releases back to 6.06).

---

### Post by Cilionelle on 2010-08-23
Thanks for your help, ST3ALTHPSYCH0.  I'm done with it now.  Finished with Ubuntu.  I just don't really care for the trouble of making it work.  I've got better things to be doing with my time.

Thanks too to everyone who made my journey into Linuxland an interesting one.  It's been really good and a great learning experience.

Cheers!

---

### Post by ST3ALTHPSYCH0 on 2010-08-23
I laughed, at the situation and at your sig. I'm not laughing at you, I promise one day you'll look at it and laugh as well. I also understand that this isn't that day.

---

### Post by Cilionelle on 2010-08-23
Hopefully, by then, Ubuntu will work on 32" TVs...

I'll still be around occasionally, checking how things are going.  But for now, I'm done.

---

