---
title: "Printing to PDF"
date: 2010-05-10
forum: General Help
---

### Post by ali999 on 2010-05-10
I am looking for a program for Lucid Lynx that can print documents to pdf, similar to CutePDF for windows. Does anybody know what is the best program out there to do this?

---

### Post by Chronon on 2010-05-10
If you install cups-pdf you should be able to print directly to PDF.

---

### Post by Scunnered on 2010-05-10
I am not sure exactly what you require this for.  If it is as simple as a spreadsheet or a word processor then Open Office will export their out put as PDFs.

Might be worth a look

---

### Post by Jose Catre-Vandis on 2010-05-10
+1 for cups-pdf
```
sudo apt-get install cups-pdf
```
then try to print from any application and PDF Printer will be in your printer selections.
Saves to ~/home/<user>/PDF

---

### Post by ali999 on 2010-05-10
When trying to install cups-pdf, i get the following error message:

```
Setting up cups-pdf (2.5.0-12) ...
 * Reloading Common Unix Printing System: cupsd         [fail]

```

I'm not really sure what this means. Any ideas?

Also how exactly can openoffice export to pdf? I can't seem to find the option for that anywhere. It is not under save as type, which is where I would figure it would have been.

---

### Post by Portmanteaufu on 2010-05-10
In OpenOffice Writer:

File --> Export to PDF

---

### Post by kingrolo on 2010-05-11
I've just got cups-pdf working....almost. If I print a text file using "lp file.txt" all is good, but if I try to print a rtf file (created in MSWord) it prints the raw file contents in text format. Can't 'lp' handle rtf files? (My server is headless so no open office installed.)

PS. Sorry if I'm hijacking this thread ;)

---

### Post by dakkar9999 on 2010-05-12
Same problem.  Can't seem to get the pdf printer to work.  It's there alright and if I run the install command, it says everthing is up to date.  But nothing shows up.  I've looked into the /home/pdf folder, but nothing is in it.

I would really like to have a working pdf printer...

---

### Post by PerfectReign on 2010-05-12
If you add the cups-pdf printer it should work.  (I don't have 10.04 as I'm still on 9.1 but I don't imagine things have changed much.)

See this blog: [http://embraceubuntu.com/2006/03/23/print-to-pdf-using-cups-pdf/](http://embraceubuntu.com/2006/03/23/print-to-pdf-using-cups-pdf/)

A little old but you'll get teh idea.

As for me, I just choose "Print to File" from the Print dialog box:

[IMG]http://www.perfectreign.com/stuff/2010/print2file.png[/IMG]

---

### Post by captainron042 on 2010-05-12
From What I've gathered, it HAS changed.

BTW, some people like to print other things besides OpenOffice documents to PDF

mine isn't working either. I've followed the directions at the link below, but this didn't work. After trying to reinstall cups, I now have two pdf printers (PDF & PDF1) and neither of them work. 

[http://www.qc4blog.com/?p=917](http://www.qc4blog.com/?p=917)

I get an error that says "Printer configuration error", and "There is a missing print filter for printer 'PDF'"

I get the same error using "print to file"

---

### Post by efflandt on 2010-05-12
Some people apparently have been having trouble with cups not running, but cup-pdf installed from Synaptic works fine for me in 64-bit Lucid, same as it always has.  Note that the dir it puts them in is ~/PDF (caps).

The 1st file was a text file printed as pdf from gedit, and the 2nd was printed from Firefox:

```
efflandt@efflandt-lucid64:~$ ls -al ~/PDF
total 704
drwx------  2 efflandt efflandt   4096 2010-05-12 22:11 .
drwxr-xr-x 35 efflandt efflandt   4096 2010-05-12 22:15 ..
-rw-------  1 efflandt efflandt  48424 2010-05-12 22:07 System-info.pdf
-rw-------  1 efflandt efflandt 657918 2010-05-12 22:11 Ubuntu_10_04_LTS_Release_Notes___Ubuntu.pdf
```

---

### Post by captainron042 on 2010-05-13
It worked fine for me with other versions, but I'm still not finding a fix for it.

I'd also like to get rid of the redundant PDF in my printer list. :/

---

### Post by DeMus on 2010-05-13
I just did a clean install of Ubuntu Lucid without anything extra concerning printing. When I want to print something I choose ctrl-P and see my printer and a choice which says Print to file.
I choose that, select where I want it and what the name should be and I get a nice pdf file. Don't understand you have to install something extra and still it doesn't work.

---

### Post by dakkar9999 on 2010-05-13
Yes, but I would need a pdf printer because of windows software running under wine.

---

### Post by r m h on 2010-05-13
I've never had an issue printing to a PDF file from within Ubuntu.  

Do I sense that you are trying to print to a PDF file from within a Windows application under WINE?  Then you may need to install a Windows app that works within WINE that prints to PDFs.

see [http://ubuntuforums.org/archive/index.php/t-138507.html](http://ubuntuforums.org/archive/index.php/t-138507.html) for more information.

---

### Post by PerfectReign on 2010-05-15
I just took the plunge and updated successfully to 10.04 from 9.1 today.  

I tried printing to PDF first thing.  No problems. I get the same dialogue box asking to print to PDF if I want.

[IMG]http://www.perfectreign.com/stuff/2010/print2file.jpg[/IMG]

---

### Post by PerfectReign on 2010-05-16
> **dakkar9999 said:**
> Yes, but I would need a pdf printer because of windows software running under wine.
Okay, I just read your post.  

I see what you are looking for. A method for PDF printing from within WINE.  There are two methods.

The old school method would have been to install a postscript driver to WINE and print to that. You could then run some form of conversion to PDF. You'd probably have to do this using some command line tool, which is the antithesis of graceful.


A little searching got me this.

I first tried to install ghostscript/PDFCreator. I use this tool on my Wintendo machine at work. I got it to install and give me a printer. However, it errors out when printing.

[IMG]http://www.perfectreign.com/stuff/2010/pdf_creator_wine.jpg[/IMG]



The next thing I did was look at the CUPS2PDF tool.  I opened the package manager under 10.02 and installed cupspdf. 

It was very easy to add a printer under the  Start > System > Control Center > Printing menu.

I just configured the CupsPDF printer and was off and running. 

I now have that printer listed in Word 2007 under Wine.

[IMG]http://www.perfectreign.com/stuff/2010/print2pdf_cupspdf.jpg[/IMG]

You can see the output attached.

---

### Post by nomnex on 2010-06-16
> **DeMus said:**
> I just did a clean install of Ubuntu Lucid without anything extra concerning printing. When I want to print something I choose ctrl-P and see my printer and a choice which says Print to file.
I choose that, select where I want it and what the name should be and I get a nice pdf file. Don't understand you have to install something extra and still it doesn't work.

because it creates printer (to PDF). you can set it as default printer and configure it centrally. As you pointed out this is mere convenience on a standard Ubuntu desktop today. You can perfectly use the manual steps you described, if your need to print to PDF is occasional.

If I recall cups-to pdf was necessary on Ubuntu desktop pre 9.04

---

### Post by Rob__oo00T on 2011-09-05
> **PerfectReign said:**
> Okay, I just read your post.  

I see what you are looking for. A method for PDF printing from within WINE.  There are two methods.


.............

You can see the output attached.

PerfectReign
I follow your guidline, and also see the attachment you are posted. You have exactly my problem:
PDF generated with cups printer inside Ubuntu app (see your test page as example) are "searchable" (you can easly open it with pdf reader and ctrl+f looking for "RED") :)
But the other examble is not "searchable", infact all documents (create a simple one with notepad) printed inside a WINE environment are not indexed :-k

Can anyone help me in this?
I've test this with more than ubuntu buildsm however with different release 11.04 (mine) or 10.04 LTS, ......

rc

---

