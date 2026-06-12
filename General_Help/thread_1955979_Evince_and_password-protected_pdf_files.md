---
title: "Evince and password-protected pdf files"
date: 2012-04-10
forum: General Help
---

### Post by vasa1 on 2012-04-10
Evince (Document Viewer) allows one to unlock a password-protected file "forever". However, this unlocking appears specific to Evince. In other words after "unlocking forever", It seems I can subsequently reopen the PDF file without entering the password but **only** with Evince. For example, the built-in PDF reader in Google Chrome still needs the password and pdf.js in Firefox currently just throws up an error.

Does anyone know if there's a program to unlock PDF files once and for all so that PDF readers other than Evince can open them?

---

### Post by pwoo on 2012-04-14
Evince stores a private use password in the key ring (ring file "login" for my case in Ubuntu 11.10, accessible via seahorse).  I guess only Evince can use the stored password.  However, there would be one entry per document so if you use this feature for a lot of documents, you would end up with a very fat login ring...

---

### Post by callmemahavir on 2012-04-15
Refer the URL...

[http://www.cyberciti.biz/faq/removing-password-from-pdf-on-linux/](http://www.cyberciti.biz/faq/removing-password-from-pdf-on-linux/)

---

### Post by vasa1 on 2012-04-15
> **pwoo said:**
> Evince stores a private use password in the key ring (ring file "login" for my case in Ubuntu 11.10, accessible via seahorse).  I guess only Evince can use the stored password.  However, there would be one entry per document so if you use this feature for a lot of documents, you would end up with a very fat login ring...

So if I understand correctly, 
[list][*]Evince remembers the password so that I don't have to enter it when I open the file on a subsequent occasion. [*]And this stored password is accessible only to Evince. [*]And that's why the other pdf readers still need a password.
[/list]

Appreciate that!

@mahavir, I had seen that link. It had four options. The first required Java. I would prefer an option without Java.
The fourth option works but the resulting file was significantly larger than the original. I haven't got round to trying options #2 and #3.

Edit: the original file was 86.7 kB. After using the fourth option, the output.pdf was 368.2 kB but it could be opened without need of a password.

Edit: qpdf did the job perfectly. Thanks! Marking as solved.

---

### Post by justdotait on 2012-06-07
You could try to use Wondershare pdf password remover.
[http://www.pdfpie.com/product/wondershare-mac-pdf-password-remover.html](http://www.pdfpie.com/product/wondershare-mac-pdf-password-remover.html)

> **vasa1 said:**
> Evince (Document Viewer) allows one to unlock a password-protected file "forever". However, this unlocking appears specific to Evince. In other words after "unlocking forever", It seems I can subsequently reopen the PDF file without entering the password but **only** with Evince. For example, the built-in PDF reader in Google Chrome still needs the password and pdf.js in Firefox currently just throws up an error.

Does anyone know if there's a program to unlock PDF files once and for all so that PDF readers other than Evince can open them?

---

