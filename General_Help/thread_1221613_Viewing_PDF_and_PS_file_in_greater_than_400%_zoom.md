---
title: "Viewing PDF and PS file in greater than 400% zoom"
date: 2009-07-24
forum: General Help
---

### Post by lethalfang on 2009-07-24
Both Evince and Okular cannot zoom over 400%.
Acroread can zoom PDF files, but I can't seem to find it in amd64.
Are there any applications that do?

Thanks.

---

### Post by NoReflex on 2009-07-24
Hello!

Acroread is available through apt. You can find instructions on how to add the repository and install the software here:
[http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html](http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html)
If you don't want to add their repository you can download the Linux_x86 deb file from 
[http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)
and install it with:
sudo dpkg --force-architecture -i filename.deb
There's a "not so elegant" way to zoom past 400%. You can actually zoom your entire desktop. Keep the Windows Key pressed and scrool up and down. It's a really cool feature but I believe you must have compiz enabled for it to work.
Hope this helps you!

Best wishes,
NoReflex

---

### Post by lethalfang on 2009-07-24
I just found out that Inkscape can view .PDF files in any arbitrarily large resolution. Good!

---

### Post by ebodnaruk on 2012-08-08
> **lethalfang said:**
> Both Evince and Okular cannot zoom over 400%.
Acroread can zoom PDF files, but I can't seem to find it in amd64.
Are there any applications that do?

Thanks.

Okular won't zoom more than 400% for me!

---

