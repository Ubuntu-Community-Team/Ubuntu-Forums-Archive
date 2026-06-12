---
title: "Please help me change the display of my computer"
date: 2011-05-10
forum: General Help
---

### Post by ehostserver on 2011-05-10
Hi Friends,

I have a Samsung B2030 Monitor whose resolution is 1900x1200 but after installation of UBUNTU 11.04 it shows only 1024x768. If anybody can help me change the resolution - I would really appreciate it.

If the person wants a remote access to the system - I can allow that as well but he will have to tell me the info step by step as I am a novice and new to ubuntu.

Regards,

D. Richard

---

### Post by Grenage on 2011-05-10
> **ehostserver said:**
> Hi Friends,

I have a Samsung B2030 Monitor whose resolution is 1900x1200 but after installation of UBUNTU 11.04 it shows only 1024x768. If anybody can help me change the resolution - I would really appreciate it.

If the person wants a remote access to the system - I can allow that as well but he will have to tell me the info step by step as I am a novice and new to ubuntu.

Regards,

D. Richard

First off, don't offer remote desktop access to anyone - there's no guarantee that someone malicious isn't reading your post.

When looking under *Additional Drivers*, are any graphical driver options available?  What graphics card do you have?  If you don't know, post the output of:

```
lspci | grep VGA
```

---

### Post by ehostserver on 2011-05-10
After Entering the command in Terminal - This is the information that came up.

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Thanks

Richard D.

---

### Post by Grenage on 2011-05-10
Ah, SiS.  While I have no personal experience with SiS cards these days, they do often cause headaches.

There's a good blog post [here]("http://hellbunker.blogspot.com/"), which may prove useful.

---

