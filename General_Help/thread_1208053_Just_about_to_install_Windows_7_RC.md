---
title: "Just about to install Windows 7 RC"
date: 2009-07-08
forum: General Help
---

### Post by The Toxic Mite on 2009-07-08
Hi all!

I have tried Windows 7 on a VM before, but now I want to see its full potential, so I'm going to install it on my laptop. :P

I'm thinking it would be a good idea to install it on a separate partition, basically have the hard disk "split in half" (one half being Ubuntu, the other half being Windows 7).

I want to keep GRUB as my bootloader, so how do I edit it to show Windows 7 on it?

-TTM-

(P.S. The Community Cafe might not be the right place to post it, so feel free to move it if you need to. Thanks :))

---

### Post by jonian_g on 2009-07-08
Boot ubuntu cd and choose rescue mode. You will see there an option to reinstall grub.

---

### Post by The Toxic Mite on 2009-07-08
> **jonian_g said:**
> Boot ubuntu cd and choose rescue mode. You will see there an option to reinstall grub.

O.K. Will it automagically add Windows 7 to the list when you reinstall it?

---

### Post by jonian_g on 2009-07-08
I think so, but I'm not sure. I never tried it witth windows on dual boot but I have tried it with linux distros dual booted.

---

### Post by The Toxic Mite on 2009-07-08
Is it the alternate CD I use to reinstall GRUB?

---

### Post by Sealbhach on 2009-07-08
> **The Toxic Mite said:**
> Is it the alternate CD I use to reinstall GRUB?

Any Live CD should do it.

.

---

### Post by LookTJ on 2009-07-08
> **The Toxic Mite said:**
> Is it the alternate CD I use to reinstall GRUB?

I think you use the live CD to use the rescue mode.

---

### Post by The Toxic Mite on 2009-07-08
Sod it, I will just use the Windows bootloader

*hopes it will auto-detect my Ubuntu partition :D*

---

### Post by CJ Master on 2009-07-09
> **The Toxic Mite said:**
> Sod it, I will just use the Windows bootloader

*hopes it will auto-detect my Ubuntu partition :D*

Nope. If you install W7 AFTER you install Ubuntu it won't.

It's not that hard to reinstall grub. Just get the Ubuntu LiveCD, go into recovery mode, and choose to reinstall grub. It'll automatically detect both Ubuntu and W7.

---

### Post by The Toxic Mite on 2009-07-09
I can't find a "recovery mode" on the Live CD, so I got the alternate CD.

EDIT: I will just install Windows 7 over Ubuntu, then install Ubuntu beside it once it's done. :)

---

### Post by Hominym on 2009-07-09
You could have used EasyBCD to add an entry for Ubuntu to the Windows bootloader, but too late now I guess.

---

### Post by scouser73 on 2009-07-09
You do realise that the Windows 7 RC is about to expire, which means shut downs every two hours; [http://arstechnica.com/microsoft/news/2009/06/warning-windows-7-beta-bi-hourly-shutdowns-start-next-week.ars]("http://arstechnica.com/microsoft/news/2009/06/warning-windows-7-beta-bi-hourly-shutdowns-start-next-week.ars")

---

### Post by twright on 2009-07-09
> **scouser73 said:**
> You do realise that the Windows 7 RC is about to expire, which means shut downs every two hours; <a href="http://arstechnica.com/microsoft/news/2009/06/warning-windows-7-beta-bi-hourly-shutdowns-start-next-week.ars">Ars Technica</a>
That is the beta, not the rc - the rc still has about 6 months left (sigh, "somewhere a clock is ticking")

---

