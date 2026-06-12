---
title: "Create read only pdfs?"
date: 2009-10-16
forum: General Help
---

### Post by mikkeX on 2009-10-16
Is there a tool to easy create read-only pdfs? I have a bunch a pdf files I would like to convert.

---

### Post by XCan on 2009-10-16
I think pdftk can do it. ```
 pdftk mydoc.pdf output mydoc.128.pdf owner_pw foopass 
```

---

### Post by mikkeX on 2009-10-16
> **XCan said:**
> I think pdftk can do it. ```
 pdftk mydoc.pdf output mydoc.128.pdf owner_pw foopass 
```
No, this do not create an read-only pdf.

---

### Post by XCan on 2009-10-16
Too bad, read the manual, it's in there somewhere.

---

### Post by kaibob on 2009-10-16
Post deleted by kaibob.

---

### Post by mikkeX on 2009-10-18
> **XCan said:**
> Too bad, read the manual, it's in there somewhere.
I have read the manual, that is why I am asking - I can't find a way of doing this with pdftk or PDF editor.

---

### Post by jamesy on 2009-10-18
You can just use chmod to change the permissions of the file. try

[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

as a starting point. This can certainly make a file read only but is probably not quite what you're after... Just my $0.02

---

### Post by mikkeX on 2009-10-18
No, that is not what I am after. I want to create read only pdf's like you could do in Acrobat - everybody can view a pdf, but nobody get the permisssion to print it.

---

### Post by niteshifter on 2009-10-18
> **mikkeX said:**
> I have read the manual, that is why I am asking - I can't find a way of doing this with pdftk or PDF editor.

Must have missed this part:
> [allow <permissions>]
    Permissions are applied to the output PDF only if an encryption strength
    is specified or an owner or user password is given.  [B]If permissions are
    not specified, they default to 'none,' which means all of the following
    features are disabled.[/B]

The permissions section may include one or more of the following 
features:

Printing
    Top Quality Printing
DegradedPrinting
    Lower Quality Printing
ModifyContents
    Also allows Assembly
Assembly
CopyContents
    Also allows ScreenReaders
ScreenReaders
ModifyAnnotations
    Also allows FillIn
FillIn
AllFeatures
    Allows the user to perform all of the above, and top quality printing.


So ...
```
pdftk mydoc.pdf output mydoc.128.pdf allow owner_pw foopass
```
produces a locked-down pdf - no printing, copying, modifying, assembly, etc.

---

### Post by juancarlospaco on 2009-10-18
Theres no read-only PDF, all PDF can be edited and printed on Ubuntu :)

---

### Post by niteshifter on 2009-10-18
Hi,

Now that I have more time and can give a more complete response ...

Content in a PDF has very little security:

Adobe Reader (any OS) will pay attention to the security settings. PDFedit will open but won't display anything or just garbage.

The "security" provided by the above is an illusion. As:

GNOME's Evince will allow selection and copy, but won't print. 

pdftops will open and convert, no problem. ps2pdf will make another pdf that will pass visual inspection. The new pdf file will have a different DOC_ID from the original (but can be reset with pdftk).

pdftotext will open and convert, no problem. In fact most all the pdf* tools will work.


Credentials can have better security:

Cracking (via pdfcrack, in order to get the actual passwords) can be quick or very time consuming, depends upon number of bits used and password quality. 128 bits and a high quality (read: very random and long) password: You can tie a fast machine up for days.

As the OP didn't say what the target reader and OS was his request for locking down a pdf was answered. I just hope he's not betting the farm on this "security". If he's worried about unauthorized alteration, he should at least checksum his files (md5sum) or better still, generate gpg signatures on the files. And get used to the notion that the content can't be locked down.

---

### Post by HermanAB on 2009-10-19
Xpdf will cheerfuly ignore all those annoying restrictions.  :)

Also, anyone with a text editor can delete (or just mangle) the stanza with the restrictions and then any PDF reader will ignore it.

---

### Post by kaibob on 2009-10-19
I think the command line suggested by XCan does indeed remove print, copy, change, and addNote permissions, which is what I believe the OP means by "read only." At least, the pdfinfo utility indicates that this is the case (see example below). Unfortunately, as others have indicated, secured PDF's are not really secure. For example, I was able to open mydoc.128.pdf in Evince and print the document without issue. 

You can add a user password, which I believe is a bit more secure or at least it is not ignored by Evince. But, that's not what the OP is after. Another alternative is to use the GUI for pdftk. I don't believe this will make the PDF any more secure, but at least there is a GUI with clear options.

[http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html)

> $ pdftk mydoc.pdf output mydoc.128.pdf owner_pw foopass
$ pdfinfo mydoc.128.pdf
Title:          <deleted>
Author:         (kaibob)
Producer:       GPL Ghostscript 8.64
CreationDate:   Wed Oct  7 18:15:36 2009
ModDate:        Wed Oct  7 18:15:36 2009
Tagged:         no
Pages:          1
Encrypted:      yes (print:no copy:no change:no addNotes:no)
Page size:      612 x 792 pts (letter)
File size:      36918 bytes
Optimized:      no
PDF version:    1.4

---

### Post by mikkeX on 2009-10-19
Ups sorry, both missed that part in the manual and did wrong with the command suggested. So yes, now I do have a read only pdf. Thanks!

---

