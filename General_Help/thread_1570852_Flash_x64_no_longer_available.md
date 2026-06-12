---
title: "Flash x64 no longer available"
date: 2010-09-08
forum: General Help
---

### Post by cra1g321 on 2010-09-08
i noticed after adding the flashplugin-x64 ppa from ubuntu tweak, when im in the synaptic package manager and go to install it, it appears to be installed but when i check the terminal log i see that it fails to download the plugin. I know that flash x64 has temporally been halted by macromedia
 i have tried using nspluginwrapper and the 32bit flash version but with certain videos im unable to use the controls. 

I was wanting to know where i could get the latest x64 flashplugin ?? that was made before macromedia stopped creating them.

[[IMG]http://omploader.org/tNWhrZQ[/IMG]]("http://omploader.org/vNWhrZQ")

---

### Post by sandyd on 2010-09-08
> **cra1g321 said:**
> i noticed after adding the flashplugin-x64 ppa from ubuntu tweak, when im in the synaptic package manager and go to install it, it appears to be installed but when i check the terminal log i see that it fails to download the plugin. I know that flash x64 has temporally been halted by macromedia
 i have tried using nspluginwrapper and the 32bit flash version but with certain videos im unable to use the controls. 

I was wanting to know where i could get the latest x64 flashplugin ?? that was made before macromedia stopped creating them.

[[IMG]http://omploader.org/tNWhrZQ[/IMG]]("http://omploader.org/vNWhrZQ")
I anticipated adobe's removing of the file altogether, and I have it in my dropbox acct.
brb.

---

### Post by sandyd on 2010-09-08
[http://dl.dropbox.com/u/3593659/adobe_flash/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://dl.dropbox.com/u/3593659/adobe_flash/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

---

### Post by cra1g321 on 2010-09-08
thnx. i was checking out your website while you got the dropbox link :)

---

### Post by howefield on 2010-09-08
> **cra1g321 said:**
> i have tried using nspluginwrapper and the 32bit flash version but with certain videos im unable to use the controls.

Before you go using an unsupported version of flash which has a security issue, you might try sorting out the controls by typing this into a terminal

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
``` 

and placing this on a new line before the last line. Then save and try your flash again.

```
export GDK_NATIVE_WINDOWS=1
```

Just giving you an alternative option.

---

### Post by cra1g321 on 2010-09-08
> **howefield said:**
> Before you go using an unsupported version of flash which has a security issue, you might try sorting out the controls by typing this into a terminal

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```and placing this on a new line before the last line. Then save and try your flash again.

```
export GDK_NATIVE_WINDOWS=1
```Just giving you an alternative option.

tried it but didnt make a difference. Thnx 4 helping anyway

---

### Post by Brunellus on 2010-09-08
Thread moved to an appropriate support forum.

---

### Post by wojox on 2010-09-08
Have a look here [Flash Issues & Solutions]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html")

---

### Post by cra1g321 on 2010-09-09
> **howefield said:**
> Before you go using an unsupported version of flash which has a security issue, you might try sorting out the controls by typing this into a terminal

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```and placing this on a new line before the last line. Then save and try your flash again.

```
export GDK_NATIVE_WINDOWS=1
```Just giving you an alternative option.

Hey sorry guys, turned out this has worked. the 1st time i tried it i added the line after the last line rather than before. Sorry 4 wasting ppls time :sad:

thnx 4 the link wojox ! :)

---

