---
title: "Flash videos (such as youtube) won't play."
date: 2009-10-28
forum: General Help
---

### Post by Chaos Punk on 2009-10-28
Searched around, but couldn't find my particular issue. After installing all packages for flash, no videos will actually play. There's just a giant play button over the flash app and when you click it, it'll either glitch out and never play or just not do anything. This has happened on my Ubuntu desktop (which is what I'm on now) and my Debian laptop. Any suggestions?

---

### Post by fancypiper on 2009-10-28
Try removing gnash if it is installed.

---

### Post by Chaos Punk on 2009-10-28
> **fancypiper said:**
> Try removing gnash if it is installed.
It's not installed, should I install it and see what happens?

---

### Post by masux594 on 2009-10-28
First of all you must know if you have the flash plugin installed.. So, type "[about:plugins](about:plugins)" in your browser and see what kind of flash plugin have u currently installed ..

Sysc, A

---

### Post by Chaos Punk on 2009-10-28
> **masux594 said:**
> First of all you must know if you have the flash plugin installed.. So, type "[about:plugins]("http://about%3Cb%3E%3C/b%3E:plugins")" in your browser and see what kind of flash plugin have u currently installed ..

Sysc, A
This is what it says for flash.

**Shockwave Flash**

 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Adobe Flash movie swf Yes   application/futuresplash FutureSplash movie spl Yes

---

### Post by masux594 on 2009-10-28
Oki, then..```
sudo apt-get remove swfdec-gnome swfdec-mozilla
```close firefox, reopen it, and then see in [about:plugins](about:plugins) that there's no flash info o plugin installed.. Then, close FF```
sudo apt-get install flashplugin-installer flashplugin-nonfree
``` and reopen it, look at [about:plugins](about:plugins) if the plugin is installed and check in youtube for a flash videos..

Sysc, A

---

### Post by Chaos Punk on 2009-10-28
> **masux594 said:**
> Oki, then..```
sudo apt-get remove swfdec-gnome swfdec-mozilla
```close firefox, reopen it, and then see in [about:plugins]("http://about%3Cb%3E%3C/b%3E:plugins") that there's no flash info o plugin installed.. Then, close FF```
sudo apt-get install flashplugin-installer flashplugin-nonfree
``` and reopen it, look at [about:plugins]("http://about%3Cb%3E%3C/b%3E:plugins") if the plugin is installed and check in youtube for a flash videos..

Sysc, A
Oh my god that did it. Thank you, you frickin' rule.

EDIT: Wait, hold the phone, there's no audio. I can play music in RythmBox though, just not videos.

EDIT: Nevermind, I got it, it was my fault.:p

---

### Post by masux594 on 2009-10-28
I don't understand, the problem is in firefox or in RythmBox ??

Sysc, A

---

### Post by masux594 on 2009-10-28
Another question.. Does ```
sudo apt-get remove swfdec-gnome swfdec-mozilla
``` remove something else that is not these two packages?

Sysc, A

---

### Post by Chaos Punk on 2009-10-28
> **masux594 said:**
> I don't understand, the problem is in firefox or in RythmBox ??

Sysc, A
Nevermind, I just had my Ubuntu sound settings all f'ed up#-o, I fixed it though, thanks for your help.\\:D/

---

### Post by masux594 on 2009-10-28
Nevermind.. In facts looks strange =)

Sysc, A

---

### Post by lovinglinux on 2009-10-28
For future reference, this issue and solution are described in **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

