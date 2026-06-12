---
title: "BUG? Chromium caused UNR 10.04 freeze"
date: 2010-09-22
forum: General Help
---

### Post by z3romaster on 2010-09-22
Hi to all,

I would like to report my experience while using UNR 10.04.

Everytime I connect my Nokia handphone either as a mass storage mode (for transfering video/image) OR using my handphone as a 3.5G Modem.

While connected or even after I finished connecting my handphone for the above purposes, when I close down Chromium browser, the whole OS will freeze!! Neither keyboard or mouse would work. This thing does not happened if I'm using Firefox for browsing internet.

I have to do a hard restart to use my netbook again. 

Chromium:
6.0.472.53 (57914) Ubuntu 10.04

UNR 10.04: with updated software packages

HP Mini 110-1006TU
Standard specification with 2GB RAM.

Look forward for the forum to comment.

Thanks

---

### Post by z3romaster on 2010-09-24
i guess, no one would know about this.

---

### Post by brodiewells on 2010-10-02
I was using chrome and my netbook kept freezing the mouse.  I saw your post and now that I am not using Chrome it seems to work.  Thanks for narrowing it down for me.

---

### Post by Puxbunny on 2010-10-04
It seems to be a bug in kernels prior to 2.6.35 when connecting a phone in USB mode to the computer.
It is caused by two modules loading: phonet and cdc_phonet.
It seems to occurs when chromium's sandbox is used (by default).

Three solutions should work:
[LIST]
blacklisting theses modules by adding
```
blacklist cdc_phonet
blacklist phonet

```
at the end of /etc/modprobe.d/blacklist.conf
[/LIST]
[LIST]
disabling sandbox in command-line by adding the option --no-sandbox
[/LIST]
[LIST]
upgrade your kernel to 2.6.35 version
[/LIST]

Further informations:
[http://code.google.com/p/chromium/issues/detail?id=54617&q=exit%20os%3DLinux&colspec=ID%20Stars%20Pri%20Area%20Feature%20Type%20Status%20Summary%20Modified%20Owner%20Mstone%20OS](http://code.google.com/p/chromium/issues/detail?id=54617&q=exit%20os%3DLinux&colspec=ID%20Stars%20Pri%20Area%20Feature%20Type%20Status%20Summary%20Modified%20Owner%20Mstone%20OS)
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/637803](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/637803)

---

