---
title: "Natty: Unable to Scan to JPEG/PNG/TIFF"
date: 2011-07-18
forum: General Help
---

### Post by 2CV67 on 2011-07-18
Since upgrading from 10.10 to 11.04 I have a new scanning problem with my Epson Perfection V200 Photo scanner.

Using the same "Image Scan!" (Avasys Iscan) application as before, I can now only save as PNM or PDF.
The PNG & JPEG & TIFF options are now greyed out & not available.

I found this Bug report which seemed to cover the JPEG problem & offered a solution.
[https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/792882](https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/792882)

But I have just tried creating the suggested link (libjpeg.so pointing to libjpeg.so.62.0.0) and there is no improvement.
OK, I did it by GUI - copy/pasting/renaming the existing libjpeg.so.62 link, but that should give the same result, surely...

Any ideas please?

---

### Post by 2CV67 on 2011-10-29
Bump!

Still no jpeg/png/tiff...

---

### Post by 2CV67 on 2011-10-30
Googling (whatever did we do before?) this problem, I came across Old Nabble, whoever or whatever that is:
[http://old.nabble.com/-iscan--New-release-available-td31970137.html](http://old.nabble.com/-iscan--New-release-available-td31970137.html)

And noticed:
 > ----------------------------------------------------------------------
 iscan-2.26.3                                              (2011-04-11)
 ----------------------------------------------------------------------
  * fixes PNG, JPEG and TIFF file format selection on Ubuntu 11.04
  * adds a manual page for the iscan-registry utility 

So I uninstalled iscan, downloaded & installed the current version (2.27.1-4) and can now save to all the required formats!

Problem [SOLVED]

Still leaves some questions though:
1. Why can't I find any trace of this fix on Avasys site [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/) ? (maybe I didn't look in the right places...)? 
2. Is there some way of upgrading iscan, without removing & reinstalling?

Oh well - at least it is working again!

---

