---
title: "Missing files on NTFS partition"
date: 2012-06-21
forum: General Help
---

### Post by theblackkat on 2012-06-21
Ok, I know there are some posts about this kind of thing, but most are old and not really the same thing I am experiencing, so here it goes:
I have Kubuntu 12.04 and Windows 7 (both 64-bit)on dual boot (using Wubi, actually). I created some files on the "host" ntfs partition, which I can access normally when I'm on Kubuntu. However, when I boot Win7, those files are simply not there. So I go back to Kubuntu, and they're still there, everything exactly the way it was before. I tried running chkdisk, but didn't help. I guess I must also add that I am not hibernating windows, only using good ol' shutdown.
This problem started yesterday, before that, all files I created on Kubuntu could be read normally from Windows...

So... Does anyone have any idea about this?

Thanks!

---

### Post by dino99 on 2012-06-21
im not using winblow since ages but if im right you need ifsprogs installed on winblows, and ntfs-3g on ubuntu

maybe these files are simply hidden: ctrl+h to unhide

---

### Post by theblackkat on 2012-06-21
Thanks for the response!
Well, I never let windows hide anything from me, so they're certainly not hidden.
I remember the time when writing to ntfs system caused all sorts of problems, but as far as I know, everything is a lot better now, and we don have to worry about installing ntfs-3g the sorts of it, they come "pre-installed" with newr versions of ubuntu...

---

