---
title: "Where are the MD5Hashes for 9.10?"
date: 2009-10-29
forum: General Help
---

### Post by jpmelos on 2009-10-29
I can't find them where they are supposed to be...

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Can someone please tell me the md5sum for Ubuntu and Kubuntu 9.10 Desktop i386 final release? Thank you very much!

---

### Post by coffeecat on 2009-10-29
The MD5SUMS would have been a choice lower down the page from where you downloaded. Anyway, this is what I downloaded:

> 836440698456aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
d91659de6e945dbb96eb8970b2b4590a *ubuntu-9.10-desktop-armel+dove.img
297875d2a7531824a0fb08f241d33e85 *ubuntu-9.10-desktop-armel+imx51.img
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
ed6e77587b87fe0d92a2f21855869f00 *ubuntu-9.10-netbook-remix-i386.iso
14707e8847b9c9ba2dd1869fb5086e4f *ubuntu-9.10-server-amd64.iso
55618ad5f180692f9dac20cbff352634 *ubuntu-9.10-server-i386.iso
37a04db193b1a342f961f59aea2fada8 *wubi.exe

**Edit:** Ah, see what you mean - the Ubuntu download isn't showing the usual page at the moment. I'll have a dig around and see what I can find.

---

### Post by The Cog on 2009-10-29
This page has a link to a file called MD5SUMS:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by plucky on 2009-10-29
For Kubuntu.


```
76e5a5d4b704677744bd84e042c05b63 *kubuntu-9.10-alternate-amd64.iso
33fce2476d982977216faa40cbc334c5 *kubuntu-9.10-alternate-i386.iso
5a996e0d794e35509d0275d411a3e737 *kubuntu-9.10-desktop-amd64.iso
18ecb71bff567ce7a91443720a86473e *kubuntu-9.10-desktop-i386.iso
36b1f68a396f3b4e4b5cc0849877ff35 *kubuntu-9.10-netbook-i386.iso
```

Good Luck

See [here](http://releases.ubuntu.com/) for links

---

### Post by jpmelos on 2009-10-29
Thank you guys, problem solved! :D

---

### Post by coffeecat on 2009-10-29
Right - probably something to do with the load on the servers. They've changed the Ubuntu site from what it was this morning. With Ubuntu, where you "select a location", you can only choose a country, rather than a mirror, and you simply get the firefox download prompt. But if you go to the kubuntu.org site, with the "choose a location" drop down list, you can choose an actual server. Click the "Start Download" button, and cancel the Firefox download prompt, and you'll see the download url. Paste everything from that URL except the ISO filename into your address bar and you'll get the page I'm talking about. Scroll down and you'll see "MD5SUMS" which you can click on to view.

I guess they'll update the link you posted when the dust has settled a little.

**Edit:** OK - others got there before me. :) I'll leave this convoluted explanation up. It might just come in useful. :?

---

