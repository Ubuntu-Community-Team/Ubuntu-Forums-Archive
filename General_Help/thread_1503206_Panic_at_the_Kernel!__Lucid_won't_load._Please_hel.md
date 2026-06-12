---
title: "Panic at the Kernel!  Lucid won't load. Please help!"
date: 2010-06-06
forum: General Help
---

### Post by giddyup306 on 2010-06-06
Hello.  


I went to fire up Lucid this after noon and it gave me this error message.  I didn't want to write all of that down so I took a picture.  


[IMG]http://i169.photobucket.com/albums/u219/giddyup306/ruh-roh.jpg[/IMG]

After several minutes it did nothing.  I then decided to do a hard restart.  This time it isn't giving a signal to the monitor.  The monitor is less than half a year old, but I tried another.  Still nothing. It show's no signal like it's not even hooked up to a machine.  It doesn't even show the BIOS menu! I don't know if this is the cause or not but, I left my computer at my mothers house last night were they had a thunderstorm.  

Any help would be greatly appreciated.  I have several applications like Virtual box and Mobloquer that took a hell of a long time to setup.  Plus three guest operating systems, and some work that I didn't backup like videos.  If we can get this up and running without re-installing...  Sorry but I really don't know where to start with this, so I figured I'd just jump in and ask.

Thanks,

Mike

---

### Post by davidmohammed on 2010-06-06
at a guess - framebuffer refers to I think your graphics card.  Maybe a recent update has issues with your driver - is it a proprietary one like nvidia or ATI?

to get a basic desktop I would boot you system with the options

nomodeset xforcevesa in your grub

(press shift on boot to display grub [list of kernels], press e, then on the line with quiet splash add the above before quiet splash).

You might also like to see if booting with an earlier kernel fixes your issue.

---

### Post by giddyup306 on 2010-06-06
> **davidmohammed said:**
> at a guess - framebuffer refers to I think your graphics card.  Maybe a recent update has issues with your driver - is it a proprietary one like nvidia or ATI?

to get a basic desktop I would boot you system with the options

nomodeset xforcevesa in your grub

(press shift on boot to display grub
[list of kernels], press e, then on the line with quiet splash add the above before quiet splash).

You might also like to see if booting with an earlier kernel fixes your issue.
Thanks for the reply.  

Yes my graphics card is a nvidia.  When I try and restart the computer it tells me that I have no DVI or VGA signal.  It's just like it's not even hooked up to a computer.  Then it goes to sleep.   :-({|=

---

### Post by #!/bin/bash on 2010-06-06
> It show's no signal like it's not even hooked up to a machine. It doesn't even show the BIOS menu! 
Does it beep at all. There are beep error codes you can find on the Internet that might give you a clue. Do you hear the hard drive? Does the hard drive led flash? Does keyboard lights flash at all?

Try to unplug it and let it sit for 5 min then plug it in again and turn it on.

---

### Post by davidmohammed on 2010-06-06
... what was the outcome of booting with those options I suggested?

---

### Post by giddyup306 on 2010-06-06
Thanks for the help guys.  I have no idea how it happened, but now it is working fine.  

I'm still curious as to why it did what it did.  *shrugs*

---

