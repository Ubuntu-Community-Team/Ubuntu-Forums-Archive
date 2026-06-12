---
title: "IPv6 woes"
date: 2009-10-28
forum: General Help
---

### Post by justin.rixx on 2009-10-28
I installed Karmic RC (I actually had the same problem in Beta). I couldn't connect to the internet, but I could connect in other places. I concluded that my router is the problem.
This is what I have decided:

Ubuntu says "Hi can you use IPv6?"
Router says "Sure!"
Ubuntu says "okay, I will use that!"
Router tries, but apparently doesn't even support IPv6
Ubuntu just keeps using IPv6, because router said it can take it

I get this same problem connecting hard-wired. So my question is: Is there a way to manually tell Ubuntu to only use IPv4 while connected to "router"?

Like I said it connects fine elsewhere, I guess my router is just unlucky . . .

Thanks in advance!

JustinRixx

---

### Post by winotree on 2009-10-28
I don't know if this will help but you can turn off ipv6 in Firefox: open about:config and type ipv6 in the Filter bar; change this line *network.dns.disableIPv6* from false to true.

---

### Post by justin.rixx on 2009-10-28
How do I get to about:reply?

Is it in one of the Firefox menus?

---

### Post by winotree on 2009-10-28
It's about:config.  Type about:config in your URL or address bar.  Click enter.  Click *I'll be careful...* [You'll see  ;) ]

Type the line *network.dns.disableIPv6 *in the filter bar*. * Click enter. In my case a right-click brings up a box -- toggle to change it from false to true.  As I said, this may not work for you...

---

### Post by justin.rixx on 2009-10-28
Thanks, it works!!

---

### Post by PhilGil on 2009-10-28
Another option is to change your DNS server to Open DNS: [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/) .  The network manager looks a bit different in Karmic, but the instructions should still be easy to follow.  The advantage of this approach is that it works for all your Internet-connected applications, not just Firefox.

I'm not entirely thrilled with putting my DNS resolution into the hands of a third party, but it will do until the devs get this problem sorted.

---

### Post by winotree on 2009-10-28
> **justin.rixx said:**
> Thanks, it works!!
Well, I'll be -- erm, I mean that's great.  ;)  :D

---

