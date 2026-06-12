---
title: "libxine-extracodecs |  Package NOT found!"
date: 2006-06-04
forum: General Help
---

### Post by link141 on 2006-06-04
Greetings fellow Ubuntu users.  I currently have ubuntu installed on my 32-bit PC.  I am posting this because the provided solution on the wiki page to support MP3's (and other restricted codecs) < [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) > instructs me to install the package libxine-extracodecs to enable support these formats.  The problem is that this particular package cannot be found in ANY of the repositories (I enabled **all** of the multi-verse and universe repositories already).  I could try using other servers for this package, but I don't wan't to slow my package manager down to a crawl.  Is anyone else experiencing this problem, and does anyone know how to fix it?  

I have many other problems that I wan't to fix, but I don't feel like dealing with them at the moment.  

Thanks in advance.

---

### Post by croak77 on 2006-06-04
libxine-extracodecs is in multiverse so maybe you should double check your /etc/apt/sources.list.

---

### Post by tsb on 2006-06-04
add 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse' to your sources.  I had the same problem because the Taiwan mirror didn't seem to have many files.  This one has them.

---

### Post by whoscheesemine on 2008-03-17
after following that i still didn't find the package, but was redirected to 

libxine1-ffmpeg

 which worked just fine

---

