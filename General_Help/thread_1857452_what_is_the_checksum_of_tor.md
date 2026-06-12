---
title: "what is the checksum of tor?"
date: 2011-10-10
forum: General Help
---

### Post by ioyear on 2011-10-10
I don't it is a right place to post, if wrong then I am sorry. I got tor-browser-gnu-linux-i686-2.2.33-2-dev-en-US.tar.gz from [https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-i686-2.2.33-2-dev-en-US.tar.gz](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-i686-2.2.33-2-dev-en-US.tar.gz),  I want to know its MD5, thank you!

---

### Post by shashanksingh on 2011-10-10
MD5 is basically a hashing algorithm. What it means is that for every possible "data", ie, collection of bits, it produces a unique value called MD5 sum.

While distributing software, an MD5 is given by the provider so that the user can ensure if what he has downloaded is EXACTLY what the provider intended to without any errors in transmission.

---

### Post by raja.genupula on 2011-10-10
[http://checksumtool.sourceforge.net/](http://checksumtool.sourceforge.net/)


go with that, I hope thats gonna help you.

---

### Post by haqking on 2011-10-10
see here [https://www.torproject.org/docs/verifying-signatures.html.en](https://www.torproject.org/docs/verifying-signatures.html.en)

towards the bottom for Linux

---

### Post by haqking on 2011-10-10
> **shashanksingh said:**
> MD5 is basically a hashing algorithm. What it means is that for every possible "data", ie, collection of bits, it produces a unique value called MD5 sum.

While distributing software, an MD5 is given by the provider so that the user can ensure if what he has downloaded is EXACTLY what the provider intended to without any errors in transmission.

I think they wanted the checksum to verify the integrity of the package not what MD5 actually is

> **raja.genupula said:**
> [http://checksumtool.sourceforge.net/](http://checksumtool.sourceforge.net/)


go with that, I hope thats gonna help you.

That wont verify the integrity of the source download

---

