---
title: "Custom Resolution?"
date: 2010-01-29
forum: General Help
---

### Post by Cuzit on 2010-01-29
Video Card: Nvidia GForce 9600 (1GB)
Ubuntu 9.10

My setup is dual-monitor, the smaller of which works fine, but the bigger (and my main) doesn't.  It's a 60" Mitsubishi 737 Series 1080P HDTV, of which overscans the image pretty bad on PC input (I've looked, there's no 1:1 support, unless I have massively overlooked something).

I haven't used Ubuntu on the rig I'm connecting to this TV because it's mainly a gaming rig.  When I connected it, in Windows all I had to do was go into the NVidia driver's settings and drag the corners of the screen until they fit, thus fixing the problem with the TV overscanning.

I have found no such support in the linux driver.  The settings only has standard resolutions, and when I clicked Advanced and try to modify them, upon clicking out the box they instantaneously revert back into 1920x1080.

I also tried editing my xorg.conf file BUT I'm not entirely sure I did it correctly.  If I did, it had no effect.

Any help?  If I should post my xorg.conf file, let me know; I'll post it ASAP.  I'm going to reinstall because, being the numbskull that I am, I wasn't thinking and partitioned my HDD in a way I do not want.  When I get everything set up again and my drivers installed, I'll post the file.

Thanks in advance, sorry for the long post.

---

### Post by Raian the Fallen on 2010-01-31
Check [this]("https://wiki.ubuntu.com/X/Config/Resolution") out.

---

### Post by rogue_0111 on 2010-01-31
--
I use "[COLOR=DarkRed][COLOR=Black]lxrandr". Easy to use and you can set resolution of any secondary video connection.

Install via terminal:

apt-get install lxrandr

--
[/COLOR][/COLOR]

---

