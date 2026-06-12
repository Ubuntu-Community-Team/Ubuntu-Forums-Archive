---
title: "Ubuntu 11.04 freezes after surfing around"
date: 2011-04-30
forum: General Help
---

### Post by dArignac on 2011-04-30
Howdy,

I recently upgraded to 11.04 and when I browse to pages that use the flashplugin the whole system froze. So I installed the flashplugin that somehow got deinstalled and while installing the system froze again. I fixed the dpkg and then I could connect to websites using flash but nonetheless the system freezes after some seconds using any browser.
I have a Netgear WLAN card that uses Windows drivers as there are none for linux. It worked alright in 10.04 for a whole long time. But I'm not sure what the real problem is as I can't find any log telling my some sort of error. So I'm kinda stuck.
On my netbook with 11.04 everything works like a charm...
Thanks in advance!

Alex

---

### Post by chrism3568 on 2011-05-06
I too have found the same behavior in 11.04. If I run anything other than a browser I am fine, the system is stable. This machine ran fine with 10.x. I've tried multiple browsers, Chrome, Firefox, and Epiphany and get the same result. Tried safe mode and classic mode with the same result.

I am now trying removing flash and reloading to see if that helps.

The machine freezes but does not crash, i.e. I left it "frozen" for a couple of hours clock did not refresh, no mouse, no keyboard.

---

### Post by dArignac on 2011-05-15
Well, the problem was definitely the wlan cards drivers.
I bought a new card, the Cisco Linksys WMP600N, that was said within the ubuntu wiki to work out of the box - and it does, simply changed the card, started ubuntu and everything was fine.

---

