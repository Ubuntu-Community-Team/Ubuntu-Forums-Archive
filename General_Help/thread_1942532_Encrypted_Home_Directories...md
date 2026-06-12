---
title: "Encrypted Home Directories.."
date: 2012-03-17
forum: General Help
---

### Post by 0011235813 on 2012-03-17
Hi,
I've installed Ubuntu 11.10 via liveUSB, and when I installed it, I had selected the "encrypt my entire home directory" option. However, hibernate doesn't seem to work, as when I try to load into Ubuntu it gives me a blank screen. I have to reboot it and then I get a "cryptswap is not ready yet or not present" error for a couple of seconds (but the swap works fine) .

I had heard that this was an issue within older versions of Ubuntu but I didn't know it was present in Oneiric. My question is, is there any way to set the swap to be non-encrypted, or at least disable the hibernate function (my friends also use the computer) ?

Thanks.

---

### Post by Dave_L on 2012-03-17
"Enable and disable encrypted swap"
[http://www.logilab.org/29155](http://www.logilab.org/29155)

I haven't personally used the above procedure for disabling encrypted swap, so do it at your risk.  I don't know your level of experience with the command shell, but instead of "vim" you can, of course, use any editor.

---

### Post by 0011235813 on 2012-03-17
> **Dave_L said:**
> "Enable and disable encrypted swap"
[http://www.logilab.org/29155](http://www.logilab.org/29155)

I haven't personally used the above procedure for disabling encrypted swap, so do it at your risk.  I don't know your level of experience with the command shell, but instead of "vim" you can, of course, use any editor.

I've read the article, and I've decided it's best to disable the hibernate function in the shell, as the setup looks rather complicated and risky...
Do you know how I could remove the hibernate function in gnome-shell?

---

