---
title: "Cannot view PDF attachments in alpine mail client"
date: 2012-09-04
forum: General Help
---

### Post by cpbl on 2012-09-04
When I try to view a PDF attachment in Alpine, I get "don't know how to display application pdf" error.

I have application/pdf lines in both /etc/mailcap and ~/.mailcap

I have tried setting the mailcap path in alpine's settings to each of those.  Nothing works.

Can anyone help me tell alpine about evince?

---

### Post by gaitonde on 2013-02-22
I use alpine in text mode.  It used to show attached PDF files using xpdf.  However, in Ubuntu 12.04 there is a problem with xpdf.  It bombs.

I now use evince.  I found the location of evince using 'which evince'.  It was /usr/bin/evince.  I edited /etc/mailcap (sudo vi ...) and added the following line at its end:

application/PDF; /usr/bin/evince '%s'

Now a PDF attachment is shown using evince, when I press v on the attachment.

Hope this helps.

Enjoy Ubuntu!

Sincerely,
U N Gaitonde

---

