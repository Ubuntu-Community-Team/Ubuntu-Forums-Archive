---
title: "Safe and anonymous websurfing on ubuntu 10.0"
date: 2011-07-11
forum: General Help
---

### Post by ubuntistas on 2011-07-11
Hello to all of you guys! is there any way to create an anonymity on ubuntu 10.0 ? i tried Vidalia and Tork but the tork client is not working! any help will be appreciate! thank you !!

---

### Post by hwttdz on 2011-07-11
This is what I use, you're going to want to make sure to get an up to date version for your hardware and if you use it more than a few times a year it's probably worth keeping it around instead of deleting it at the end.

#!/bin/bash
wget -q -O tor_bundle.tar.gz [https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-x86_64-1.1.4-dev-en-US.tar.gz](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-x86_64-1.1.4-dev-en-US.tar.gz)
tar -zxf tor_bundle.tar.gz
./tor-browser_en-US/start-tor-browser
/bin/rm -rf ./tor-browser_en-US/ tor_bundle.tar.gz

---

### Post by ubuntistas on 2011-07-13
thank you very much it works perfect!!

---

### Post by ubuntistas on 2011-07-14
is there any tutorial or something else for better anonymity with TOR.?

---

