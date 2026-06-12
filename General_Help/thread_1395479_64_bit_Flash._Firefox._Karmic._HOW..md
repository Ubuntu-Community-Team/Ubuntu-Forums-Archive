---
title: "64 bit Flash. Firefox. Karmic. HOW."
date: 2010-01-31
forum: General Help
---

### Post by Roasted on 2010-01-31
Yes. I've googled.
Yes. I've downloaded the libflashplayer.so file.
Yes. I've even put it in my .mozilla/plugins folder as directed.
And yes, it failed.

How do I install flash 64 bit on Linux?

---

### Post by audiomick on 2010-01-31
As far as I know,
```
apt-get install ubuntu-restricted-extras
```
should do it.

There is also this
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Roasted on 2010-01-31
> **audiomick said:**
> As far as I know,
```
apt-get install ubuntu-restricted-extras
```
should do it.

There is also this
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Pretty sure the restricted-extras just install the 32 bit flash with a wrapper to work with 64 bit.

I just found after posting this a fix for my flash problem. 

[http://ubuntuforums.org/showpost.php?p=8276784&postcount=6](http://ubuntuforums.org/showpost.php?p=8276784&postcount=6)

I wanted to install 64 bit flash because on some youtube videos I was unable to click on anything inside the flash video (fast forward, exit ads, etc). But what I pasted there above seemed to work.

However, I'm still very curious on why me putting the 64 bit libflashplayer.so file in .mozilla/plugins didn't work, even after restarting firefox as well as rebooting the whole PC...

---

### Post by hawthornso23 on 2010-01-31
> However, I'm still very curious on why me putting the 64 bit libflashplayer.so file in .mozilla/plugins didn't work, even after restarting firefox as well as rebooting the whole PC...

I don't think that is how you do it. Isn't there an installation script to run?

---

### Post by oldos2er on 2010-01-31
[http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html](http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html)

---

### Post by Roasted on 2010-01-31
> **hawthornso23 said:**
> I don't think that is how you do it. Isn't there an installation script to run?

That's what I was told to do in IRC.

And no, the installation script said it's not supported by my architecture (64 bit) yet I was downloading the 64 bit flash player.

Oh Adobe, how much you make me smile.

---

### Post by hawthornso23 on 2010-01-31
I installed it using this useful script which I got from ... somewhere I can't remember...

```

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz


```

---

### Post by hawthornso23 on 2010-01-31
> **Roasted said:**
> That's what I was told to do in IRC.

And no, the installation script said it's not supported by my architecture (64 bit) yet I was downloading the 64 bit flash player.

Oh Adobe, how much you make me smile.

Just checking - you do have 64 bit Karmic installed on your 64 bit architecture right? It won't work with 32 bit Karmic even if you do have a 64 bit processor.

---

### Post by audiomick on 2010-01-31
> **Roasted said:**
> ... because on some youtube videos I was unable to click on anything inside the flash video (fast forward, exit ads, etc).

Yes, I have had that myself lately. I think I might have to look into it.

Although I tend to just boycott sites that don't work properly.
Stubborn, I guess...;)

---

### Post by tom.swartz07 on 2010-01-31
> **audiomick said:**
> Yes, I have had that myself lately. I think I might have to look into it.

Although I tend to just boycott sites that don't work properly.
Stubborn, I guess...;)

Theres a link in my sig that shows the best method for x64 flash- Adobe released a new version of the 'beta' flash for linux- I have had 100% success with it, its never crashed on me yet! :D


Hope this helps

---

### Post by Roasted on 2010-01-31
> **hawthornso23 said:**
> Just checking - you do have 64 bit Karmic installed on your 64 bit architecture right? It won't work with 32 bit Karmic even if you do have a 64 bit processor.

Yep. Quad core 64 bit Intel CPU, Ubuntu 9.10 64 bit.

---

### Post by lovinglinux on 2010-02-01
> **Roasted said:**
> I wanted to install 64 bit flash because on some youtube videos I was unable to click on anything inside the flash video (fast forward, exit ads, etc). But what I pasted there above seemed to work.


See [http://ubuntuforums.org/showpost.php?p=8555261&postcount=2](http://ubuntuforums.org/showpost.php?p=8555261&postcount=2)

I installed 64bit that way and it works.

> **Roasted said:**
> However, I'm still very curious on why me putting the 64 bit libflashplayer.so file in .mozilla/plugins didn't work, even after restarting firefox as well as rebooting the whole PC...

I have noticed some bug once that I could fix by deleting the file pluginreg.dat from your FF profile. Then it recognized the plugin. Must close FF first.

---

### Post by darco on 2010-02-01
> **lovinglinux said:**
> See [http://ubuntuforums.org/showpost.php?p=8555261&postcount=2](http://ubuntuforums.org/showpost.php?p=8555261&postcount=2)

I installed 64bit that way and it works.



I have noticed some bug once that I could fix by deleting the file pluginreg.dat from your FF profile. Then it recognized the plugin. Most close FF first.

yes, that script works perfect. I have used it a few times. When a new version of flash comes out, you just have to edit the script to point to the new version. Its a keeper!

---

### Post by coldraven on 2010-02-01
Yes, read this
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)
Ran the script
and it works!:p

---

### Post by philinux on 2010-02-01
> **Roasted said:**
> Yes. I've googled.
Yes. I've downloaded the libflashplayer.so file.
Yes. I've even put it in my .mozilla/plugins folder as directed.
And yes, it failed.

How do I install flash 64 bit on Linux?

Thats all I did to get it to work, then restart firefox. Simple and easy method. And yes restricted extras install the 32 bit plugin.
I assume you downloaded this.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Have you checked you haven't got other instances of flash.

```
sudo updatedb

then

locate libflashplayer.so
```

Post back the result of the locate command.

---

### Post by audiomick on 2010-02-02
@ philinux
Excuse me for butting in.
Mine says
```
mick@ubuntu-desktop:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
```
Does that look right?

---

### Post by Leppie on 2010-02-02
> **coldraven said:**
> Yes, read this
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)
Ran the script
and it works!:p
+1, script works a charm

---

### Post by Leppie on 2010-02-02
> **audiomick said:**
> Does that look right?
is flash not working for you either?
mine looks like this:
```
$ ocate libflashplayer
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
```
but i used that script, so it's different for me. you seem to be using the flash installer.

---

### Post by lovinglinux on 2010-02-02
> **audiomick said:**
> @ philinux
Excuse me for butting in.
Mine says
```
mick@ubuntu-desktop:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
```
Does that look right?

If you are using 32bit Ubuntu, then yes. You have flashplugin-installer. Nevertheless, it looks to me that you have the 64bit wrapper too. So, if you are using 64bit Ubuntu and are experiencing problems, remove flashplugin-installer with this:

```
sudo apt-get remove flashplugin-installer
```

Then install the 64bit version following [this tutorial](http://ubuntuforums.org/showthread.php?t=1358591).

Do you have any problems with it?

> **Leppie said:**
> is flash not working for you either?
mine looks like this:
```
$ ocate libflashplayer
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
```
but i used that script, so it's different for me. you seem to be using the flash installer.

Mine looks exactly the same.

---

### Post by LuisGMarine on 2010-02-02
+1 for the script that is floating around.  However be warned that if you are quite the Hulu Junkie there are some problems with the  64-bit flash Linux and Hulu.  

At this point I have not looked into the matter to determine who is at fault, flash or hulu.  Just giving you the heads up to reduce problems, I too suffer the whole not being able to pause/play on flash videos, but I suck it up due to the fact I <3 watching hulu.

---

### Post by audiomick on 2010-02-02
> **Leppie said:**
> is flash not working for you either?

It works, but not 100%. I noticed that problem with the "transport controls" on you tube or somewhere like that not working, and ocassionally a site with too much whizz-bang just wont go.

I should try that script, I suppose, and get around to reading lovinlinux' firefox optimization thread all the way through...

for anyone who hasn't seen it:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

edit: Ran the script. Now the You tube transport controls work.
Maybe I'm dreaming, but I also have the impression that Firefox is generally just a wee bit snappier now.

---

### Post by Leppie on 2010-02-02
> **audiomick said:**
> Maybe I'm dreaming, but I also have the impression that Firefox is generally just a wee bit snappier now.
may wekk be, flash drains system resources. even more when not installed properly (or using chrome)

---

