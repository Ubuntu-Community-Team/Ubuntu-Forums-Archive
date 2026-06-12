---
title: "Updates broke Ubuntu 9.10 AGAIN!"
date: 2010-03-20
forum: General Help
---

### Post by PoopyTheJ on 2010-03-20
I just downloaded the most recent version of the updates for Ubuntu 9.10 and for the 4th or 5th time since I've used 9.10 it's broken 9.10 so I can't boot. Usually after breaking it it just hangs at the screen between the big white ubuntu O and the next with the progress bar, this time after the big white O I get random multicolored characters at the top of the screen and the computer hangs with no activity, no hdd lights or anything. Unless anyone has any suggestions I'm just not going to use Ubuntu, at least until 10.04 is available this is really getting old.

---

### Post by Ozymandias_117 on 2010-03-21
Yeah, they fudged 9.10 :(. Anyway, to your problem. I had something similar, had to boot to recovery mode and had to move my xorg.conf so it would automatically remake it, when I then rebooted, it worked.

(In case you don't know)
```
mv /etc/X11/xorg.conf ~/Desktop
```

---

### Post by 98cwitr on 2010-03-21
sudo update-manager -d

10.04 is available...do it.

---

### Post by Ozymandias_117 on 2010-03-21
> **98cwitr said:**
> sudo update-manager -d

10.04 is available...do it.

Don't do that. They highly recommend you download the .iso now that they are in beta. (Apparently enough packages have changed you will end up with a Frankenstein machine if you try to just update to it).

---

### Post by 98cwitr on 2010-03-21
i have a custom built machine...no problems here. I understand that it might not be the same for everyone...but that's why I imaged my machine last night ;)

---

### Post by 3rdalbum on 2010-03-21
You know, if you have any graphics drivers that you have manually installed (for instance, you downloaded the Nvidia or ATI drivers from the manufactuer's website), you need to reinstall them **after every kernel upgrade** and after some Xorg upgrades. Which is why you should be using Ubuntu's Hardware Drivers program to install graphics drivers, or at least use a PPA that will keep the driver in sync with the kernel.

---

### Post by PoopyTheJ on 2010-03-21
> **3rdalbum said:**
> You know, if you have any graphics drivers that you have manually installed (for instance, you downloaded the Nvidia or ATI drivers from the manufactuer's website), you need to reinstall them **after every kernel upgrade** and after some Xorg upgrades. Which is why you should be using Ubuntu's Hardware Drivers program to install graphics drivers, or at least use a PPA that will keep the driver in sync with the kernel.

I install new drivers as they are released from ATI. Can you explain how I can use a PPA to get the newest drivers and keep them in sync with the kernel? I've never done anything like that before, just used the install packages from ATI.

---

### Post by PoopyTheJ on 2010-03-21
> **Ozymandias_117 said:**
> Yeah, they fudged 9.10 :(. Anyway, to your problem. I had something similar, had to boot to recovery mode and had to move my xorg.conf so it would automatically remake it, when I then rebooted, it worked.

(In case you don't know)
```
mv /etc/X11/xorg.conf ~/Desktop
```

Thanks that fixed it!

---

### Post by soltanis on 2010-03-22
> **3rdalbum said:**
> You know, if you have any graphics drivers that you have manually installed (for instance, you downloaded the Nvidia or ATI drivers from the manufactuer's website), you need to reinstall them **after every kernel upgrade** and after some Xorg upgrades. Which is why you should be using Ubuntu's Hardware Drivers program to install graphics drivers, or at least use a PPA that will keep the driver in sync with the kernel.

This advice generally holds true, although the Hardware Driver's program never works in this regard. After any upgrade that includes a kernel update, you should disable the proprietary driver, reboot, update it, then reboot again.

For me this is the only solution. Under Fedora I used akmod-nvidia, but I have no idea if this works in Ubuntu.

---

