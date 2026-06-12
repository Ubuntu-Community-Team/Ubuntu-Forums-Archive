---
title: "Having problems getting my onboard WLAN Broadcom to work."
date: 2006-03-11
forum: General Help
---

### Post by Tomguruken36 on 2006-03-11
I am new to Ubuntu ( and Linux in general). I have installed Ubuntu on my Hp Pavilion dv1000 laptop and tried to get my wireless card working. I have already looked at many different ways of doing it. They all involve an .inf file. My Broadcom 802.11b/g WLAN onboard wifi card only uses a .sys file. Is there anyway to get my card working in Ubuntu with only a .sys file.

---

### Post by Zelut on 2006-03-11
Your windows driver may only use the .sys file but the driver package should include a .inf file as well.

there are a few ways of trying to find out which drive you need for ubuntu.
1) you can a simple script I wrote to help you find out [here]("http://christer.homeip.net/wordpress/?p=15")
2) you can try using my step-by-step & find out on your own [here]("http://christer.homeip.net/wordpress/?page_id=8")

3) you need to download the appropriate driver & ndiswrapper.  You'll find details there on my how-to page.

---

