---
title: "LibreOffice artifacts"
date: 2011-02-21
forum: General Help
---

### Post by Foxcow on 2011-02-21
Has anyone else experienced strange artifacts?

A lot of my math work comes in .doc or .docx form and there are a lot of anomalies/artifacts in every document I open.

[IMG]http://i.imgur.com/rm40r.png[/IMG]


Is there a way to fix this?  For what its worth, I don't have this problem in Windows 7.

---

### Post by ubuntu27 on 2011-02-21
Hi Foxcow :)

You said that you do not have that problem on Windows OS. Are you using LibreOffice in Windows as well?

Then, it might be a font problem. Select all, and change to another font such as Times New Roman or Linux Libertine.

Another option is to open the doc file under [Google Docs]("https://docs.google.com") and download it as ODF or PDF.

Lastly, ask the sender to send the files in PDF formats.


EDIT: Could you attach one file for us to test it?

---

### Post by Foxcow on 2011-02-21
Hello,

I am using LibreOffice in Windows as well.  Changing the fonts didn't change the artifacts either.  Maybe I messed something up during install?  Here is a side by side comparison:

Ubuntu:

[IMG]http://i.imgur.com/KI1nq.png[/IMG]


Windows 7:

[IMG]http://i.imgur.com/o4DRx.png[/IMG]

---

### Post by Foxcow on 2011-02-21
Download link for the original file:

[Chapter2ReviewSol.doc - 306.0 KB](http://uploading.com/files/ffabe316/Chapter2ReviewSol.doc/)



edit:  No luck with Google Docs either.  Instead of artifacts, there is a lot of whitespace where symobols are supposed to be.

---

### Post by emarkay on 2011-02-21
I see the same thing.
I have:
"LibreOffice 3.3.0 
OOO330m19 (Build:6)
tag libreoffice-3.3.0.4, Ubuntu package 1:3.3.0-1lucid1"

First, why saved as a ".doc" and not an ".odf" file?

This is an "OLE-Object".  Isn't that  a Microsoft only thing? Google shows many hits on "OLE-object, openoffice" and issues thereof.

I get a "General Error" when I try to Activate it - don't know what that is for, but...

Did you use LibreOffice Math to create this? Was this document created natively in OO/LO or converted?

May want to post this in the official LO forum, too:
[http://nabble.documentfoundation.org/LibreOffice-f1639495.html](http://nabble.documentfoundation.org/LibreOffice-f1639495.html)

Sorry  I couldn't be more help.

---

### Post by ubuntu27 on 2011-02-21
Hmmm. I cannot change it either. I will open it in Windows later.

You might want to post your question at [LibreOffice forums]("http://nabble.documentfoundation.org/LibreOffice-f1639495.html") and [OpenOffice.org forum]("http://user.services.openoffice.org/").

A little trick/guide for everyone: [Converting OpenOffice documents to PDF or HTML, as a batch]("http://openoffice.blogs.com/openoffice/2010/07/converting-openoffice-documents-to-pdf-or-html-as-a-batch.html")

---

### Post by Foxcow on 2011-02-21
> **emarkay said:**
> I see the same thing.
I have:
"LibreOffice 3.3.0 
OOO330m19 (Build:6)
tag libreoffice-3.3.0.4, Ubuntu package 1:3.3.0-1lucid1"

First, why saved as a ".doc" and not an ".odf" file?

This is an "OLE-Object".  Isn't that  a Microsoft only thing? Google shows many hits on "OLE-object, openoffice" and issues thereof.

I get a "General Error" when I try to Activate it - don't know what that is for, but...

Did you use LibreOffice Math to create this? Was this document created natively in OO/LO or converted?

May want to post this in the official LO forum, too:
[http://nabble.documentfoundation.org/LibreOffice-f1639495.html](http://nabble.documentfoundation.org/LibreOffice-f1639495.html)

Sorry  I couldn't be more help.



I think I will post it in the LibreOffice forum.  Thanks.


The entire school thus the professor uses Office 2007.  Every document that we get from the professors these days is a .doc or .docx file.

---

### Post by keithpeter on 2011-02-21
Hello

Desparate work around: save as PDF in Windows. Then you can at least read it on Ubuntu.

---

### Post by emarkay on 2011-03-04
> **Foxcow said:**
> The entire school thus the professor uses Office 2007.  Every document that we get from the professors these days is a .doc or .docx file.

Viva Duh Revoulutionz, or maybe, Death to the Capitalist Sheep! 
("Hurrah! Hurrah!")
  
Educate your professor on the merits and global savings of Open Source.

Expose the Microsoft blackmail inherent in Higher Ed (hint, it's the same thing as Coke and Pepsi putting soda machines in elementary school lunchrooms); convince the student body to forsake the graft and corruption of cheap software licenses, and use FREE and OPEN SOURCE licenses!

Protest the wasted time in Win Updated and anti-malware updates. 

Leave Ubuntu CD-ROMS all over campus. 

Start a FOSS club, newsletter and Frat.  Write a letter to the editor, calls the local news channel.  Stand up for your Rights (and Lefts, too!) 

Make your Campus an example of the 21st century!  (Cue the patriotic music!)

Or, at least, if all else fails, find a friend with that Win stuff and export the files in a few formats and find what works best.

Peace!

---

### Post by grahammechanical on 2011-03-04
You say that changing fonts did not work. Find out if Office 2007 is using unicode fonts. LibreOffice does. 

I have documents that I created in windows using a truetype font that gave Greek characters. But the font was not unicode so if I change the font in the document to freeserif, for example, then the words do not display correctly. I am slowly retyping these words to be in a unicode font such as freeserif which has all the characters for many languages built in unlike the old style Microsoft truetype fonts.

You might need to install some Microsoft unicode fonts. In Synaptic Package Manager you will find something called ttf-mscorefonts-installer. That will install free fonts supplied by MS. So, you will have the same fonts on your system as those that your professor uses. It might fix it.

Regards.

---

### Post by Foxcow on 2011-03-05
> **grahammechanical said:**
> You say that changing fonts did not work. Find out if Office 2007 is using unicode fonts. LibreOffice does. 


nevermind, I re-read what you posted...  I will check it out.

---

### Post by Foxcow on 2011-04-17
Here is a link to the thread in the LibreOffice forums.  No solution yet but...

[http://en.libreofficeforum.org/node/542#comment-1587](http://en.libreofficeforum.org/node/542#comment-1587)

---

### Post by Foxcow on 2011-05-04
I just upgraded to 11.04 and was disappointed to find that the problem still persists.  I'm stumped...

---

### Post by Foxcow on 2011-06-05
I'm pleased to announce that for the most part, the artefacts have gone away with the release of LibreOffice 3.4.

Rather than wait for the PPA to be updated, I completely removed LibreOffice, downloaded 3.4 from the site, and followed installation instructions.


Voila!

[IMG]http://i.imgur.com/IBW2N.png[/IMG]

There is one little artefact in the entire document but I'm happy nonetheless!

---

