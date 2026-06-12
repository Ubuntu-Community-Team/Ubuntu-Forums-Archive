---
title: "DNS problems using Chrome and/or Chromium"
date: 2010-01-16
forum: General Help
---

### Post by DeMus on 2010-01-16
Hi,
Like many I also had the problems of slow working Google Chrome and Chromium webbrowsers.
For around 10 seconds after clicking a link I would see the words: "**Resolving host**" in the left bottom corner of the screen.
I did find the solution for this. It consists of a couple of steps necessary to get rid of it. But then it works lightning fast. Also other internet programs, like Firefox, benefit from it.

Step 1:
Open menu **System** -> **Preferences** ->  **Network connections**
With a wired system choose TAB **Wired**, click on **Eth0** and choose **Edit**.
In the next window choose **IPv4 Settings**.
Choose for **Method**: **Automatic (DHCP) Addresses only**
Type at **DNS servers: 8.8.8.8, 8.8.4.4**
Click Apply and close the windows

Step 2:
Open the **Options** in Chrome/Chromium by clicking the **wrench** on the right top side of the screen.
Choose Tab U**nder the Hood**. _Unclick_: **Use DNS pre-fetching to improve page load performance**. Click close.

Step 3:
If you use a router also write the DNS addresses in there as well. How to do that depends on the type of router you use.

Step 4:
Stop and re-start Chrome to make it use the settings.

Have fun.

---

### Post by mechro on 2010-01-16
Is that Google DNS servers? Interesting... I'll give it a go.

---

### Post by DeMus on 2010-01-16
> **mechro said:**
> Is that Google DNS servers? Interesting... I'll give it a go.

Yes, they are the Google DNS servers. I forgot to mention that.

---

### Post by Linuxforall on 2010-01-16
Actually for days google dns was unable to resolve Facebook DNS so I had to switch to DNS advantage which works quite good. To make it even quicker, I did the boot hack to disable ipv6 and installed pdnsd which is a locak dns cache server so now combined with all, Opera 10.5 pre alpha and chrome both rock.

---

