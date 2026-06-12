---
title: "Unable to open pdf's in Thunderbird before saving"
date: 2010-07-06
forum: General Help
---

### Post by wmcbecker on 2010-07-06
I just upgraded to Lucid from Karmic and that is when this issue started.  In order to open some attachments to emails (I'm using Thunderbird) I have to save them first.  Didn't have to do that before.  Can't find a preferences setting in Thunderbird to change it.

Any ideas anyone? 

Thanks

---

### Post by d_liebscher on 2010-07-06
Hi,

what version of Thunderbird do you use 2.x or 3.x?

Regards Daniel

---

### Post by wmcbecker on 2010-07-06
I'm using v3.0.4 




> **d_liebscher said:**
> Hi,

what version of Thunderbird do you use 2.x or 3.x?

Regards Daniel

---

### Post by virtual_najac on 2010-07-07
Here is how it worked for me.

The trouble is that some mail programs send attachments with a nonspecific content type: "application/octet-stream or application/x-msdownload" instead of "Content-Type: application/pdf" (see message source with Crtl-U without opening the email).

To work around this send yourself an e-mail to which you manually attached the pdf file. (Do not forward the email whose attachment caused the box to be disabled.) Then open the attachment and choose how you want Thunderbird to open it. Check the box "Do this automatically for files like this from now on".

After that go to menu /Edit/Preferences/attachments and you'll find an attachment-handling action for PDF documents associated to "Documents Viewer (Default). Just change this association (choose "Use other...") and choose /usr/bin/evince.

That's all

---

### Post by wmcbecker on 2010-07-07
Many thanks.  It worked! 

> **virtual_najac said:**
> Here is how it worked for me.

The trouble is that some mail programs send attachments with a nonspecific content type: "application/octet-stream or application/x-msdownload" instead of "Content-Type: application/pdf" (see message source with Crtl-U without opening the email).

To work around this send yourself an e-mail to which you manually attached the pdf file. (Do not forward the email whose attachment caused the box to be disabled.) Then open the attachment and choose how you want Thunderbird to open it. Check the box "Do this automatically for files like this from now on".

After that go to menu /Edit/Preferences/attachments and you'll find an attachment-handling action for PDF documents associated to "Documents Viewer (Default). Just change this association (choose "Use other...") and choose /usr/bin/evince.

That's all

---

### Post by jdp75495 on 2010-12-18
Using 10.04 LST
I corrected this problem for myself by loading package  'adobereader-deu' in the Synaptic Package Manger.
I hope this helps.

---

### Post by bleverett on 2011-02-03
> **virtual_najac said:**
> Here is how it worked for me.

The trouble is that some mail programs send attachments with a nonspecific content type: "application/octet-stream or application/x-msdownload" instead of "Content-Type: application/pdf" (see message source with Crtl-U without opening the email).

To work around this send yourself an e-mail to which you manually attached the pdf file. (Do not forward the email whose attachment caused the box to be disabled.) Then open the attachment and choose how you want Thunderbird to open it. Check the box "Do this automatically for files like this from now on".

After that go to menu /Edit/Preferences/attachments and you'll find an attachment-handling action for PDF documents associated to "Documents Viewer (Default). Just change this association (choose "Use other...") and choose /usr/bin/evince.

That's all

At /Edit/Preferences/attachments, there is a table in which the left column is "Content type" and the right column is "Action".  There are two rows, one for content type "PDF document" and the other for content type "Word document".  The action for "PDF document" is "Use Adobe Reader 9 (default)".  I tried to change this to evince, but that broke all .pdf attachments, both those with the right content type and those with the nonspecific content type; nothing opens at all.  So I changed it back to Adobe Reader 9, but when I try to open an attachment with a nonspecific content type, I get an error box saying, "... could not be opened, because the associated helper application does not exist."  What am I missing?  Thanks.

---

