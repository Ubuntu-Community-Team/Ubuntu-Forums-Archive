---
title: "pdf edit does not work features are missing ubuntu 10.10"
date: 2011-08-08
forum: General Help
---

### Post by AgentZ86 on 2011-08-08
Hi

pdf edit has missing features.

lots of greyed out features and cannot add text to pdf's as I once did in previous version of Ubuntu

Using ubuntu 10.10 64bit version.

Anyone else noticed this problem

---

### Post by Kira_Belka on 2011-08-08
> **AgentZ86 said:**
> Hi

pdf edit has missing features.

lots of greyed out features and cannot add text to pdf's as I once did in previous version of Ubuntu

Using ubuntu 10.10 64bit version.

Anyone else noticed this problem

hi.. mmmm type in terminal apt-get install pdfedit
have a lot of fun:popcorn:

---

### Post by scorp123 on 2011-08-08
I'd use the "pdfimport" plugin for LibreOffice / OpenOffice and edit PDF's that way ...

```
> apt-cache search pdfimport

openoffice.org-pdfimport - OpenOffice.org extension for importing PDF documents
libreoffice-pdfimport - LibreOffice extension for importing PDF documents
```

So for OpenOffice, you'd install this:
```
sudo apt-get install openoffice.org-pdfimport
```

If you have LibreOffice you'd install this:
```
sudo apt-get install libreoffice-pdfimport
```

---

### Post by AgentZ86 on 2011-08-08
WHoa, never used the Open office version of this REALLY NICE !

A little slow importing and opening the document and it opens it as a OpenDRAW but it's still cool

as far as apt with the edit pdf I didn't try that and went with the OpenOffice option this time.

But I used edit PDF for years and never had a problem with it, and even uninstalled with synaptic and then reinstalled and same thing.

The edit features are sort of disabled / turned off for some reason


Thanks all for the help. 

I am still curious what happened to the edit pdf thing but at least I got an option for pdf editing when one thing fails another works lol

---

### Post by pietro_spina on 2011-09-15
any other alternatives out there?

the LibreOffice extension doesn't function properly for me.
(it screws up the margins on many of the pages I try to add to the PDF.)

what I want to be able to do is "Add, delete, rotate, resize, reorder pages" also it would be great if I could add annotations.

---

