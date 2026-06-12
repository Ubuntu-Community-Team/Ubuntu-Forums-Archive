---
title: "Flash 10.2 beta on 10.10 Maverick (Chrome)"
date: 2010-12-15
forum: General Help
---

### Post by davidstoll on 2010-12-15
I followed the instructions (the same on many sites) for installing the new hardware accelerated flash 10.2 beta.  However, when I go to a web site to check the version, it still says I have 10.1 in Chrome.  However, Firefox says I have 10.2.

I don't want to use FF.  I only downloaded it to see if I was doing things correctly.

```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p2_32bit_linux_111710.tar.gz
tar zxvf flashplayer10_2_p2_32bit_linux_111710.tar.gz
sudo cp libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.so
```

[http://www.playerversion.com/](http://www.playerversion.com/)
or
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

Can anyone help me?

---

### Post by Foxcow on 2010-12-15
To figure out what version of the plugin you have, type "about:plugins" in any browser and hit enter.  It will tell you what plugins you have installed and their versions.


Also, if you are running a 64-bit system, the version of flash you want is not available yet.


edit: does that flashplugin-installer wrap the 32-bit version for use on a 64-bit machine?

---

### Post by Linye on 2010-12-16
I read somewhere that because Chrome has flash built in it can't be changed.

Someone could verify this.

---

### Post by davidstoll on 2010-12-16
> **Foxcow said:**
> To figure out what version of the plugin you have, type "about:plugins" in any browser and hit enter.  It will tell you what plugins you have installed and their versions.


Also, if you are running a 64-bit system, the version of flash you want is not available yet.


edit: does that flashplugin-installer wrap the 32-bit version for use on a 64-bit machine?

Yes, that is another way to check.  I have 10.1.

---

### Post by davidstoll on 2010-12-16
> **Linye said:**
> I read somewhere that because Chrome has flash built in it can't be changed.

Someone could verify this.

This web site seems to have a procedure specifically for Chrome.  However, if I follow the step for disabling the "built in" flash, then flash doesn't work at all.

[http://ubuntuguide.net/try-adobe-flash-player-10-2-beta-in-ubuntu-linux](http://ubuntuguide.net/try-adobe-flash-player-10-2-beta-in-ubuntu-linux)

---

### Post by wojox on 2010-12-16
Run it from the terminal and see what it says:

```
chromium-browser -- enable-plugins
```

---

### Post by davidstoll on 2010-12-17
OK, I figured it out.

When you type about:plugins into the web browser, I can see the Shockwave flash player.  It says it's version 10.1...no sign of 10.2.  If I click disable, then flash doesn't work at all.

Here's the trick.  In the about:plugins screen, over on the right, click on "+ details".

NOW, you can see both version 10.1 and 10.2.  NOW, you can just disable 10.1 and leave 10.2 enabled.

---

