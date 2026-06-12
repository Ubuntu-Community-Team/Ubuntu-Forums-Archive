---
title: "How to do a decent check of the file system?"
date: 2009-11-04
forum: General Help
---

### Post by viking_maniac on 2009-11-04
Well, I booted with the Kubuntu Live CD and entered the Terminal:

$ sudo fsck /dev/sda1

It checked the HDD in just a fraction of a second, and it stated "clean".

It didn't seem like it really checked it. I don't know, shouldn't you see a bar or % or something going upwards and some real HDD activity?

---

### Post by phillw on 2009-11-04
> **viking_maniac said:**
> Well, I booted with the Kubuntu Live CD and entered the Terminal:

$ sudo fsck /dev/sda1

It checked the HDD in just a fraction of a second, and it stated "clean".

It didn't seem like it really checked it. I don't know, shouldn't you see a bar or % or something going upwards and some real HDD activity?

*nix holds stuff differently to windows.

```
man fsck
```Will give you options ... If you want fsck to *really* go trawl as a forced option, then ...

```
sudo fsck -AV
```Is kinda scary ..... do bear in mind the warning message !!!!!

And, yeah, it's that fast.

By the way, you should have a cron job automatically set up to do a deep scan about once a month - You'll see it when you start the computer up.

There is a brief discussion here ...   [http://brainstorm.ubuntu.com/idea/16854/](http://brainstorm.ubuntu.com/idea/16854/)

Phill

---

