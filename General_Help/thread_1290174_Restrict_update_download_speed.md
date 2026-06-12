---
title: "Restrict update download speed"
date: 2009-10-13
forum: General Help
---

### Post by ILMV on 2009-10-13
Hello All

Here is my issue, I use Ubuntu Server for my dev rig at work, we have about 15-20 staff that are constantly using the internet for various reasons. Now whenever I want to update Ubuntu it downloads at the highest possible speed it can achieve, however this is using so much of our bandwidth it is causing people to fail to connect to various web services (website, email etc).

I need a way to slow down my updates, so they can be installed but without causing so much havoc, I don't care if it takes hours to download them.

So is there a way of restricting the speed of my updates?

Thanks :guitar:

---

### Post by zer0x on 2009-10-13
Hi,

Just found this thread:
[URL="http://ubuntuforums.org/showthread.php?t=39034"]
http://ubuntuforums.org/showthread.php?t=39034[/URL]

HTH

zer0x

---

### Post by ILMV on 2009-10-13
Awesome, many thanks!

For those who may stumble upon this, here is what I have got working:

```
sudo apt-get -o Acquire::http::Dl-Limit=25 upgrade
```

---

