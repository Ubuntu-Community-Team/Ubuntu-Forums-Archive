---
title: "File compression"
date: 2010-01-29
forum: General Help
---

### Post by Marvin666 on 2010-01-29
What sort of compression ratios would I get from different archive formats for jpg pictures? They are about 300-500kb each.

---

### Post by raktarok on 2010-01-29
Have a look here - it has some nice graphs :)

[http://www.linuxjournal.com/article/8051](http://www.linuxjournal.com/article/8051)

7z is the one with the highest compression ratio, but then, if you also care about the time taken to extract the files, I would suggest you to go for something like gzip or rar.

I hope this was what you were looking for!

---

### Post by mcduck on 2010-01-29
Hardly any, since JPG is already highly compressed data. There's little any stuff that any lossless compression could remove to decrease the size.

Compressed data doesn't compress very well. In worst case you may end with archive that's even slightly *larger* than the original file was.

---

### Post by raktarok on 2010-01-29
> **mcduck said:**
> Hardly any, since JPG is already highly compressed data. There's little any stuff that any lossless compression could remove to decrease the size.

Compressed data doesn't compress very well. In worst case you may end with archive that's even slightly *larger* than the original file was.

I agree. No use compressing already compressed files...

---

### Post by Marvin666 on 2010-01-29
Would it compress better in a png format?
If it doesn't influence file size, does anybody know of a batch image conversion program?

---

### Post by chewearn on 2010-01-29
> **Marvin666 said:**
> Would it compress better in a png format?
If it doesn't influence file size, does anybody know of a batch image conversion program?

In most cases, jpg compresses more than png, since jpg is lossy while png is loseless.

---

### Post by Vaphell on 2010-01-29
modern multimedia formats are heavily compressed already, after all their size translates to time required to transfer them and nobody likes to wait. PNGs in general are bigger than JPGs because they don't cut corners (lossless). Additional compression makes no sense, unless you want to make 1 archive to contain all pics (easier to handle) - but don't expect any significant compression ratio.

---

