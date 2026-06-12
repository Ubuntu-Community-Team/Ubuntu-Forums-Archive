---
title: "Cannot open any websites via Firefox 7.0.1"
date: 2011-10-26
forum: General Help
---

### Post by soumyabratapaul on 2011-10-26
I am running Mozilla Firefox 7.0.1 in Ubuntu 10.04 LTS with all the latest updates, still I cannot open websites such as facebook.com, ubuntuforums.org, and many other webpages. Please help.

---

### Post by linuxwin2 on 2011-10-26
Can you connect with other browser like chrome, opera?
Check you connexion, proxy...

---

### Post by soumyabratapaul on 2011-10-26
> **linuxwin2 said:**
> Can you connect with other browser like chrome, opera?
Check you connexion, proxy...

Everything is fine as far as connection and proxy is concerned. The problem is that Google Chrome opens the pages, but without any text or pictures and filled with hyperlinks. Chrome as well as Firefox, seems to go into trouble when open yahooapis and twitter handling guis as page extras.

---

### Post by lovinglinux on 2011-10-27
> **soumyabratapaul said:**
> Everything is fine as far as connection and proxy is concerned. The problem is that Google Chrome opens the pages, but without any text or pictures and filled with hyperlinks. Chrome as well as Firefox, seems to go into trouble when open yahooapis and twitter handling guis as page extras.

Looks like a problem downloading the style sheets and additional content from third-party servers. Are you using a blocking add-on, like AdBlock Plus?

---

### Post by soumyabratapaul on 2011-10-29
> **lovinglinux said:**
> Looks like a problem downloading the style sheets and additional content from third-party servers. Are you using a blocking add-on, like AdBlock Plus?

The same thing happens with addon and without it. Please help!

---

### Post by LinuxFan999 on 2011-10-29
Go to the terminal and type these 3 commands:
 
```
 
sudo apt-get purge firefox
 
sudo apt-get update
 
sudo apt-get install firefox

```
Repeat this process to reinstall Chromium.

---

### Post by soumyabratapaul on 2011-10-31
> **LinuxFan999 said:**
> Go to the terminal and type these 3 commands:
 
```
 
sudo apt-get purge firefox
 
sudo apt-get update
 
sudo apt-get install firefox

```
Repeat this process to reinstall Chromium.

The same thing continues to happen!

---

### Post by vasa1 on 2011-10-31
> **soumyabratapaul said:**
> I am running Mozilla Firefox 7.0.1 in Ubuntu 10.04 LTS with all the latest updates, still I cannot open websites such as facebook.com, ubuntuforums.org, and many other webpages. Please help.

Which sites **can** you open without any problem? That may give some hint.

Also in Fx 7.0.1, just to make sure .. have you tried clicking Help and then chosing "Restart with add-ons disabled"?

---

### Post by soumyabratapaul on 2011-11-01
> **vasa1 said:**
> Which sites **can** you open without any problem? That may give some hint.

Also in Fx 7.0.1, just to make sure .. have you tried clicking Help and then chosing "Restart with add-ons disabled"?

How many times will I say that disabling the thing and enabling the thing yields the same result. Websites such as facebook.com, ubuntuforums.org, yahoo.com, do not open among many. I have tried Chrome and the same result. Reinstalling the thing also yields the same result. Sites containing yahooapis and twitter guis fail to load.

---

