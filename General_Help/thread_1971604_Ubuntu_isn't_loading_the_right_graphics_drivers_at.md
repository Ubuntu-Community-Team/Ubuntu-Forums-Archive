---
title: "Ubuntu isn't loading the right graphics drivers at boot"
date: 2012-05-02
forum: General Help
---

### Post by Thelinuxgeek on 2012-05-02
Just did a fresh install of Ubuntu 12.04. In order to run the live disc, I had to specify NOMODESET because there's an issue with the drivers for my graphics card. (Nvidia Geforce GTX 550 TI) Now that Ubuntu is installed, I'm having the same problem. When I try to boot up, the screen turns purple. And that's it. I can hear the little drum-like sound effect that plays when you go to the login screen, but the screen stays purple. I have to open the GRUB loader and specify NOMODESET so I can at least get a picture on the screen.

I downloaded and installed the drivers from [http://www.nvidia.com](http://www.nvidia.com) hoping that would resolve the issue, but it doesn't. I'm thinking that the default open source drivers are still being loaded somehow.

I'm having to specify NOMODESET on every boot up, and that loads very basic display drivers with no 3D suuport.

---

### Post by Thelinuxgeek on 2012-05-02
LOL! My first replies are from a freaking spam bot?



Ha. The little bugger got his account removed.

---

### Post by i22yb on 2012-05-26
Same problem here.  Gonna run some updates & see what I can do to fix it.  Will report back if I find a solution.  Pretty sad this is happening on an LTS version!  Had similar problems on Linux Mint lately.

---

