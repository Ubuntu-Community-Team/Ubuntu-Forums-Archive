---
title: "who do i contact to get a driver changed in the kernel?"
date: 2009-12-01
forum: General Help
---

### Post by confused_user on 2009-12-01
Hi, for some weeks i have been battling with the stock rtl8080 kernel module that ships with Ubuntu.  The short of it is that it is broken.  The driver times out frequently and requires an unloading / loading of the module to get it working again.  

I was able to pass about 2MB of data before it would time out.

I spoke with Realtek who sent the source for a better driver and it works much better than the one supplied in the kernel.

My question is, how do i get this included in the kernel so that 

A) every one with the rtl8187SE wireless chipset can use their cards with no trouble

and 

B) i can do a kernel update without breaking this working driver.


Is there a forum or an email address or something?

Thanks
cf

---

### Post by t0p on 2009-12-01
There's the Linux kernel mailing list - its faq is [here]("http://www.kernel.org/pub/linux/docs/lkml/").  Or you could post a bug report - instructions [here]("https://wiki.ubuntu.com/Bugs").

---

### Post by HermanAB on 2009-12-01
You can contact Greg Kroah-Hartman at Novel.  He'll make you a custom device driver for pretty much anything for about $10,000 or so.

---

### Post by confused_user on 2009-12-01
thanks for the link, i'll try there.

erm,why would i pay that guy $10k when i can just send an email to realtek and they email me back a working driver?

---

