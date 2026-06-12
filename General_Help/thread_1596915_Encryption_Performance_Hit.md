---
title: "Encryption Performance Hit"
date: 2010-10-14
forum: General Help
---

### Post by mouldy on 2010-10-14
Hey guys. I've found a few websites that claim about a 5-10% general performance hit when using drive encryption, but no mention of how it affects boot times. At the moment, I've got 10.10 installed on my Acer Aspire One netbook with encryption enabled on /home and it takes a long time to boot, even with loads of services I don't need disabled. It usually takes about 1:20.

If I invested the effort into disabling the encryption (or re-installing from scratch if conversion isn't possible) - would I gain a worthwhile performance boost by not loading encryption related services on boot?

---

### Post by Dusenberg on 2010-12-31
> **mouldy said:**
> Hey guys. I've found a few websites that claim about a 5-10% general performance hit when using drive encryption, but no mention of how it affects boot times. At the moment, I've got 10.10 installed on my Acer Aspire One netbook with encryption enabled on /home and it takes a long time to boot, even with loads of services I don't need disabled. It usually takes about 1:20.

If I invested the effort into disabling the encryption (or re-installing from scratch if conversion isn't possible) - would I gain a worthwhile performance boost by not loading encryption related services on boot?

Hi,

I just installed 10.10 on an old eeepc701. First I did a netbook remix install from live cd which I didn't like (Unity is awful) so then I did a std desktop install but decided I should encrypt the whole disk in case I left the book somewhere... So I used the alternative cd and chose LVM + disk encryption.... It took forever to install (a few hours compared to 50 mins) but finally got there (I'm on SSD so things generally slow).

Ok so - I agree with you, boot (and shutdown) take longer with encryption on.  The netbook 10.10 without encryption booted in about 57secs, with encryption its around 1m40s. Shutdown time is doubled. I am finding updates taking longer as well......

I'm not noticing things are slower in general use however, and the added peace of mind feels worth it for me.

Hope this helps

---

### Post by mouldy on 2011-01-03
Thanks for the reply. Since my last post, I have installed 10.04 with no encryption enabled and everything is much faster, it boots in 22 seconds. I don't know how much is down to it being a different version of ubuntu and how much is down to disabling the encryption - but it was just too slow before.

---

