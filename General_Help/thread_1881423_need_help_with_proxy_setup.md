---
title: "need help with proxy setup"
date: 2011-11-15
forum: General Help
---

### Post by peragrate72 on 2011-11-15
I've been at this for about three hours and can't get lucid to work through a local or remote proxy.

I need a complete newbie guide to setting up a local encrypted proxy for ftp and http/s.

Changing the proxy settings in seamonkey or firefox doesn't work. After changing to manual proxy settings I still get the same public IP as if I selected "direct Internet connection," or "no proxy."

Help!

I've tried tor, torbutton, polipo, and squid. I can't get anything to work, and I really need a simple solution. I don't really understand SSH or VPS, and I'm trying to do this for free (not cheap - just needs to be that way for now.)

Searched up and down, including blackhat and ubuntu forums. Can't get this to work.

PS: It took about five minutes to set up before re-entering North America. Had to wipe computer before coming in (heavy activist here), and now I can't set it up at all.

I'm not sure if I'm on a static IP or not. I think it's static, because it's the same IP between reboots. (Don't know who the ISP is at the moment.) IP begins with 70.28.**.***

Can anyone help?

Lucid
64-bit

---

### Post by Dangertux on 2011-11-15
[http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)  

This should get tor working on lucid so long as you do the following. Change the following line 

```
[FONT=monospace]
[/FONT]deb     http://deb.torproject.org/torproject.org natty main
```to

```
[FONT=monospace]
[/FONT]deb     http://deb.torproject.org/torproject.org lucid main
```This should work out for you.

---

### Post by peragrate72 on 2011-11-15
Thanks a million. That took care of it.

---

### Post by Dangertux on 2011-11-15
Glad it worked for you :-)

---

