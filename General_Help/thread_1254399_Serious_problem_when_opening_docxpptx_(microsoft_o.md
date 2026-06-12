---
title: "Serious problem when opening docx/pptx (microsoft office files) with openoffice"
date: 2009-08-31
forum: General Help
---

### Post by akber on 2009-08-31
This problem occurs mostly with the ppt files because when i open them the actual powerpoint looks nothing like the original, half the text is missing, and all the pictures images and text boxes are all over the place. 

I really need this working so that i can use all the powerpoints my teachers use for notes and studying when i get home. 

Any ideas?

---

### Post by red_spyder on 2009-08-31
I actually don't use open office. I sort of missed Microsoft Office when I switched to Ubuntu. If you have a copy of Office, you can install it on Ubuntu through wine.

---

### Post by jheaton5 on 2009-08-31
> **red_spyder said:**
> I actually don't use open office. I sort of missed Microsoft Office when I switched to Ubuntu. If you have a copy of Office, you can install it on Ubuntu through wine.

Well if akber wants to use ubuntu instead of windows what's the point of telling him how to continue using windows apps?  He can go back to windows to do that.

I am using Jaunty and Open Office 3.1 from the Jaunty repositories.  Presentation opens ppt files accurately for me. 

Can you tell us more about your working environment:  ubuntu version, open offiice version, more specific information about what open office is doing.

Edit:  Oh, yes, how much memory do you have?

---

### Post by akber on 2009-08-31
I am using ubuntu 9.04 (jaunty), open office 3.0.1, and basically what open office is doing with the ppt files (usually pptx files from microsoft office 2007) is displaying them, but not very well. Text is missing, pictures are out of place, font colors are all wrong. Is there any way i can send you a few screenshots so you can look at it for yourself? I think that would be easier for you than having me describe however vaguely the problems.

---

### Post by Bucky Ball on 2009-08-31
As far as I know, .docx is specific for Microsoft Office Enterprise 2000 (think that is what it's called). That is the only time I have come across them and they were a nightmare to open in anything else (never succeeded).

You could try renaming it and taking the x of doc then try to open. See what happens.

---

### Post by akber on 2009-08-31
jheaton5: i have 1g of memory

And i am very very sure that .docx is for microsoft office 2007, and taking the x off didnt do anything. but ill give you one thing, they are a nightmare to open.

---

### Post by Bucky Ball on 2009-08-31
Back in the day I had Enterprise and couldn't open one in MS '07. They would only open in Enterprise. But who knows, I'd just never seen them before Enterprise (also a nightmare). :)

---

### Post by DavePlummer on 2009-08-31
Do you have package "odf-converter-integrator" installed? It's the latest/greatest for converting MS Office 2007 file formats.

---

### Post by akber on 2009-08-31
no i dont, and i cant find it in synaptic. i am not so great with using linux yet, mind telling me how to install the package?

---

### Post by Bucky Ball on 2009-08-31
System->Administration->Synaptic Package Manager.

Search for:

odf-converter-integrator

Click the box on the left (if it is found), 'mark for installation' then hit 'Apply'

---

### Post by fluffman86 on 2009-08-31
OpenOffice.org 3.1 has a better OOXML (docx, xlsx, and pptx) coverter.

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

---

### Post by akber on 2009-08-31
Buckyball, it isnt found, i dont know why. 

and fluffman, i followed all the directions, but the partial update part never came up and i dont think that open office 3.0 ever got removed because it keeps starting up.

Edit: although i cant access it from the applications menu, when i opened a .pptx file it opened by default with 3.1, and it still looked messed up. I guess it didnt do the trick.

---

