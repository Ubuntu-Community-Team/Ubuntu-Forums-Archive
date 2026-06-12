---
title: "Sign PDF"
date: 2009-09-08
forum: General Help
---

### Post by Rackstar on 2009-09-08
Hi everyone,

Hope someone can help me with this one:

I was asked to sign a contract (pdf) digitally. Now, what do they actually mean with sign it digitally? I guess I have to sign it with my electronic identity card.

What I already have:
- Cardreader and Belgian eID card.
- I can read my card and use it without any difficulties on tax-website etc

Now, how do I sign the PDF?

I tried following instructions on this page:
[http://my.oltrans.org/en/ubuntu-faqs/41-customizing/74-digital-signature-and-signing-pdf-documents.html](http://my.oltrans.org/en/ubuntu-faqs/41-customizing/74-digital-signature-and-signing-pdf-documents.html)

But they ask this:
> Save a copy of the root certificate of the authority that issued your signing certificate, rename it as CA.cer, and put it in the root directory of the project.
What do they mean with that?


Thanks!

---

### Post by Brandon Williams on 2009-09-08
Are you viewing the PDF with Acrobat Reader? and if so, which version?

I am running Jaunty and using Acrobat 9.1.3 from the Ubuntu partners repo. I have been asked to digitally sign PDFs twice, and in both cases, when I open the PDF with this version of Acrobat Reader, there is a menu item for signing the document: Document -> Sign -> Sign Document. There is also a clickable 'electronic signature' item somewhere in the document. When I click on that item or select the menu entry, a window pops up asking me for more information about how I want to sign. One of the items I can select is "A device connected to this computer", which could work with you eID card reader. I don't have such a card, so I can't be certain that this will work for you.

You can find out more information about digital signatures in acrobat reader [here](http://help.adobe.com/en_US/Acrobat/9.0/Standard/WS58a04a822e3e50102bd615109794195ff-7d4c.w.html).

---

