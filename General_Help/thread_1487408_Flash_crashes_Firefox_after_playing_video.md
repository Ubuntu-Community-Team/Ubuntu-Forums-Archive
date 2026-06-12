---
title: "Flash crashes Firefox after playing video?"
date: 2010-05-19
forum: General Help
---

### Post by ghostandmachine on 2010-05-19
Upgrade from Hardy to Lucid.

Installed Adobe flash plugin 10.

Firefox crashes after playing flash video.

```

LoadPlugin: failed to initialize shared library /home/eric/.mozilla/plugins/libnpfbook_1_0_3.so [/home/eric/.mozilla/plugins/libnpfbook_1_0_3.so: undefined symbol: idna_strerror]

```

I just find it strange that the browser would crash after playing the video.

Any help would be great. Sorry if this is in the wrong forum.

thanks in advance.

---

### Post by wojox on 2010-05-19
Well at least you got to watch the video. :)

Did you completely uninstall the older version first? try looking here [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by ghostandmachine on 2010-05-19
> **wojox said:**
> Well at least you got to watch the video. :)

Did you completely uninstall the older version first? try looking here [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

I have but I went through it again just to be sure.

Every file was already removed and the flashplugin-nonfree was at it's latest release.

Thanks though.

---

### Post by lovinglinux on 2010-05-19
I don't use Facebook, but looks like your problem is caused by the Facebook plugin. I have no idea what it is, but the file is **/home/eric/.mozilla/plugins/libnpfbook_1_0_3.so**. Delete it and it should stop crashing Firefox. You might need to remove some Facebook extension too, if this was the way you got that plugin file.

---

### Post by ghostandmachine on 2010-05-19
> **lovinglinux said:**
> I don't use Facebook, but looks like your problem is caused by the Facebook plugin. I have no idea what it is, but the file is **/home/eric/.mozilla/plugins/libnpfbook_1_0_3.so**. Delete it and it should stop crashing Firefox. You might need to remove some Facebook extension too, if this was the way you got that plugin file.

I've deleted the "libnpfbook" but firefox still crashes after playing a video. Now, when I run it from the terminal, I don't get an error at all.

It's a fresh install and I haven't installed any facebook plugin.

---

### Post by lovinglinux on 2010-05-19
> **ghostandmachine said:**
> I've deleted the "libnpfbook" but firefox still crashes after playing a video. Now, when I run it from the terminal, I don't get an error at all.

It's a fresh install and I haven't installed any facebook plugin.

Does it crash when you try to watch any video or just a particular one? Can you provide a link? Your system is 32bit or 64bit?

---

### Post by ghostandmachine on 2010-05-23
> **lovinglinux said:**
> Does it crash when you try to watch any video or just a particular one? Can you provide a link? Your system is 32bit or 64bit?

It's any video: youtube, myspace, vimeo.

I have a 32bit system

---

### Post by lovinglinux on 2010-05-23
You could try Firefox 3.6.5pre from ubuntu-mozilla-daily, which has plugin isolation. See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

