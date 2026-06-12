---
title: "Wine printing help"
date: 2010-01-01
forum: General Help
---

### Post by gatliff on 2010-01-01
I have a Window Adobe Acrobat Pdf doc I have to used wine to open it read fine but won't print 
it only print line after line of letters and numbers nothing readable the printer is fine in linux 
How do I get this doc to print? 
I want to print out not print to pdf this doc:confused:

---

### Post by Pollox on 2010-01-01
You installed Acrobat Reader in wine to open a pdf?  Why not just use the built-in pdf reader for Ubuntu, evince?  Or install acroread for linux.

---

### Post by gatliff on 2010-01-01
The doc is part of a window program can only use wine Adobe Acrobat came with it and have to be install to read the doc

---

### Post by Pollox on 2010-01-01
What type of file is this exactly?  A .pdf?  A .doc?  How is it "part of a window program"?  If it can open in Acrobat Reader under wine, it should open under Acrobat Reader running natively in linux, and you'd probably have better luck printing that way.

---

### Post by northrup on 2010-01-01
I would print to a PDF, then print the new PDF using one of Ubuntu's own PDF viewers.  Or just find the original PDF in the program's files.

---

### Post by gatliff on 2010-01-01
The doc is shop manual in pdf format it was a download  .exe file that why I have to used wine

---

### Post by Loan_Refi on 2010-03-08
You can print form Adobe Acrobat! Here is what you need to do;

A. Open your document to be printed with Adobe Acrobat
B. Chose Print, on your print screen choose "Advance" at the bottom left corner.
C. On your left hand column select "PostScript Options" and make sure you check print as Image Box.

Done!

Now you can print to any printer! Just make sure you follow the steps when print to different printers such as PDF, HP, Ricoh, Savin etc........

I searched everywhere for a solution to this issue but didn't find anything until I started playing with the settings of Acrobat on my own.  I knew there had to be a way since we can print from IE or any MS Windoze ofise application running under wine.

Another thing I found out is that encrypted PDF's can be printed with Ubuntu's default document viewer and the encryption is removed. Then you can manage the document anyway you want like editing text signing and encrypting again!! Weird but who cares, I like it cause I have control over all the documents that come my way. Ubuntu + Wine & Adobe Acrobat = Paperless Environment!!

Whomever is reading this, in case you need to create a signature for your self to sign PDF documents as if you did by hand do the following;

Requirements; Ubuntu, Scanner, GIMP Image Editor

First Set of Steps
A. Sign a blank document they way you normally sign your name
B. Scan the signed document and open it in Ubuntu with GIMP or
From Gimp, File->Acquire->Sane to create an image of the signature.
C. Rightclick, Image->Alpha->Add alpha channel, in order to make this layer transparent.
D. Rightclick, Select->By color.
E. In the image, click in the white portion, in order to select everything white.
F. Rightclick, Edit->Clear, in order to clear selected material to transparent.
G. Rightclick, Select->None, in order to clear all selections. 

You now have the signature on a transparent background, and are ready to save.

2nd Set of Steps
A. Save the image as Example.png
B. Open Adobe Acrobat and select Comments>Commenting Tools>Stamps>Manage Stamps and Select "Create" then brows for the file you saved Example.png Select a Category, Give it a Name and you're done.
C. Open any document you wish to sign, go to Comments>Commenting Tools>Stamps>Signatures or (Category you Created) now stamp your signature anywhere you want. 

BEFORE YOU EMAIL YOUR SIGNED FORM/DOCUMENT Print it, if you don't the person who gets your signed document will delete or modify your signature.  

Select Print, Choose PDF, and Document & Markups - Now Your're Done!! Email or Print your document.

If you don't know how to use the typing tool build in Adobe Acrobat learn to use it;

Tools>Advanced Editing>TouchUp Tex Tool

Point your cursor over the line you wish to start typing and press & hold Ctrl button then click left mouse button to active typing.  That's it!!

Lets not kill trees if we don't have too.

Enjoy!!! Viva Ubuntu!!

---

