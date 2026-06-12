---
title: "vga=xxx"
date: 2011-05-26
forum: General Help
---

### Post by frank_n on 2011-05-26
Under 10.04 vga=xxx as a kernel boot option allowed me to set the framebuffer resolution for the text console (note: text console means no desktop).

The same option under 11.04 is accepted but has no effect. When I move to the text console I get some 48 lines and a font which is a physical pain on my eyes. I have run 'dpkg-reconfigure console-setup' and it works. But at the next boot we are back again to the unreadable framebuffer. I can now run 'setupcon' and it works but what is needed is a permanent solution.

So how can I convince 11.04 to respect my option vga=xxx?

---

### Post by TeoBigusGeekus on 2011-05-26
The vga=xxx method is deprecated in grub2. Add these lines
```
GRUB_GFXMODE=1280x1024x32
GRUB_GFXPAYLOAD_LINUX=keep
```
to your grub.cfg file (replacing 1280x1024x32 with your desired resolution of course) and run
```
sudo update-grub
```

---

### Post by frank_n on 2011-05-27
Thanks, Teo, but please note that I'm booting 11.04
from Windows boot.ini through grub4dos - exactly as 
I did for 10.04 without problems.

Since I got into trouble in the past de-installing grub2, it
is still officially installed but I renamed its files so
they cannot be found.

What files are responsible for passing parameters to the
kernel at boot time? Assuming these files are scripts, I
tried to find them searching for 'vga', 'frame', 'fb',
'vesa'. Total failure.

Thanks again.


frank

---

