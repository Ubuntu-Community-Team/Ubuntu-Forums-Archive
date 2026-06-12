---
title: "unable to  play video in firefox"
date: 2010-01-05
forum: General Help
---

### Post by rudedcam on 2010-01-05
i have used this documentation with no success and i wonder why it is so hard? [https://help.ubuntu.com/7.04/internet/C/web-plugins.html]("https://help.ubuntu.com/7.04/internet/C/web-plugins.html") (i know it's for 7.04 but i couldn't find anything for 9.04)

can anybody help?

---

### Post by amsterdamharu on 2010-01-05
Follow these instructions:
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

It will install vlc player and the firefox plugins, vlc will play allmost anything you can throw at it.

---

### Post by Zoot7 on 2010-01-05
Bring up a terminal and type this:
```
sudo apt-get install ubuntu-restricted-extras
```

That'll install the flash plugin, the media codecs along with many other restricted bits and bobs.

---

### Post by lovinglinux on 2010-01-05
[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by rudedcam on 2010-01-05
thank you amsterdamharu, i've installed a couple of missing plugins

```
sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libdns45
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

still not working

---

### Post by lovinglinux on 2010-01-05
> **rudedcam said:**
> thank you amsterdamharu, i've installed a couple of missing plugins

still not working

What kind of video you are trying to watch? Have you followed the tutorial from my previous post?

---

### Post by rudedcam on 2010-01-05
> **lovinglinux said:**
> What kind of video you are trying to watch? Have you followed the tutorial from my previous post?

i have tryed but i get error about a missing PUBKEY, i've posted a reply there too if you want to help me out ;)

here's a example (not the most glam-glam i admit) of a streaming video which doesn't work put for me. [http://www.ehow.com/video_4908552_highspeed-rotary-tools-engraving.html]("http://www.ehow.com/video_4908552_highspeed-rotary-tools-engraving.html")
thx

---

### Post by lovinglinux on 2010-01-05
> **rudedcam said:**
> i have tryed but i get error about a missing PUBKEY, i've posted a reply there too if you want to help me out ;)

here's a example (not the most glam-glam i admit) of a streaming video which doesn't work put for me. [http://www.ehow.com/video_4908552_highspeed-rotary-tools-engraving.html]("http://www.ehow.com/video_4908552_highspeed-rotary-tools-engraving.html")
thx

It is a flash video. See **Solution** [*[COLOR="Red"]**FOT004 **[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004 ).

---

### Post by rudedcam on 2010-01-05
> **lovinglinux said:**
> It is a flash video. See **Solution** [*[COLOR="Red"]**FOT004 **[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004 ).

finally working like a charm:D
thank you!

---

