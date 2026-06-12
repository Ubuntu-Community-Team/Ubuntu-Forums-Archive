---
title: "Wrong Nvidia Driver, Ubuntu won't boot"
date: 2011-09-20
forum: General Help
---

### Post by User3k on 2011-09-20
I installed Ubuntu 11.04 i386 from the alternate cd. I got everything set up perfectly, except for the Nvidia drivers. I installed the wrong one. I needed to install the one for Geforce4 440 MX, which should have been the nvidia-96 (I believe,) instead I installed the latest driver. So now it won't boot, I can't even get it to boot into recovery.

So How can I fix this? I tried a couple of livecd's and thought I could edit /etc/X11/xorg.conf but that is no where to be found. I looked in /usr/share and /usr/lib (or local? Well two alternate places a google search told me to look.) and still couldn't find it in the X11 folder.

So now I am stuck. I need to get this laptop back soon and would rather fix this then reinstall.

Also: I removed nouveau drivers. The plan was to remove it, then install the CORRECT nvidia drivers, reboot and all worked out well like it always does.


Edit: Just put the install cd in. Saw a "Rescue Broken System" I am giving that a try, or attempting to.

---

### Post by User3k on 2011-09-20
I love it when I answer my own post.

I used the install cd, rescue broken system. It eventually asked me where the root was and then dropped me down to a shell. I apt-get --purge remove nvidia and it boots fine now.

---

