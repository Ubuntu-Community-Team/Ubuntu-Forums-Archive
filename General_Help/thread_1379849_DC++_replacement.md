---
title: "DC++ replacement"
date: 2010-01-13
forum: General Help
---

### Post by nishant.singh28 on 2010-01-13
I'm seriously fed up with DC++'s sluggishness. It keeps getting stuck and is too much of a resource hog. Is there a better replacement for it? I found the [source code]("http://rsxplusplus.sourceforge.net/downloads.html") of RSX++ which works better than DC++ on Windows. Can someone help me compile it? Or suggest another client? I don't want to run anything on Wine.

---

### Post by matt.foy91 on 2010-01-13
linuxdcpp is a supported version in the software channel

```
sudo apt-get install linuxdcpp
```

Hope this works for you.

---

### Post by nishant.singh28 on 2010-01-13
When I said DC++, I meant linuxdcpp..

---

### Post by matt.foy91 on 2010-01-13
Then I'm at a loss, I think there is a newer version not available via apt-get, but I'm not sure if it's faster.
Unless that's the one you have... sorry I can't be of more help.

I believe ShakesPeer can be run on linux, it's the same direct connection idea so you might try that if all else fails.

---

### Post by nishant.singh28 on 2010-01-13
Latest version already installed.

---

### Post by Uncle Spellbinder on 2010-01-13
The version in the Ubuntu Karmic repos is 1.0.3-1. There is an official PPA with version 1.1.0 [Here](https://launchpad.net/~linuxdcpp-team/+archive/ppa).

---

### Post by nishant.singh28 on 2010-01-13
Arrey Uncle!!! I told you I have the latest version installed. Btw, I found Valknut. Works pretty well. Will be back if any new issues come up.

---

### Post by Uncle Spellbinder on 2010-01-13
> **nishant.singh28 said:**
> Arrey Uncle!!! I told you I have the latest version installed.

Thought the official PPA might be a later version. As you didn't say exactly which version you had. Sorry 'bout that. Good luck with Valknut

---

### Post by nishant.singh28 on 2010-01-15
Valknut is good.

---

### Post by Uncle Spellbinder on 2010-01-15
From the [The Valknut Project](http://wxdcgui.sourceforge.net/)  page:

> About:

Valknut is an open source cross platform client for the Direct Connect network.

Valknut only supports the old (but common) Direct Connect "protocol".

Unfortunately it has **no** support for the new ADC protocol from the DC++ team. If you need an ADC client, try something based on the DC++ core like [LinuxDC++](http://linuxdcpp.berlios.de/articles.php?um=index).

---

### Post by nishant.singh28 on 2010-01-15
I don't need ADC support. And the whole post was about the sluggishness of LinuxDC++.

---

