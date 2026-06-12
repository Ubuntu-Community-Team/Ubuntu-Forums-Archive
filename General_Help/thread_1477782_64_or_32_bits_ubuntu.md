---
title: "64 or 32 bits ubuntu"
date: 2010-05-09
forum: General Help
---

### Post by gwu777 on 2010-05-09
Hi there,

Here is a general wandering. I have ubuntu-amd-64 installed, it works fine, I just have some issues with flash. For the sake of testing, would I gain to install on an other partition the 32bits version? Will I notice any difference and will flash work better?

Thank you for your opinion.

On my current installation, I can view most flash animation and video, but I usually have no access to the option, for exemple I cannot make videos fullscreen on youtube or rewind...

---

### Post by dcstar on 2010-05-09
> **gwu777 said:**
> Hi there,

Here is a general wandering. I have ubuntu-amd-64 installed, it works fine, I just have some issues with flash. For the sake of testing, would I gain to install on an other partition the 32bits version? Will I notice any difference and will flash work better?

Thank you for your opinion.

On my current installation, I can view most flash animation and video, but I usually have no access to the option, for exemple I cannot make videos fullscreen on youtube or rewind...

There must be hundreds of posts now on installing the 64-bit flash from Adobe, have you looked at any of them?

---

### Post by mscout2004 on 2010-05-09
the standard 32 flash works better straight out of the box but there is a 64bit tested version of flash that I installed on mine and I have no issues with flash anymore.

---

### Post by mscout2004 on 2010-05-09
Try this    [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by gwu777 on 2010-05-09
> **dcstar said:**
> There must be hundreds of posts now on installing the 64-bit flash from Adobe, have you looked at any of them?

I have looked in the forum!!! There are indeed many options, I have followed some threads and the best result I have is the one auoted above!!! however that was already 6 month ago, so maybe I am going to try some of the above in the near future on my current installation.

My main question is whether there is a real gain to have the 64bits rather than installing a 32bits ubuntu version on my laptop.

Thank you for your input

---

### Post by gwu777 on 2010-09-16
To close this topic. I now have flash32 running on Ubuntu 64, with the following workaround to get my mouse button working correctly:
> [bcschmerker]("http://ubuntuforums.org/member.php?u=609186"), your issue sounds like "[Adobe Flash  Player does not respond to mouse clicks]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/410407")".  It is an issue with the emulation of flash due to lack of a native  64-bit plugin. There are a couple of work arounds, described at the  beginning of the bug report, that sometimes work.

Workaround 3, which solved the problem for me, is to open a terminal and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
Before the last line of text enter the following:
export GDK_NATIVE_WINDOWS=1

Yesterday, I tried to install flash64 from the adobe website, bit the package had disapeared from their repository, so I ended up using ubuntu-restricted-extras. today, there is a new pluggin on their lab, flash-square, I know it is early as it came out yesterday, but any feedback and comparative with the flash pluggin in restricted extras. As I have flash working OK, I do not want to mess it up...

---

### Post by gwu777 on 2010-09-16
> **gwu777 said:**
> I know it is early as it came out yesterday, but any feedback and comparative with the flash pluggin in restricted extras. As I have flash working OK, I do not want to mess it up...

Flash-square 64 resolve all the problem! I first uninstalled all my previous flash installation as per various tutorial:
```
sudo apt-get autoremove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```

```
sudo rm -f /usr/lib/mozilla/plugins/*flash*  
sudo rm -f ~/.mozilla/plugins/*flash*  
sudo rm -f /usr/lib/firefox/plugins/*flash*  
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*  
sudo rm -rfd /usr/lib/nspluginwrapper
```

Downloaded and installed the pluggin from adobe lab:
[Flash Square Player]("http://labs.adobe.com/downloads/flashplayer10.html")

Unpack it and copy it in the mozilla pluggin folder:
```
cp libflashplayer.so ~/.mozilla/plugins
```

Works much better than ever before - Great!

---

### Post by oldos2er on 2010-09-16
> **gwu777 said:**
>  today, there is a new pluggin on their lab, flash-square, I know it is early as it came out yesterday, but any feedback and comparative with the flash pluggin in restricted extras.

The restricted-extras version seems doomed to always be 32-bit + nspluginwrapper. The new "Square" plugin is 64-bit and is working fine for me so far (just installed it this morning).

---

### Post by gwu777 on 2010-09-18
> **oldos2er said:**
> The restricted-extras version seems doomed to always be 32-bit + nspluginwrapper. The new "Square" plugin is 64-bit and is working fine for me so far (just installed it this morning).

Considering the square version came out 3 days ago, and that so far 64bit have been buggy, I would not condemn the restricted extras just yet. If this 64bit prove itself, I know that it will be probably included included in futur repo. Although it still has security and stability check to overcome.

So far for me it works perfectly and better than before. I am happy.

---

