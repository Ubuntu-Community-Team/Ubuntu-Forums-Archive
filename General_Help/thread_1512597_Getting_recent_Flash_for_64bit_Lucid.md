---
title: "Getting recent Flash for 64bit Lucid"
date: 2010-06-18
forum: General Help
---

### Post by roncrump on 2010-06-18
Hi,

I've just upgraded to 64-bit Lucid and then tried to access the BBC iplayer. I got a message saying I needed a newer version of Flash, so I followed the link provided to the Adobe web site. However, there doesn't seem to be a 64-bit version available from there.

I'm sure I'm not the first person to have had this problem, but I couldn't find an obvious thread on it among the many flash-related ones, so how do I get a recent version of Flash installed in 64-bit Ubuntu 10.04? Have Adobe stopped creating 64-bit versions, or do they just not do a good job of identifying the architecture?

Ron.

---

### Post by philinux on 2010-06-18
[http://ubuntuforums.org/showthread.php?t=1503920&highlight=flash+security](http://ubuntuforums.org/showthread.php?t=1503920&highlight=flash+security)

I've installed the 32 bit plugin till the dust settles.

```
sudo apt-get install flashplugin-nonfree
```

This fixes full screen flash for me with the 32 bit plugin.
[http://ubuntuforums.org/showpost.php?p=9468193&postcount=4](http://ubuntuforums.org/showpost.php?p=9468193&postcount=4)

---

### Post by dcstar on 2010-06-18
> **roncrump said:**
> Hi,

I've just upgraded to 64-bit Lucid and then tried to access the BBC iplayer. I got a message saying I needed a newer version of Flash, so I followed the link provided to the Adobe web site. However, there doesn't seem to be a 64-bit version available from there.

I'm sure I'm not the first person to have had this problem, but I couldn't find an obvious thread on it among the many flash-related ones, so how do I get a recent version of Flash installed in 64-bit Ubuntu 10.04? Have Adobe stopped creating 64-bit versions, or do they just not do a good job of identifying the architecture?

Ron.

Abode are really annoying removing the 64-bit RC candidate because they could not be bothered fixing that latest security issue that caused them to release the new version of Flash player a week or so ago. However here is a link to download the last 64-bit plugin that I use:

[http://members.iinet.net.au/~dcstar/files/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://members.iinet.net.au/~dcstar/files/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

---

### Post by roncrump on 2010-06-18
> **dcstar said:**
> ..here is a link to download the last 64-bit plugin that I use..

Thanks for that. Then the (uncompressed and untarred) .so file just goes into ${HOME}/.mozilla/plugins ?

---

### Post by dcstar on 2010-06-18
> **roncrump said:**
> Thanks for that. Then the (uncompressed and untarred) .so file just goes into ${HOME}/.mozilla/plugins ?

/usr/lib/firefox-addons/plugins

---

