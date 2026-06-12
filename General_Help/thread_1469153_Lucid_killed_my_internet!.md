---
title: "Lucid killed my internet!"
date: 2010-05-01
forum: General Help
---

### Post by iu34 on 2010-05-01
Hey all. Upgraded from 9.10 to 10.04 Thursday night. My internet was working perfectly under 9.10, but when I turn my comp on friday morning, my internet speed has been crippled to almost a halt.

In short, I get about 25 kb/s average speed, when it doesn't completely drop me. Under 9.10, I had 250+ kb/s. 

Why is this? I figure it has to be a bug, but is there any way to fix it? It's rendering my ubuntu install completely useless. I'm lucky I got my windows partition fixed, or else my laptop would be more or less a paperweight for a while.

::edit::
Speedtest.net results.

Under windows xp: [[IMG]http://www.speedtest.net/result/801027999.png[/IMG]](http://www.speedtest.net)

Under ubuntu 10.04: ::updated
[[IMG]http://www.speedtest.net/result/801736022.png[/IMG]](http://www.speedtest.net)
This is on the same laptop by the way, same internet connection.

---

### Post by iponeverything on 2010-05-02
poke around on launchpad for bugreports relating to lucid and your particular network hardware. If you find something, add your voice if you don't then create a new bug. 

For future reference, providing 1 or 2 tiny details like perhaps your network hardware might help people help you.

---

### Post by iu34 on 2010-05-02
Ah yes, sorry..

I'm using a linksys wusb54G version 4 adapter. On the other side of the connection, there's a wrt54G router, and a westell 2200 modem. Verizon ISP.

---

### Post by utnubuuser on 2010-05-02
You could try disabling ipv6
Tip #3, bottom of page.> [http://sazeit.com/articles/Ubuntu-tweaks]("http://sazeit.com/articles/Ubuntu-tweaks")

---

### Post by iu34 on 2010-05-02
Already tried that. It helped a little bit, but it didn't solve the problem. I also set up an alternate dns, first tried openDNS then google DNS. Again, helped a little bit, didn't solve anything.

---

### Post by dino99 on 2010-05-02
can you check the difference with an other distro or pc , using the same link, to know if its a lucid problem or else ?

---

### Post by TrevP on 2010-05-02
Hi,

I had similar problems with a Linksys router with intermittent internet speeds (no problems with Windows on my son's machine). The problem was cured by upgrading the firmware on the router. Make sure you have got the latest version. I'm using Lucid Lynx and I'm getting 18.5 to 19.3 Mb/s using Speedtest.net on an up to 20 Mb/s connection.

---

### Post by ishiyakazuo on 2010-05-02
I'm having a similar problem, but it seems to be related to Firefox rather than something across the board (Midori works fine, and Chromium seems to also).
Firefox takes ages to load a new page and resolve IP addresses, the others are quite fast.
I've got an Intel 5100 network card.

---

### Post by iu34 on 2010-05-02
> **TrevP said:**
> Hi,

I had similar problems with a Linksys router with intermittent internet speeds (no problems with Windows on my son's machine). The problem was cured by upgrading the firmware on the router...

How would I upgrade the firmware? I've never done anything like that before..

---

