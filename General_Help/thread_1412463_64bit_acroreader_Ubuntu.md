---
title: "64bit acroreader Ubuntu"
date: 2010-02-21
forum: General Help
---

### Post by thebigob on 2010-02-21
Hi all looking to install acroread in 64 bit ubuntu.

uname -a:

 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

I have added medibuntu to my repo but cant install acroread.

Any ideas welcome.

Cheers

---

### Post by gmargo on 2010-02-21
Acroread is not in the medibuntu repository.  This stuff is: [http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

Googling, I found this but have not tried it myself: "**[Install acrobat reader in Ubuntu 9.10 (Karmic)]("http://www.ubuntugeek.com/install-acrobat-reader-in-ubuntu-9-10-karmic.html")"** ([http://www.ubuntugeek.com/install-acrobat-reader-in-ubuntu-9-10-karmic.html)]("http://www.ubuntugeek.com/install-acrobat-reader-in-ubuntu-9-10-karmic.html")

---

### Post by coffeecat on 2010-02-21
> **thebigob said:**
> I have added medibuntu to my repo but cant install acroread.

It certainly used to be in Medibuntu, but not any more I fear. In fact it is easily installable via Synaptic.

Open Synaptic, then Settings > Repositories > "Other Software" tab and tick the "http://archive.canonical.com/ubuntu karmic partner" line. Do a 'Reload' and Acroread should appear in the package list. This is for 64-bit.

**Edit:** in fact you need to go to Medibuntu for the package acroread-fonts, which you need if (from the package description):

> These fonts are needed by Acroread to correctly display a document when an author does not embed the appropriate font in to the document. 

---

### Post by mechro on 2010-02-21
Either add **archive.canonical.com** to your sources list or choose your .deb package from here...

[http://archive.canonical.com/ubuntu/pool/partner/a/acroread/](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/)

---

### Post by thebigob on 2010-02-24
Brilliant thanks all for the replys!!!!!

---

