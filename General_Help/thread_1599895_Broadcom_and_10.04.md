---
title: "Broadcom and 10.04"
date: 2010-10-18
forum: General Help
---

### Post by ubunterooster on 2010-10-18
I heard that the broadcom wireless was opensourced. Now, I have found an ex-linux user who has a laptop with broadcom wireless so I was wondering if the the drivers are in 10.04.

Is it plug and play or do I need to download the drivers separately?

---

### Post by snowpine on 2010-10-18
Broadcom is open-sourcing their drivers, it's true, but not in time for the 10.04 or 10.10 releases (11.04 at the soonest).

So, for now, please refer to the Broadcom How To:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Step 1, "Identifying Your Card/Driver" is **the most important step** so I recommend posting the results back here for advice before proceeding, if you are unsure.

---

### Post by TBABill on 2010-10-18
You'll need to watch for distros running kernel 2.6.37 or newer before they'll be part of the kernel according to articles I had read when the announcement came out.

---

### Post by Megaptera on 2010-10-18
I've found this simple Broadcom fix works  on Dell (not only Mini) with 10.04

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by TBABill on 2010-10-18
My Dell Inspiron 1545 with Broadcom BCM4312 just requires plugin to ethernet, System>Applications>Hardware and choose the STA driver to install. Then reboot. Works every time.

---

### Post by ubunterooster on 2010-10-18
> **snowpine said:**
> Broadcom is open-sourcing their drivers, it's  true, but not in time for the 10.04 or 10.10 releases (11.04 at the  soonest).

So, for now, please refer to the Broadcom How To:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Step 1, "Identifying Your Card/Driver" is **the most important step** so I recommend posting the results back here for advice before proceeding, if you are unsure.

I will set this up in a VM and use remastersys to make a good Live CD for the guy. Thanks all.

---

### Post by snowpine on 2010-10-18
Let's find out which specific Broadcom card the OP has before we start offering suggestions, people... the answer depends on the particular chipset.

---

### Post by ubunterooster on 2010-10-18
> **snowpine said:**
> Let's find out which specific Broadcom card the OP has before we start offering suggestions, people... the answer depends on the particular chipset.
All I know is "broadcom"

I meet the guy about once a week. I'll ask him next time I see him

---

### Post by snowpine on 2010-10-18
> **ubunterooster said:**
> I will set this up in a VM and use remastersys to make a good Live CD for the guy. Thanks all.

You cannot identify the wireless chipset from within a VM, unfortunately. The VM will only see the "virtual" network device (usually a generic ethernet), not the actual Broadcom card.

A better solution is to boot an Ubuntu Live CD and then follow the command to identify the card (cut and pasted for your convenience):

```
lspci -vvnn | grep 14e4
```

Without the output of that command, any advice I can give you would be an uneducated guess. :) Generally speaking, there are (at least) 4 ways to "get Broadcom working in Ubuntu": wl (also known as 'sta'), b43, b43legacy, ndiswrapper. Which one to choose depends on the chipset you have.

---

