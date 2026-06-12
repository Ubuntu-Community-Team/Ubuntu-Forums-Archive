---
title: "Opening webpages is very slow"
date: 2011-04-18
forum: General Help
---

### Post by confederate502 on 2011-04-18
I'm using Ubuntu 10.10 and whenever I open webpages in my web browser it's very slow even though when loading youtube videos or updating the speed is about right. I did a speed test and it's what it's suppose to be so what's the deal? I had windows xp on one my computer's and the internet is very fast but when I went to 10.10 the speed went to crap.

---

### Post by spikoley on 2011-04-19
It is difficult to trouble shoot something that is half way working.  My only suggestion is to try a different browser.  Try installing Chromium (open source version of Google Chrome).

```
sudo apt-get install chromium-browser
```

Let us know if Chromium has the same issue.

---

### Post by confederate502 on 2011-04-20
it's still slow

---

### Post by spikoley on 2011-04-20
Go to [speedtest.net]("http://speedtest.net") and compare the results to your connection speed.

---

### Post by cimh on 2011-04-30
I am experiencing similar problem with Natty. But is an inconsistent error so probably very hard to track down.

Using either chrome or ff 'some' pages and sites take forever to download but others seem ok.

Some pages may be ok initially then stall when I return to them several minutes later. 

My wifi looks ok. Pinging ubuntu.com gives me 22ms. 

One site I cant open is speedtest. pinging this is also inconsistent sometimes 180ms but at other times 1000ms. Sometimes nothing.

This does appear to be unique to natty. In another partition I have peppermint ice (based on ubuntu 10) This opens pages quickly and reliably. Pinging ubuntu.com gives the same about 22ms. I can run speedtest.com easily on peppermint the ping test gives 46. Download speed = 10M, upload speed 0.4 I can't remember what the units are. 

Keithpeter at
[http://ubuntuforums.org/showthread.php?p=10691279](http://ubuntuforums.org/showthread.php?p=10691279)
had a very similar problem on a v similar machine. Mine is an eee901 and his an eee1000 I think we both use the same wifi module. but that thread is closed.

The one problem when I installed natty was getting a good internet connection the wifi would connect but that was all. I couldnt even get synaptic or apt-get to work. Now I did solve this by asking synaptic to search for the best server and connect to that which it did. But I wonder if this is a left over from those initial problems and indicates a glitch somewhere in my system.

cimh
eee 901 natty

---

