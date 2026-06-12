---
title: "Easy web filtering?"
date: 2010-07-30
forum: General Help
---

### Post by BDot on 2010-07-30
With an emphasis on easy.

I've been trying without success for the past couple of weeks to setup a filtering system for my little sister's netbook. The main problem I've been running into is inconsistency. 

First, I tried using dyndns per the instructions here:

[http://www.liberiangeek.net/2010/05/the-perfect-parental-control-for-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/05/the-perfect-parental-control-for-ubuntu-10-04-lucid-lynx/)

The problem with this is the DNS settings (and in turn the filtering settings) dont appear to 'stick' once the Netbook touches a different network. So if I sign onto a different wireless network than the one I used to set up the filtering, it stops working. The reason why is Ubuntu will overwrite the current DNS settings with those of the new network (I have no idea why, and am too frustrated to figure out).

Also, I noticed that even if the settings did stick, they're fairly easy to disable because all she has to do is stumble across the DNS settings, change them back and voila.

I've had great success with OpenDNS on Windows boxes, but there doesn't seem a to be a feasible way to apply it to Ubuntu.

Dansguardian looks like it may be worth a shot, but I've seen dozens of "simple" configuration guides, none of which that actually looked simple. 

So my question is this, what is the easiest, most bulletproof way to setup web filtering 10.4? Preferably something that a 12 year-old could easier find her way around.

Any and all input is appreciated.

---

### Post by lykwydchykyn on 2010-07-30
If you want something local to the machine and system-wide, Dansguardian is pretty much the only option.

There are some firefox add-ons like "procon latte" that are very simple to work with, but they have to be installed per-user and only affect firefox.

Here's a setup for Dansguardian with a GUI; it's lengthy, but it's pretty much color-by-numbers if you know what I mean:

[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

That said, I don't know that dansguardian would be the best thing for a netbook, but it's the only one I've personally used.

---

### Post by bodhi.zazen on 2010-07-30
Here is a link on how to set up opendns on Ubuntu:

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

For blocking content, I use dansguardian + privoxy.

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

---

