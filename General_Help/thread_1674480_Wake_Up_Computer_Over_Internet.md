---
title: "Wake Up Computer Over Internet"
date: 2011-01-23
forum: General Help
---

### Post by DavidG24 on 2011-01-23
Hey guys,

I was just wondering if there was anyway to wake up a computer with Ubuntu 10.10 x64 over the internet? I'm going to be in hospital for the next month and only have limited net on a shitty laptop running XP, and would love to be able to boot up my home PC, execute a few things and then turn it off.

I was going to use Teamviewer for Remote Desktop (simply as its an easy solution), but am stuck on getting it to boot over the net.

Is this possible?

Cheers,

David

---

### Post by tigerstripedcat on 2011-01-24
There is a way but it may not be worth it.  I've looked into it, but the setup is rather involved.  You need:

1) A Wake-on-LAN (WOL) compatible router
2) A Wake-on-LAN compatible motherboard
3) A WOL access to the router over the internet. Just do some googling and this lifehacker article may help you:

[http://lifehacker.com/348197/access-your-computer-anytime-and-save-energy-with-wake+on+lan](http://lifehacker.com/348197/access-your-computer-anytime-and-save-energy-with-wake+on+lan)

The other options are:

1) Just have someone turn your computer on for you when you need it; you can shut it down remotely.
2) Just leave it on all the time.  Depending on your powersupply and what kind of powerdraw you have you probably wouldn't spend more than $20/month USD and that's most likely towards the upper limit (I run two computers for about $30/month if I remember correctly.)  It is not the best solution if you don't use them all the time, but it is the easiest.

---

### Post by djeikyb on 2011-01-24
Aye. Aside from needing a BIOS and motherboard that supports wake-on-lan, you need a computer on the LAN to issue the wake command. In my case, that computer is a Linksys WRT-54GL router with DD-WRT firmware. I ssh into the router creating a SOCKS server, then use the DD-WRT web gui to wake my tower. You may find these links useful:

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://www.dd-wrt.com/wiki/index.php/WOL](http://www.dd-wrt.com/wiki/index.php/WOL)
[http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

---

