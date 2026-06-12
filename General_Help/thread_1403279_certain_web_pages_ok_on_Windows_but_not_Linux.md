---
title: "certain web pages ok on Windows but not Linux"
date: 2010-02-10
forum: General Help
---

### Post by rebeltaz on 2010-02-10
I tried to make that as short and descriptive as I could...

There are certain web pages that I try to visit on my Linux computer that either respond after more than a minute of waiting for a response or, more often than not, simply do not respond at all - leaving the browser "waiting for xxxxx". Yet when I try those same pages on my GF's Windows computer, connected to the same router/DSL connection, the pages load quickly and without problems. Both systems are running Firefox..

One of the pages, for reference, is [www.Stens.com](www.Stens.com).

Any ideas? Any one else have problems with that page?

---

### Post by stinkeye on 2010-02-10
Loads fine for me in both Opera and Firefox.

---

### Post by murderslastcrow on 2010-02-10
Yeah, it's just fine for me. Is the computer you're checking these pages from a laptop or a desktop? In particular, does it use wireless or wired internet to go to these websites? This sounds a lot like a networking issue.

You can try a different browser, like Opera or Google Chrome, but I would also suggest checking your Hardware Drivers to see if your pages aren't slow due to a video card not being installed, or even more serious not having the wireless card installed.

Also, if it is wireless, and there is a Free or Proprietary option for your wireless card in Hardware Drivers (under System/Administration), the proprietary one might work better than the free one, and bring you up to acceptable speed.

---

### Post by davec64 on 2010-02-10
If you are using Firefox you could turn off IPV6 (assuming you are not using it).

Open Firefox and type the following in the address bar:

```
about:config
```

Click on "I'll be careful, I promise!"

Then in the filter type "IPV6" (without the quotes).

Double click the row "network.dns.disableIPv6" and the value should change to "True"

Close and restart Firefox to see if this has made a difference. :)

EDIT:
To explain, Firefox uses IPV6 by default to resolve addresses, then when it can't resolve it uses IPV4. Sometimes rhis causes a delay and occasionally the page to time out. By changes this setting you force Firefox to use IPV4.

---

### Post by rebeltaz on 2010-02-11
In answer to the questions: The machine I am having this problem on is a desktop wired to the router. It figures I would be the only one with this problem! :rolleyes:

As for the IPV6 solution, I will give that a try tomorrow. But just for my own curiosity can you tell me what IPV6 is and how I would know if I use it?

Thanks....

---

### Post by davec64 on 2010-02-11
IPV6 is the new addressing system using hexadecimal characters, as opposed to IPV4 which is the standard format for IP addresses. IPV4 uses the format 123.123.123.123 which you're probably aware of.

IPV6 was brought out to replace IPV4 because the powers to be thought that addresses on the Internet would run out. Using IPV6 the range of addresses available is many times greater (I can't remember how much greater!)

If your ISP is using IPV6 I would be very surprised, I'm not aware of it being used (but I could be wrong!)

Hope that answers your question! :)

---

