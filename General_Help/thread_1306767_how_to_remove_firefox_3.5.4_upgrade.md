---
title: "how to remove firefox 3.5.4 upgrade"
date: 2009-10-30
forum: General Help
---

### Post by Crash~Override on 2009-10-30
Hey guys. So i need some help removing the firefox 3.5.4 update. Yesterday I installed ubuntu 9.10 64 bit and it came with firefox 3.5.3 and i was able to add flash player plugin. But today after i manually upgraded to firefox 3.5.4 my flash player has stopped working. I tried to remove firefox completely for a reinstall but for some reason i just cannot remove firefox thoroughly from ubuntu. 

So I guess my only option would be to downgrade to 3.5.3 but I have no clue how to do that. Please someone help me because i really need flash player back. Either kindly help me get flash working on firefox 3.5.4 or help me downgrade to 3.5.3 firefox

PS: I upgraded to 3.5.4 using the guide here [http://jaxov.com/2009/10/upgrade-install-firefox-3-5-4-in-ubuntu-linux/](http://jaxov.com/2009/10/upgrade-install-firefox-3-5-4-in-ubuntu-linux/)

---

### Post by lavinog on 2009-10-30
```
sudo aptitude reinstall firefox-3.5
```

How did you install flash player?

---

### Post by Crash~Override on 2009-10-30
> **lavinog said:**
> ```
sudo aptitude reinstall firefox-3.5
```How did you install flash player?

no doesn't work...and yes i tried reinstalling flash player but it still doesn't help.

Reinstalling firefox just brings me back to 3.5.4 which apparently doesn't seem to support 64bit flash player. The original 3.5.3 worked perfectly with 64bit flash

---

### Post by lavinog on 2009-10-30
what does the following say:
```

aptitude show firefox-3.5

```

---

### Post by shaggy999 on 2009-10-30
Flashplayer broke for me as well and this is what I had to do:

> 
sudo apt-get --purge autoremove flashplugin-nonfree
sudo apt-get install flashplugin-installer


---

### Post by Crash~Override on 2009-10-30
> **lavinog said:**
> what does the following say:
```

aptitude show firefox-3.5

```

this is what it shows for me
```
Package: firefox-3.5
State: installed
Automatically installed: yes
Version: 3.5.3+build1+nobinonly-0ubuntu6
Priority: optional
Section: web
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Uncompressed Size: 3,793k
Depends: fontconfig, psmisc, debianutils (>= 1.16), xulrunner-1.9.1 (>= 1.9.1),
         libasound2 (> 1.0.18), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4),
         libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>=
         2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>=
         2.10), libnspr4-0d (>= 4.7.3-0ubuntu1~), libpango1.0-0 (>= 1.14.0),
         libstdc++6 (>= 4.1.1), firefox-3.5-branding | abrowser-3.5-branding
Recommends: ubufox
Suggests: firefox-3.5-gnome-support (= 3.5.3+build1+nobinonly-0ubuntu6),
          latex-xft-fonts, libthai0
Conflicts: firefox-3.0 (< 3.1~), firefox-3.0-dom-inspector (< 3.1~),
           firefox-3.0-venkman (< 3.1~), firefox-3.1 (< 3.1~b4~hg20090317),
           firefox-dom-inspector (< 3.1~)
Replaces: firefox-3.0 (< 3.1~), firefox-3.0-dom-inspector (< 3.1~),
          firefox-3.0-venkman (< 3.1~), firefox-3.1, firefox-dom-inspector (<
          3.1~)
Provides: firefox-3.0, firefox-3.0-dom-inspector, firefox-3.0-venkman,
          firefox-3.1, firefox-dom-inspector, www-browser
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface, enhanced
 security features including protection from online identity theft, and
 integrated search let you get the most out of the web.

```

---

### Post by lavinog on 2009-10-30
What is telling you that 3.5.4 is installed?

How did you install 64bit flash?

---

### Post by Crash~Override on 2009-10-30
> **lavinog said:**
> What is telling you that 3.5.4 is installed?

How did you install 64bit flash?

if i go in firefox help>about firefox
it shows verstion 3.5.4

And i installed 64bit flash by creating a plugin directory in .mozilla folder and copying the flash plugin from adobe ```
http://labs.adobe.com/downloads/flashplayer10.html
```

everything was working fine until i upgraded to 3.5.4

---

### Post by lavinog on 2009-10-30
make sure you uninstall all flash packages from synaptic and do not reinstall them.

what does this report?
```
whereis firefox
```

---

### Post by Crash~Override on 2009-10-30
> **lavinog said:**
> make sure you uninstall all flash packages from synaptic and do not reinstall them.

what does this report?
```
whereis firefox
```

it reports the following:
```
firefox: /usr/bin/firefox /usr/bin/firefox.ubuntu /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox

```

---

### Post by lavinog on 2009-10-31
does running firefox.ubuntu launch firefox, if so what version.

---

### Post by Crash~Override on 2009-10-31
> **lavinog said:**
> does running firefox.ubuntu launch firefox, if so what version.

no that doesn't launch firefox at all
```
firefox.ubuntu: command not found
```

---

### Post by shaggy999 on 2009-11-01
I wanted to come back and mention that an update to firefox on karmic got rolled out last night (or maybe it was this morning) and it broke flash *again*. I had to use the same fix I mentioned above to get it going again.

---

### Post by jmiter on 2009-11-03
Here is how I removed Firefox 3.5.4 and rolled back to Firefox 3.5.3.  Flash is working fine now - no problems, crashes, etc.


1. I removed Firefox 3.5.4:

```
sudo apt-get remove firefox-3.5
```

2. Went to /var/cache/apt/archives and listed the firefoxes I had

```
ls -l *fire*
```

3. I had both the 3.5.3 and 3.5.4.   I installed all of the 3.5.3 packages.

```
sudo dpkg -i firefox-3.5-branding_3.5.3+build1+nobinonly-0ubuntu6_amd64.deb firefox_3.5.3+build1+nobinonly-0ubuntu6_all.deb firefox-3.5_3.5.3+build1+nobinonly-0ubuntu6_amd64.deb
```

4. Restarted firefox - everything works, no crash with the use of flash.

Good luck

---

### Post by lavinog on 2009-11-03
3.5.4 is the current version in the repositories, you may want to try and install that.

For future reference you should avoid manually installing firefox, unless you want to break your system.

---

### Post by slick_nick on 2009-11-04
Thought I would chime in, I'm on a fresh install of Karmic (64bit), and flash in my FF 3.5.4 is at least half broken as well. I have installed Flash both through the Ubuntu Software Center and from FF's "a plugin is needed to display missing content" prompt.
Flash will work occasionally and randomly; it used to be that if a Flash app crashed, I could simply reload the page, but now I have to restart my browser. Not acceptable! I will try some of these fixes.

EDIT: Thanks shaggy999, this fix worked for me!

> **shaggy999 said:**
> Flashplayer broke for me as well and this is what I had to do:
Quote:
sudo apt-get --purge autoremove flashplugin-nonfree
sudo apt-get install flashplugin-installer 


The first command didn't work for me, but after I uninstalled Flash through the Ubuntu Software Center, I installed it using the second command and it seems to be fixed! I have three different pages with Flash content open and they are all working fine.

---

### Post by slick_nick on 2009-11-05
I partially rescind my previous statement, Flash is working *better* but not nearly perfect, maybe not even as well as it used to in previous versions. Bah. Hopefully it gets updated/fixed soon!

---

### Post by lavinog on 2009-11-05
> **slick_nick said:**
> I partially rescind my previous statement, Flash is working *better* but not nearly perfect, maybe not even as well as it used to in previous versions. Bah. Hopefully it gets updated/fixed soon!

I feel that the 64bit flash is even better than the 32bit one offered in the 64bit repos.

---

### Post by slick_nick on 2009-11-05
Okay finally, fixed, at least for this 64bit user!

First I followed the instructions under "Flash 10" on [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) to remove installed Flash stuff:
> sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

Then it was as simple as downloading libflashplayer.so from Adobe and copying libflashplayer.so to ~/.mozilla/plugins!
 [http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

---

