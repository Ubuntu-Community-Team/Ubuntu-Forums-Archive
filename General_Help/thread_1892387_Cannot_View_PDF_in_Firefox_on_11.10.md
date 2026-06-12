---
title: "Cannot View PDF in Firefox on 11.10"
date: 2011-12-07
forum: General Help
---

### Post by jcobban on 2011-12-07
I desperately need a solution to the inability to view PDFs in Firefox on 11.10.  There are two key problems which have been reported in other postings:
[LIST=1]
[*]The document will not reliably open.  The tab will indicate completion, but the contents are blank.  Pressing refresh over and over and over and over again may eventually display the document.
[*]The Gnome 3 scroll bars move in response to mouse actions but the image does not move.  It is still possible to scroll vertically using the mouse wheel, but there is no solution for horizontal scrolling.
[/LIST]
I have tried the suggested alternative of installing Google docs and gPDF, but Firefox still insists upon invoking AcroRead.

I need to solve this problem because a site that I depend upon for images has packaged them as PDFs, even though this is a waste of resources for users and causes unnecessary document reloads from their servers (because Firefox does not cache PDFs locally the way it does normal image files).  The site's justification is that IE's image support is brain-dead and most of their customers are using IE.  In particular the clients want more control of zoom levels than is provided by the raw image support in the browser, which basically provides only "fits the window" or 100%.

I need this solved yesterday!

---

### Post by llamabr on 2011-12-07
Hi.  I'm not sure I quite understand your problem.  When you find a link to a pdf in a web browser, firefox should ask you how you want to open it.  If you choose default, you should get evince.  Does evince show your document correctly?

If not, you should also have the option of using anything else you like.  You mentioned gpdf. I prefer xpdf.  Do either of those work?  Why do you think you're stuck with acroread?

Then, you say:

```
The Gnome 3 scroll bars move in response to mouse actions but the image does not move. It is still possible to scroll vertically using the mouse wheel, but there is no solution for horizontal scrolling.
```
I don't use gnome3, so I can't recreate this.  But are you saying that this is a acroread problem, or a firefox problem?

It would help to begin troubleshooting your problem to move one step at a time.  We can definitely solve this yesterday.  But I think it'll take some walking through.

---

### Post by jcobban on 2011-12-07
> **llamabr said:**
> Hi.  I'm not sure I quite understand your problem.  When you find a link to a pdf in a web browser, firefox should ask you how you want to open it.  If you choose default, you should get evince.  Does evince show your document correctly?

If not, you should also have the option of using anything else you like.  You mentioned gpdf. I prefer xpdf.  Do either of those work?  Why do you think you're stuck with acroread?

Firefox does not give me an option.  It simply pops up acroread.  I cannot even find evince.  

By stuck I mean even after I have installed gPDF I **still** am not given any option when I click on the link to the URL of the PDF.  When I look at the media type association for media/pdf in Firefox it still points at acroread. If I save the document to a file and right click on it the only option I am given for opening the document is Acroread.  That is capital **S** stuck in my mind.  If I directly invoke the Document Viewer from the list of applications I can then open the PDF file in the viewer, but I am not given that choice when I am clicking on the file icon itself.

> **llamabr said:**
> 
Then, you say:

```
The Gnome 3 scroll bars move in response to mouse actions but the image does not move. It is still possible to scroll vertically using the mouse wheel, but there is no solution for horizontal scrolling.
```
I don't use gnome3, so I can't recreate this.  But are you saying that this is a acroread problem, or a firefox problem?

It would help to begin troubleshooting your problem to move one step at a time.  We can definitely solve this yesterday.  But I think it'll take some walking through.

The lack of support of gnome 3 (which is integral to Ubuntu 11) is in Acroread, since the problem occurs whether I view the document through the Firefox plugin or by directly opening the file.  But then why would anyone expect Adobe to take the time to support gnome 3 when Ubuntu 11 is about the only platform on the market that uses it?  Perhaps if there were some way that I could tell Ubuntu to fall back to gnome 2 when invoking this specific application I could get it to work.

---

### Post by bsniadajewski on 2011-12-07
Try uninstalling acroread:

```
sudo apt-get purge acroread
``` 

It seems that file associations were set such that PDFs are set to always open with Adobe Reader.  Is ther a way to access file association settings in GNOME?

---

### Post by jcobban on 2011-12-08
> **bsniadajewski said:**
> 
It seems that file associations were set such that PDFs are set to always open with Adobe Reader.  Is ther a way to access file association settings in GNOME?
I have now set the default opener for PDF files to "Document Viewer".  That simplifies the process for downloaded PDF files.

I still cannot break the association of media/pdf to Acroreader in Firefox.

---

### Post by mike555 on 2011-12-08
Can't you change the preferences in Firefox ?   by clicking on Edit > Preferences > Applications tab.

---

### Post by gordintoronto on 2011-12-08
Why don't you download the PDFs and view them in your choice of viewer from your Downloads folder?

---

### Post by rewyllys on 2011-12-08
> **mike555 said:**
> Can't you change the preferences in Firefox ?   by clicking on Edit > Preferences > Applications tab.

+1 for Mike555's suggestion. 

Alternatively: Open Firefox; go to File > Open file; click on a ".pdf" file on your system; Firefox will offer Document Viewer as a suggested option; select that option and see if Document Viewer satisfies you; if not, find a PDf-viewer  application that does satisfy you, and then use Mike555's suggestion.

---

