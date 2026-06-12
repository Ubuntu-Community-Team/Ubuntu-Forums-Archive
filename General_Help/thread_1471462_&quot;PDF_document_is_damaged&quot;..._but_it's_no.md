---
title: "&quot;PDF document is damaged&quot;... but it's not?"
date: 2010-05-03
forum: General Help
---

### Post by galacticbrain on 2010-05-03
My girlfriend recently began an online college course where most of the coursework is distributed in PDF files. Every PDF that they've sent her, without exception, refuses to load on her computer. She's using Ubuntu 10.04, and opening the files in Evince results in the following error message:

"Unable to open document. PDF document is damaged"

We get similar error messages when trying it in xpdf, gv, and the official Adobe Reader for Linux--none of them work, and they all claim the file is damaged.

This would seem to point to it actually being damaged, but not only does the file open perfectly in Windows, it opens perfectly in Evince on *my *computer, which is also running Ubuntu 10.04.

I've searched fruitlessly on the forums and the general internet, but I can't even begin to understand what the problem could be. Do any of you fine people have any ideas?

---

### Post by gvernold on 2010-05-03
Presumably your girlfriend has done all of the recent updates for 10.04 and isn't using a release candidate edition? Secondly, are you both using the same version? - I have a 64bit version on my laptop which had problems in Evince (can't get the official Adobe working properly yet) and 32bit on my desktop which opens PDF's without a problem.

Lastly, something could have gone wrong at install time with a library that both Adobe and Evince use for PDF's or rendering. If it's not too much of a hassle check the dependencies for Evince in Ubuntu Launchpad, re-install them and try again. I'm not much of a supporter of full reinstallations but as a last chance.....?

---

### Post by galacticbrain on 2010-05-03
She has all the recent updates and is using a stable release, and we're both using the same 32bit version. It seems unlikely to me that Adobe relies on any of the same libraries as Evince for PDFs; given that it's proprietary and massively bloated (150 mb) it seems to be installing all of that itself. Also, although Poppler and xpdf are closely related, I don't think gv would also share the same libraries for PDF rendering with it, nor with Adobe.

But I may be wrong and it's all I have to go on, so I'll try that and see if it helps.

---

### Post by KeyserSoze93 on 2010-05-03
Try installing imagemagick, and then running

```

convert blah.pdf blah_new.pdf

```

It will force the PDF to be converted to an image and then back into a PDF, which makes it bigger, but will force the headers to be rewritten. It might help...

---

### Post by bvvad on 2011-04-21
Hmm, I'm getting get a similar error. With some pdf files I get a "unable to open document, damaged file" error with both Adobe reader 9 and evince. A friend running windows had no problems opening the attachment from the same email. 

When I tried to use imagemagick's convert as suggested above I got another error: 
```
**** Error: Cannot find a %%EOF marker anywhere in the file.
   **** Warning:  An error occurred while reading an XREF table.
   **** The file has been damaged.  This may have been caused
   **** by a problem while converting or transfering the file.
   **** Ghostscript will attempt to recover the data.

```

perhaps I can blame my email server/client (thunderbird) for chopping off the %%EOF marker. The mystery gets deeper: if I forward the email to my gmail account, google pdf viewer also fails to open the file. 

a mystery.

---

### Post by K_45 on 2011-04-21
Would you be using a wireless connection? This might corrupt the files. Which I why I will always unfailingly use Ethernet only. There might also be a problem with the HDD or RAM.

---

### Post by dingodog on 2011-04-23
> **bvvad said:**
> Hmm, I'm getting get a similar error. With some pdf files I get a "unable to open document, damaged file" error with both Adobe reader 9 and evince. A friend running windows had no problems opening the attachment from the same email. 

When I tried to use imagemagick's convert as suggested above I got another error: 
```
**** Error: Cannot find a %%EOF marker anywhere in the file.
   **** Warning:  An error occurred while reading an XREF table.
   **** The file has been damaged.  This may have been caused
   **** by a problem while converting or transfering the file.
   **** Ghostscript will attempt to recover the data.

```perhaps I can blame my email server/client (thunderbird) for chopping off the %%EOF marker. The mystery gets deeper: if I forward the email to my gmail account, google pdf viewer also fails to open the file. 

a mystery.

many times, **xref** **table** can be reconstructed with pdftk

```
pdftk damaged.pdf output fixed.pdf
```or **repair** from 

[B]*Multivalent*
[/B]-[http://goo.gl/QGgvb](http://goo.gl/QGgvb) (latest free version with tools)

```
java -cp path...to..Multivalent.jar tool.pdf.Repair *[options]* PDF-filename
```

---

### Post by KegHead on 2011-04-23
Hi!

You could remove Adobe and evince and reinstall.

KegHead

---

### Post by justifiedandancient on 2011-06-20
I have the same problem (actually on Fedora but hey, ho) with a document sent from an HP scanner. That is scanned and sent direct to E-mail. I was using the combine multiple scans into a single file option but it really shouldn't generate damaged PDFs. Anyway, the file was reported damaged by Document Viewer, Adobe Reader and pdftk so there wasn't much I could do. However, my Adobe reader on my Windows 7 VM read it perfectly happily and when I did a save as, despite the warning about only saving a copy of the original, the saved file could be opened by any *nix application. I couldn't find any sensible explanation on google but did find this thread so thought I'd add my experiences to it as it doesn't appear to be anything to do with the Linux distro.

P.S. I did do an Adobe Reader re-install which made no difference (other than getting rid of version 8 Swedish and replacing it with version 9 English)

---

### Post by lemonchicken on 2011-06-20
Google docs viewer is worth trying.

---

### Post by jmckean on 2011-06-22
I am having a similar problem and might have a clue.  The PDFs are all coming to in emails.  I use Thunderbird IMAP. The failure occurs whether I open it from the message or save it locally and try to open it. BUT if I go to my web mail client and download it from there, it opens.  So maybe something is happening in TB?

---

### Post by mfalteten on 2011-08-26
Confirmed previous post. 
In TB, i receive "Unable to open document; PDF document is damaged"; yet, when I use webmail browser, there are no problems opening PDFs.
Plus, I went back to examine some docs that were opened originally in TB only, and I received the damage error.  However, I logged into a WIN machine to check these docs (of course, with no problems), and when I WENT BACK into TB to recheck they opened fine.

All of the docs in question are scanned PDF files.

Any experts in TB, or is there a TB thread linked with these problems?

---

### Post by britvah on 2011-11-01
I was having this issue and it led me too

[http://getsatisfaction.com/mozilla_messaging/topics/why_does_thunderbird_corrupts_pdf_file_attachments](http://getsatisfaction.com/mozilla_messaging/topics/why_does_thunderbird_corrupts_pdf_file_attachments)

The gist of it is:

Go to: Tools / Options
Go to the "Advanced" tab
Click on "Config Editor"

Look for: mail.server.default.fetch_by_chunks
Click on it to change the default to "false"

Save.

This will not fix what is already there, but in the future your pdf's should be fine.

---

