---
title: "flash not working properly in firefox"
date: 2009-11-12
forum: General Help
---

### Post by winchendonsprings on 2009-11-12
I can view anything flash online, but i cannot interact with it. For example, When I'm on Hulu, I can see the video, but I cannot use any buttons on the player(fullscreen, volume, play/pause, etc.). 

I have reinstalled the flash plugin from synaptic and I'm still having the same results. Is there something that needs to accompany the flash plugin?

This has only happened since upgrading to 9.10

---

### Post by phillw on 2009-11-12
> **winchendonsprings said:**
> I can view anything flash online, but i cannot interact with it. For example, When I'm on Hulu, I can see the video, but I cannot use any buttons on the player(fullscreen, volume, play/pause, etc.). 

I have reinstalled the flash plugin from synaptic and I'm still having the same results. Is there something that needs to accompany the flash plugin?

This has only happened since upgrading to 9.10

For things Firefox, head over here -->   [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Regards,

Phill.

---

### Post by winchendonsprings on 2009-11-13
I made a new discovery. For a split second after clearing the browsers history and then restarting it, I can use the controls. Only for a split second then I cannot use them again.

Also when my mouse is over a button it will highlight, but clicking will do nothing.

Any ideas?

---

### Post by sephora on 2009-11-13
Hi, I Found a Solution, hope it works for you

1)  Uninstall from synaptic 
"flashplugin-installer" and/or  "flashplugin-nonfree"

2) Get the flash player from Adobe (64 bits) following this link [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

3) Extract the file "libflashplayer.so"

4) Using the terminal, update and also get the following packages

sudo aptitude update


sudo aptitude install nspluginwrapper


5) Copy "libflashplayer.so" to the folder /usr/lib/mozilla/plugins/

cp libflashplayer.so /usr/lib/mozilla/plugins/


6) Emulate the plugin with nspluginwrapper

sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

If you get an error message, don't worry, it worked for me anyway

7) Finally you have to  link the plugin in order that your browser can find it

sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/firefox/plugins/


sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/


8) restart mozilla

I got this from this page, I hope I translated it properly...

[http://www.taringa.net/posts/linux/3805989/Solucion-controles-flash-en-Ubuntu-9_10-64-bits-funciona.html](http://www.taringa.net/posts/linux/3805989/Solucion-controles-flash-en-Ubuntu-9_10-64-bits-funciona.html)

---

### Post by wojox on 2009-11-13
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567") Scroll down to Flash.

---

### Post by jimmy the saint on 2009-11-13
> So here the bug and workarounds.

For example on youtube, whilst it recognises my mouse moving over various buttons, actual mouse clicks are not recognised. I can navigate using 'tab' but this is very painful. I can also right click. The problem doesn't occur with other flash players, e.g. swfdec-mozilla.

WORKAROUND 1: Disable compiz
WORKAROUND 2: Remove flashplugin-nonfree / flashplugin-installer and install from adobe
WORKAROUND 3: Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

Note: The only workaround for Chrome/Chromium users is to disable compiz.

These workaround's have been verified to work for some users. We don't need verification of whether or not they work for you.

the third seems extremely easy to me.

---

### Post by winchendonsprings on 2009-11-13
You solved it. This did it -

Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

Thats it.

I opted for this option because it was so simple. It made flash work perfect.

Before I had done this flash was acting very strange. For example on the Hulu site, if i clicked the fullscreen button roughly 1,000,000 times, it would go to fullscreen.(or the pause, mute or any of the flash buttons). Clearing all the history and reopening the browser seemed to have no effect on this. It was completely random.

Thanks a lot.

Im on 64bit 9.10 with firefox 3.5.5
also this issue was not effecting youtube videos

---

