---
title: "Installing Firefox new version on Ubuntu 9.10"
date: 2010-04-23
forum: General Help
---

### Post by kasun04 on 2010-04-23
Hi,

I want to user a new version of Firefox on my ubuntu 9.10 - 64bit installation. What I got is a 64-bit version of ubuntu and couldn't find a suitable new Firefox distribution.

Please help.

---

### Post by didkoslawow on 2010-04-23
Maybe you can try this ppa:
```
add-apt-repository **ppa:ubuntu-mozilla-daily/ppa
```**

---

### Post by kasun04 on 2010-04-23
When I go to firefox site it only displays 32bit version

---

### Post by kasun04 on 2010-04-23
> **kasun04 said:**
> When I go to firefox site it only displays 32bit version
I mean at lease it should detect the version of the OS we have and suggest accordingly. (Chrome/Opera offers compatible versions but Firefox didn't)

---

### Post by lovinglinux on 2010-04-23
Mozilla doesn't release official builds of Firefox 64bit, but they do release nightly builds. The version you have is already 64bit, but if you want to upgrade to latest version, then you basically have two options:

[LIST]
[*]download from Mozilla nightly repository and extract it to your home or /opt
[*]upgrade using a ppa from Mozilla Team
[/LIST]

Lately, I have been recommending 64bit users to download from Mozilla, but if you want the convenience of the ppa, then use **mozillateam/firefox-stable** instead of **ubuntu-mozilla-daily**.

There are some considerations about using a ppa repository for Firefox that I would like to highlight:

[LIST]
[*]some ppa repositories like *ubuntu-mozilla-daily* update not only Firefox, but also other Mozilla applications, like Thunderbird.
[*]some ppa repositories like *ubuntu-mozilla-daily* install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

For more info see the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

