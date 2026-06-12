---
title: "Can't install Firefox addons in Ubuntu 10.04"
date: 2010-05-08
forum: General Help
---

### Post by lightningfox on 2010-05-08
Hello

I recently replaced Opensuse 11.2 on my computer with Ubuntu 10.04.

My internet connection is working and I can install software from Synaptic package manager, but I can't install Firefox addons.


Example I tried to install the Firefox addon Video Downloadhelper from addons.mozilla.org but I got this error:

```
Firefox could not install the file at 

https://addons.mozilla.org/downloads/latest/3006/addon-3006-latest.xpi?src=addondetail

because: Invalid file hash (possible download corruption)
-261
```

I then tried to install that extension by downloading its .xpi file to my hard drive and drragging it into the Firefox addons window but then I got this error:

```
file:///home/ahmed/Downloads/downloadhelper-4.7.3-fx+sm.xpi

because: Not a valid install package
-207
```


I also tried to install Adblock plus but got the same errors with Adblock plus.

I had no problems installing Firefox addons when I was using Opensuse.

Please help me to get Firefox addons to install.

---

### Post by barefootNH on 2010-05-09
This is a common and well-known problem. As a brand-new user of Linux (started with 9.10), I tried everything suggested and nothing fixed it. This affected both my desktop and laptop, but the problem went away by itself on both, presumably through one of the updates a few weeks(?) later.  

I just did a fresh install of 10.04 on my desktop, upgraded to 10.04 on my laptop, and the problem is back. Reading more here on UbuntuForums I saw a new suggestion of turning off IPv6, and it WORKED!

From the Mozilla website:

Enter in the URL address box:

about:config

Click "I'll be careful"

Type ipv6 in the filter box to get to the one and only line that's needed; it'll say network.dns.disableipv6 

the default value is "false"; double-click to set the value to "true" (to disable IPv6)

---

### Post by lightningfox on 2010-05-10
Hi barefootNH, thanks for your reply.
I'll do what you sugggested and see if it fixes the problem.

---

### Post by Itzamna36 on 2010-05-11
Disabling ipv6 worked for me after I was having this same problem today.  Thanks for the fix.

---

### Post by lightningfox on 2010-05-11
Hi
I installed all the updates for Ubuntu and disabled ipv6 in Firefox, and now the problem is fixed.
Thank you for your help.

---

### Post by mauricio.dev on 2011-01-23
Hah, I couldn't believe it really works! I'm on ubuntu 10.10 maverick with a fresh install and wasn't able to install extensions.
Well, great! Thanks!

---

