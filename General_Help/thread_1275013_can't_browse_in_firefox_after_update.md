---
title: "can't browse in firefox after update"
date: 2009-09-25
forum: General Help
---

### Post by BiaxidentM on 2009-09-25
I'm doing my baby steps into ubuntu and linux, installed for the first time yesterday.
I let it do the automatic updates and then installed ubuntuzilla and updated firefox to 3.5.3.
now I can't browse the internet through firefox, Pidgin works fine so it's not a connectivity issue.
I tried to search the forums and googled it but didn't fined anything useful.
it actually happened to me twice, sines I did the same once before and then decided to repartition my hard-drive and installed ubuntu again.

please help, thanks.

---

### Post by lovinglinux on 2009-09-25
> **BiaxidentM said:**
> I let it do the automatic updates and then installed ubuntuzilla and updated firefox to 3.5.3.
now I can't browse the internet through firefox, Pidgin works fine so it's not a connectivity issue.

Ubuntuzilla does not update your current Firefox 3.0.14 but installs 3.5.3 side-by-side with it and also update the launcher link to use the new version. So you still can launch FF 3.0.14 by command:

```
firefox-3.0
```

Anyway, your connection problem is probably due to ipv6. See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by BiaxidentM on 2009-09-30
thanks :)
disabling IPv6 did the trick, I can browse web pages now.

will disabling IPv6 will hurt my surfing experience in any way?

---

### Post by lovinglinux on 2009-09-30
> **BiaxidentM said:**
> thanks :)
disabling IPv6 did the trick, I can browse web pages now.

will disabling IPv6 will hurt my surfing experience in any way?

Nope. Your router and your ISP probably doesn't support ipv6 anyway. Besides, ipv6 is not widely deployed yet. For more info [http://en.wikipedia.org/wiki/Ipv6](http://en.wikipedia.org/wiki/Ipv6)

---

### Post by Xtian_1028 on 2010-06-22
Hello!

I can't seem to browse the internet no matter what browser I am using.

I think it is not the issue of network connectivity since I can use the termional to ping different websites.

Please help. I think the problem lies on either the proxy settings or the DNS. Thanks!

---

### Post by lovinglinux on 2010-06-22
> **Xtian_1028 said:**
> Hello!

I can't seem to browse the internet no matter what browser I am using.

I think it is not the issue of network connectivity since I can use the termional to ping different websites.

Please help. I think the problem lies on either the proxy settings or the DNS. Thanks!

Please create a new thread. This one is really old and marked as solved.

---

