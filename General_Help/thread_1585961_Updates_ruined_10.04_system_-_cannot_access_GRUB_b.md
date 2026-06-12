---
title: "Updates ruined 10.04 system - cannot access GRUB boot loader - locked out!!"
date: 2010-10-01
forum: General Help
---

### Post by The Bright Side on 2010-10-01
Hey guys!

Update Manager installed a bunch of updates this morning, including the latest kernel (Lucid 64 bit). Now, my PC only boots into text mode, Gnome no longer loads.

Problem is, text mode isn't displayed properly on my PC since I installed 10.04 and the NVidia graphics driver. I only see colourful pixels where letters should be. So I can't really use it.

I tried re-installing the NVidia driver to get Gnome running again (guessing Ubuntu's reponses from the colourful pixels I saw), but the installer won't load. Obviously, I can't tell why.

I can't access the GRUB boot loader either to run the previous kernel, no matter how much I slam the F8 or ESC keys during boot. This used to work.

So, I'm effectively locked out of my system.

Currently copying my Home directory to USB hard disk (ran "sudo nautilus" from Live CD to access it), hope all files will be transferred fine.

Does anybody have an idea how I can get back into my system, though? This really sucks :-(

[LIST]
[*]Is there a way to run the GRUB boot loader from CD?
[*]How can I re-install Ubuntu without destroying the partition that has my Home folder on it?
[/LIST]

Hope you can help me!
Thanks!

---

### Post by Quackers on 2010-10-01
In 10.04 you need to hold the shift key to access grub.

---

### Post by andrewthomas on 2010-10-01
You could chroot from the liveCD.

[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

and update your nvidia drivers

```
sudo apt-get update && sudo apt-get install nvidia-common
```

in the chroot.

---

### Post by The Bright Side on 2010-10-01
Thank you so much. I will try that tonight when I get back from work.

---

### Post by The Bright Side on 2010-10-01
Pressing Shift did it... Hard to believe it could be something this simple. Thanks! You lifted the veil of fear from my soul. :-)

---

### Post by Quackers on 2010-10-02
The shift key thing started when grub2 was introduced (9.10 I think) rather than the esc key.

---

### Post by The Bright Side on 2010-10-02
Yeah when you posted it, I realized that there was that change, but I had totally forgotten about it since, because I only had to use the boot loader once or twice. It's also a bit hard to find on the internet, I mostly found older tutorials.

Thanks anyway!

---

### Post by Quackers on 2010-10-02
No problem. It's very easy to forget something you very rarely use!

---

