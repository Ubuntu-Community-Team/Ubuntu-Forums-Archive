---
title: "Audio Working but Volume Control Isn't!!"
date: 2010-02-16
forum: General Help
---

### Post by timetraveller85 on 2010-02-16
Hey guys,

I'm sorry I've started this thread because its very similar to others that have been started but my problem is a bit weird:

I have a dual boot and my windows plays audio fine.

My ubuntu plays audio fine as well however when I click on the Volume Control icon on the panel it gives me this error:

**No volume control GStreamer plugins and/or devices found.**

I tried the instruction in this page: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

and I am still unable to control volume. I have alsamixer installed and it can control my system sound fine but all this time I've been able to use the controls on my HP Pavilion dv5250ca laptop's keyboard controls to control the volume and I'd like to be able to continue doing that- I haven't been able to for the last 2 days.

This is the output from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And this is the output from lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Some additional info: 
I recently upgraded to gstreamer 0.10.23 to get farsight2 to work with amsn (hasn't worked...)

Could that be a problem?

My system: Ubuntu 8.10 Intrepid

If this thread is inappropriate please let me know and I will repost it where appropriate. Or if there is a resolution somewhere, kindly point to it...

Regards,

TT

---

### Post by dragos240 on 2010-02-16
Hmm.... Can you change the volume via alsamixer? If not, it's something with gstreamer.

---

### Post by timetraveller85 on 2010-02-16
Yea,

My Songbird plays music awesome. I can change the volume level for songbird and also change the audio level for the system as a whole using alsamixer.

It's really weird.

If I reinstall a previous version of gstreamer will it replace the current newer one? If so, which one should I install because I do not recall which one was installed...

Thanks for the prompt response by the way...

---

### Post by dragos240 on 2010-02-16
Actually! Have you upgraded the plugins in gstreamer? If they're not the same version, they may not work. Make sure the plugins are all the same version, and that the version is the same as gstreamer itself.

---

### Post by timetraveller85 on 2010-02-16
Ok, that makes sense. 

But there's so many plugins. Which ones do I choose to remove and install again?

---

### Post by dragos240 on 2010-02-16
> **timetraveller85 said:**
> Ok, that makes sense. 

But there's so many plugins. Which ones do I choose to remove and install again?

Actually, there are only a few. They provide many. Try installing the latest gstreamer-plugins-good and gstreamer-plugins-base. They are the ones that will work with the gnome app.

---

### Post by timetraveller85 on 2010-02-16
THAT WORKED!!!!

THANKS!!!
I installed the latest gstreamer first

Then the gstreamer-plugins-base of the same version

then the lateest gstreamer-plugins-good

WORKED!!!

Thanks a lot!!!

---

### Post by dragos240 on 2010-02-16
No problem. Always happy to help!

---

