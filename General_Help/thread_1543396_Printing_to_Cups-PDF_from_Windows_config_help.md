---
title: "Printing to Cups-PDF from Windows config help"
date: 2010-08-01
forum: General Help
---

### Post by tecknos11 on 2010-08-01
I installed cups_pdf and I am able to print pdf files locally but not Windows.

When I connect to the PDF printer in Windows it ask for a driver so I point it to the generic Microsoft one.  I also tried some hp ones as well. When I print I don't get any errors or anything like that. The file appears in the PDF printer queue and disappears but doesn't make it to my computer. I have tried using instructions from various Internet sites but the information is vague, wants me to edit lines that don't exist in cupsd.conf, and/or adds lines that breaks the back-end scheduler to the PDF printer. Every once in a while they tell me to use a raw driver for Windows but what does that mean. 

So right now Windows can see and interact with my PDF printer but the file never gets made on the Linux machine. I have reinstalled the cups-pdf, created a pdf printer, and windows can see and connect to it but wants a driver. I am using Ubuntu 10.04 and Windows 7 and everything is up to date. What do I need to do?

---

### Post by tecknos11 on 2010-08-01
I got it to work. I don't know if it was because the reinstall, I downloaded Samba4, or I uncommitted the cups cups printer lines in the samba config file but it worked.

---

### Post by tecknos11 on 2010-08-01
I guess I still need help. I am trying to print a pdf file that uses $ealedMedia. I am trying to be able to put the document on a Nook or viewable from linux which I use for school work but the .spdf is DRM worse than any I have ever seen. 

It tries to print to the pdf printer but when it gets to 3% it stops. I try again and it says this printer seems to allow printing to file and you don't have the writes for that.

What is telling the software that it seems that the printer prints to file and how do I change it?

---

### Post by tecknos11 on 2010-08-02
Out with the old and in with the new problem. Everything works great except with the drm pdf doc I want to print. The pdf doc is created with an error on the second page. I think the problem is on the linux side. Possibly some type of drm filter that I read about somewhere. I don't know what the fix would be and my research is turning up blanks.

I'll attach it the doc with the error. The offending command is "find resource" and the error is "undefinedresource".

---

