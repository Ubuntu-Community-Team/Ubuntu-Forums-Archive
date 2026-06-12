---
title: "Can I cache Ubuntu updates locally?"
date: 2009-09-11
forum: General Help
---

### Post by Infoteksec on 2009-09-11
Hi, I have a few Ubuntu installations on various laptops and desktop systems and get hit with download charges from my ISP whenever I update them.

I know squid can cache files but generaly its intended for small files. What I'd like to do is keep a cache of updates on a USB hard disk that I can apply whenever I want.

It would be great of the cache contents were refreshed its its contents were superceded. I'm sure I'm not the first to think of this but I can't find anything other that Squid.

Peter

---

### Post by P4man on 2009-09-11
What I do is use apt-cacher-ng

It acts like a apt proxy, Its in the repo's and very easy to set up. Only annoyance, if the machine that is configured as proxy is offline, then none of the other computers can install anything without making a small change to the apt configuration file.

[http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html](http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html)

---

### Post by konqueror7 on 2009-09-11
> **Infoteksec said:**
> Hi, I have a few Ubuntu installations on various laptops and desktop systems and get hit with download charges from my ISP whenever I update them.

I know squid can cache files but generaly its intended for small files. What I'd like to do is keep a cache of updates on a USB hard disk that I can apply whenever I want.

It would be great of the cache contents were refreshed its its contents were superceded. I'm sure I'm not the first to think of this but I can't find anything other that Squid.

Peter
 have you tried [APTonCD]("http://aptoncd.sourceforge.net/")? you can backup your cache and then mount/use it on other units as a source, thus not requiring anymore download. its also available in the repos. this is whati usually use. =)

```
sudo apt-get install aptoncd
```

---

### Post by Infoteksec on 2009-09-21
Thanks guys - APTonCD works well. I was concerned that I had to write the APT list to CD since I dont have a CD drive on my Acer Aspire One. Thankfully, aptoncd creates an ISO file and which it quite happy to read from on so I can use a USB stick as my storage device.

Thanks again

---

### Post by docdtv on 2011-11-24
Evidently, *APTonCD* is not a perfect solution, because of a consideration described in its [*Wikipedia* article]("http://en.wikipedia.org/wiki/APTonCD"), *viz*.:[INDENT]*Since APTonCD just copies the deb files on the cache, it will not save files that are downloaded when the .deb packages are installed, this causes packages like "[ubuntu-restricted-extras]("http://en.wikipedia.org/wiki/Ubuntu-restricted-extras")" or the flash plugin to fail when installing them on a computer with no internet access.*
[/INDENT]

---

