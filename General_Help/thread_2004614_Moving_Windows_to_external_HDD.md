---
title: "Moving Windows to external HDD"
date: 2012-06-16
forum: General Help
---

### Post by kjbox on 2012-06-16
I have an Asus Zenbook UX31E with a 256GB SSD, currently dual booting Ubuntu 12.04 and Windows 7.

I have just 2 programmes that I cannot get to run through wine and several MS Office Excel files with macros I ceated. None of these are frequently used (one of the macros is very long and complex so it will take me a while to get it re-written in LibreOffice Calc!).

Ideally I would like to move the whole Windows partions onto an external HDD and be able to boot from there when Windows is required, thereby freeing up the whole internal SSD for Ubuntu (and in doing so justify the additional expense of a SSD!!).

My question, basically, is: Is this possible?

On a side note does anyone know of links to good resources to learn macro writing in LibreOffice?

Thanks

---

### Post by Cheesemill on 2012-06-16
I don't think it's possible.
Windows only works from an internal drive, It won't work from an external.

---

### Post by kjbox on 2012-06-16
Thanks, that is what I feared. With everything else that is squeezed into the 5mm thickness of the Zenbook finding room for one hard drive must have been difficult so adding a second is completely out of the question! Guess I will have to live with Windows being allowed there with the minimum possible space allocation.

---

### Post by Mark Phelps on 2012-06-16
> **kjbox said:**
> Guess I will have to live with Windows being allowed there with the minimum possible space allocation.

As long as you allow Windows to have some extra space, it should continue to work OK.  But if you were to shrink down the partition so that there is little or no free space, it will fail.  It's needs space for buffers, log files, temp files, and other stuff.  IF you shrink it too much, it won't even boot anymore.

---

### Post by holycow131415 on 2012-06-16
use virtual box, install windows with your windows cd, and install ms office within the windows VM.

---

### Post by sudodus on 2012-06-16
But it is possible to strip off some of the unnecessary programs and services. The main purpose is often to make Windows faster, but if you really ***remove*** programs, you also need less drive space.

Search the internet for ***strip windows***!

For XP you find for example
[[COLOR="Red"]_http://lifehacker.com/374376/trim-down-windows-to-the-bare-essentials_[/COLOR]]("http://lifehacker.com/374376/trim-down-windows-to-the-bare-essentials")

For XP, Vista and 7 you find for example
[[COLOR="Red"]_http://www.pcworld.com/article/218323/speed_up_windows_by_stripping_it_down.html_[/COLOR]]("http://www.pcworld.com/article/218323/speed_up_windows_by_stripping_it_down.html")
and 4 7
[[COLOR="Red"]_http://www.makeuseof.com/tag/remove-unwanted-crapware-brand-windows-7-system/_[/COLOR]]("http://www.makeuseof.com/tag/remove-unwanted-crapware-brand-windows-7-system/")

...

---

