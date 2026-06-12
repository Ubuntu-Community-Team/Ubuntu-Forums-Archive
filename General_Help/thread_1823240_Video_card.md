---
title: "Video card"
date: 2011-08-11
forum: General Help
---

### Post by ladlers on 2011-08-11
Hi. A power surge occurred yesterday and blew out my ati video card, noticed when the power was restored. I've removed the card and am using onboard video. Windows works (multiple boot) but Ubuntu just hangs at a text screen not giving any important error messages. I think it has something to do with the xorg.conf file. First of all, what is the location of the xorg.conf file in Ubuntu and what must I put in it? Is it something to do with driver vesa? I tried copying the xorg.conf.failsafe to the xorg.conf to no result. I have Slackware linux on the same system and was able to get it to work by copying a file named xorg.conf.vesa to its xorg.conf, but to no avail on Ubuntu. Must I reinstall? I hate to redownload those updates on my 700k dsl line. Thanks.

---

### Post by LowSky on 2011-08-11
boot into safe mode and type

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by papibe on 2011-08-11
Boot on text mode (safe mode), and rename your xorg.conf:
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
(With no xorg.conf, the system should auto detect your GPU)

Then reboot. I hope it helps,
Regards.

---

### Post by ladlers on 2011-08-12
@papbibe: Thanks very much. It worked. I am now going to get that video card replaced by Edison so I may do the same procedure when I put it back.

---

