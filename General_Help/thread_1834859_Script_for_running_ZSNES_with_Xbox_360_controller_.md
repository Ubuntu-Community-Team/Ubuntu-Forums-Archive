---
title: "Script for running ZSNES with Xbox 360 controller support"
date: 2011-08-28
forum: General Help
---

### Post by ecosvaldo on 2011-08-28
Hello everyone. I'm new to the Ubuntu scene and was looking for some help. I bought a Toshiba NB505-N508BL netbook less than a month ago and, after messing around with Windows Starter, I decided to go the Linux route and installed Ubuntu 11.04 (upgraded the ram to 2GB at the same time).

After getting everything set up the way how I wanted, I installed ZSNES with no problems. The only thing is that using the arrow keys as a d-pad puts a strain on my fingers after five minutes of use, so I did some research and found that I'm able to use my Xbox 360 controller in Ubuntu. So I came across the **Userspace Xbox/Xbox360 USB Gamepad Driver** ([http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/~grumbel/xboxdrv/")) and installed it with no problems. YAY, I can now use a controller!

So, here's where my question comes in: is there a way to create an executable from a shell script and have it available on the desktop as an icon? The reason I ask is because here's the script:

```
#!/bin/sh

exec sudo xboxdrv --silent \
  --detach-kernel-driver \
  -- \
  zsnes

# EOF #
```

I've ran this in the terminal and works flawlessly (after running xboxdrv it automatically opens ZSNES), but I want it so [once it's an executable] the terminal window doesn't pop open and have just ZSNES open.

Can anyone help me with this? Thank you so much!

---

### Post by ecosvaldo on 2011-08-28
Can anyone help me?

---

