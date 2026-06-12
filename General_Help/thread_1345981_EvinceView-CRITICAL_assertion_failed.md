---
title: "EvinceView-CRITICAL assertion failed"
date: 2009-12-04
forum: General Help
---

### Post by jeschvi on 2009-12-04
I have created a PDF document (using reportlab.pdfgen.canvas) which opens fine in evince and okular.

When I then protect the document with a password using the setEncrypt method, the two viewers suddenly behave differently. Both ask for password and presents the document but evince prints this to the console (the first two come four times):

(evince:2847): EvinceView-CRITICAL **: ev_page_cache_get_size: assertion `page >= 0 && page < page_cache->n_pages' failed

(evince:2847): EvinceView-CRITICAL **: ev_page_cache_get_height_to_page: assertion `page >= 0' failed

(evince:2847): EvinceView-CRITICAL **: ev_pixbuf_cache_set_page_range: assertion `start_page >= 0 && start_page < ev_page_cache_get_n_pages (page_cache)' failed

I have removed all content from the document - except for the password protection: same result.

Can anyone recommend what to do with this? Could okular simply be silent about some errors in the document or is it an error in evince?

I have evince 2.28.1, Ubuntu 9.10.

---

### Post by hwttdz on 2009-12-04
Can you open this pdf? [http://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf](http://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf)

If so I'm guessing it's not an error in evince, it looks like the pdf document has 0 pages (or negative, though I can't figure out what negative would mean).

---

### Post by jeschvi on 2009-12-04
Yes it opens with no complaints. However, it does not have any password protection, which is what seems to cause the errors from evince.

---

### Post by hwttdz on 2009-12-04
But the complaints don't stem from the password, it's complaining about number of pages. Why not drop it in a password protected tar archive?  That's portable and will almost certainly cause no troubles.

---

### Post by jeschvi on 2009-12-04
Thanks.

I might try to see how evince handles some other documents with password protection that are *not* produced with reportlab.
....
Have now done that, and it turns out that if I create a PDF using Scribus, exactly the same happens: when the document is encrypted, evince prints out these "Critical" failures. Okular and xpdf have no complaints. I have put it on GNOME Bugzilla, [         **Bug 588477**]("https://bugzilla.gnome.org/show_bug.cgi?id=588477").

---

