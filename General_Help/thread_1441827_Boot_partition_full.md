---
title: "Boot partition full??"
date: 2010-03-29
forum: General Help
---

### Post by EmilyRose on 2010-03-29
So, I've been noticing the last few weeks that it seems to take longer and longer to boot up, and today I got a notice on startup that thers only 7 odd mb of free space in the /boot partition. There are a whole slew of files in there apon inspection at 3.7mb but I have no idea which ones are neccasary and which ones are worthless... how do I tell the difference? Mostly there either abi-2.6..28-xx or config-2.6.28-xx-generic or intrd.img-2.6.31-xx-generic or System.map-2.6.xx-xx-generic or vmlinuz-2.6.31-xx-generic ... is there an easy way to tell? 

LOTS of thanks in advance!!

---

### Post by drs305 on 2010-03-29
An easy way to clean out older kernels is to install and use Ubuntu-Tweak. You can add the repository and install it via the following commands. It is a GUI app that can identify and uninstall kernels not in use. Generally most people keep at least one older kernel.  

You can check the kernel currently in use with:
```
uname -r
```

To install Ubuntu-Tweak, go to [https://launchpad.net/ubuntu-tweak/+download]("https://launchpad.net/ubuntu-tweak/+download")

About half way down the page is the version for Jaunty. Download the file and click on it to install.

For Karmic and later, it's even easier, just run this command to add the repository and download:
```
sudo add-apt-repository ppa:tualatrix/ppa  && supo apt-get update && sudo apt-get install ubuntu&#8212;tweak
```

Once installed, you open it via Applications, System Tools, Ubuntu-Tweak.
Then select Package Cleaner, click on "Unlock" in lower right and enter password. Click on "Clean Kernels" from the far right pane and remove kernels lower than the number you are currently using. Again, you might want to keep one extra that you know works.

There is also a section in the following post on "Removing Older Kernels" if you would prefer to do it manually or want to learn more about what files you can remove:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by EmilyRose on 2010-03-29
Ahh ha! Thank you SO much!! I actually had Ubuntu Tweak already, having installed it ages ago... but never realized it could do that :p Thanks!!

---

