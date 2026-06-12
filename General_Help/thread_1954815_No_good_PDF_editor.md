---
title: "No good PDF editor"
date: 2012-04-08
forum: General Help
---

### Post by thebluesparkcol on 2012-04-08
I have been a new Ubuntu user for 2 days, absolutely love it, however, it may be of little use to me. I am painfully disappointed that there is not ONE good pdf available on ubuntu, that allows me to edit pdfs such as highlight. As a student, there is little I can do with Ubuntu without this basic function. Help, Somebody.

---

### Post by hughr2005 on 2012-04-08
I'm pretty sure you can open them in your browser?

---

### Post by mike555 on 2012-04-08
Xournal will highlight and add text and export as .pdf
 
 also there is portable Master pdf editor" free for non commercial use;
[http://code-industry.net/pdfeditor.php](http://code-industry.net/pdfeditor.php)

---

### Post by rmil on 2012-04-08
for manipulating with pdfs generally you can use pdftk tools there are also gui solutions. (rotate, cut pages, move pages, etc...)

for editing pdfs. Depends what you need. 
Easy solutions are Inkscape/Gimp

For proffesional usage with CMYK support my solution is:
pdftops to convert to ps then edit it with the newest ScribusNG. It is also possible to directly import pdfs into ScribusNG but it is not so good yet.

---

### Post by Peripheral Visionary on 2012-04-08
> **mike555 said:**
> Xournal will highlight and add text and export as .pdf
[]("http://code-industry.net/pdfeditor.php")

I use that in school to annotate pdfs too. Best of all, Xournal is in the Ubuntu repositories!

---

### Post by haqking on 2012-04-09
pdfstudio
pdfedit
inkscape
scribus
fipsed
[http://www.pdfescape.com/](http://www.pdfescape.com/)
xournal
okular
foxit ([http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/))


I could go on, but i found those in 30 seconds, i didnt have 2 days ;-)

Plus there are a few that will work under wine.

As for "good" that is based on user perspective so hard to categorise

Plus if the only reason to not use Ubuntu is that lack of functionality then Linux is probably not for you, also you could run a Virtual machine or dual boot if it is a necessity.

Peace

---

### Post by HermanAB on 2012-04-09
...and for moving pages around: pdfshuffler and pdfchain.

---

### Post by cortman on 2012-04-09
The best one I have ever used is PDF XChange viewer. It's a Windows program but runs well in Wine. Will allow you to highlight, add notes, stamp, you name it. It's a really terrific program.

---

### Post by vandamme on 2012-04-09
I always used the PDF Import plugin in LibreOffice to edit PDFs. You have to go to the OpenOffice site and search for it and download it. Pretty slick, just open a PDF like it was any text document, edit the words and pictures, then export to PDF again if that's what you need. If I just need to grab some text, PDF XChange Viewer is faster.

---

### Post by wujj123456 on 2012-04-14
People, you really need to check out Foxit Reader.  I guess some of you are fooled by Foxit Reader Linux on their webpage.  That's crap, but their Foxit Reader 5 for Windows runs 100% fine under Wine.  Not a single glitch from installation to using.  

It has all the highlighting, annotation, signature you have from Adobe Reader X.  It also features drawing, search among multiple files, etc.  Basically it subsumes Adobe Reader X, and contains some features of Acrobat X.  

(Sorry if that sounds like an ad, but I am just so excited about Foxit Reader's performance under Wine.  )

---

### Post by callmemahavir on 2012-04-14
The document can be saved as .DOC and converted to PDF.

To convert the .DOC file to .PDF there are various tool in linux.

So the Document can be edited in Libre Office (or) Open Office.

And in shell enter the following command.

[FONT=&quot]libreoffice3.4 --headless --convert-to pdf test.doc

Also you can refer the site...

[http://kgsspot.blogspot.in/2011/09/convert-doc-to-pdf-in-command-line.html](http://kgsspot.blogspot.in/2011/09/convert-doc-to-pdf-in-command-line.html)



[/FONT]

---

### Post by goldshirt9 on 2012-04-14
if you wish to edit pdf's there is a free open office add on that allows to to do as wished.
[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by Rebelli0us on 2012-04-14
> **thebluesparkcol said:**
> I have been a new Ubuntu user for 2 days, absolutely love it, however, it may be of little use to me. I am painfully disappointed that there is not ONE good pdf available on ubuntu, that allows me to edit pdfs such as highlight. As a student, there is little I can do with Ubuntu without this basic function. Help, Somebody.

2 days?! Welcome to Ubu-world

If there's a Windows app that you prefer, you can run it in a virtual machine. You can run both OSes simultaneously. OPen Ubuntu Software Ceter and search for "VirtualBox", then select install.):P

---

### Post by Phonic_P on 2012-04-15
> **vandamme said:**
> I always used the PDF Import plugin in LibreOffice to edit PDFs. You have to go to the OpenOffice site and search for it and download it. Pretty slick, just open a PDF like it was any text document, edit the words and pictures, then export to PDF again if that's what you need. If I just need to grab some text, PDF XChange Viewer is faster.

I just looked, it's not there.  Spent two hours looking on the libreoffice webpage which claims there is an extension but when one types in the "PDF Import" in the search engine it comes up with "0" results.

goldshirt9's link two posts above has the PDF import extension

---

### Post by prefpat on 2012-04-18
Recently a find PDF Studio from Qoppa ([http://www.qoppa.com](http://www.qoppa.com)). 
It's very complete. It's not free but you have a trial version to test what you want to do. 
It's possible to buy a  licence at special price for Academia & Non-Profit. 
Try it!

---

### Post by oboedad55 on 2012-04-18
> **Phonic_P said:**
> I just looked, it's not there.  Spent two hours looking on the libreoffice webpage which claims there is an extension but when one types in the "PDF Import" in the search engine it comes up with "0" results.

goldshirt9's link two posts above has the PDF import extension

LibreOffice-pdfimport is in the repos.

---

### Post by codemaniac on 2012-04-18
For some historical reasons PDF files are not meant to be edited .Still there are avalanche of tools available in ubuntu that will let you edit PDFs .Haqking has shared a good list .

---

### Post by al111 on 2012-04-18
+1 Foxit Reader

---

### Post by ubuntu27 on 2012-04-19
> **Phonic_P said:**
> I just looked, it's not there. ... when one types in the "PDF Import" in the search engine it comes up with "0" results.


```
sudo apt-get install libreoffice-pdfimport
```

---

### Post by codemaniac on 2012-04-19
> **al111 said:**
> +1 Foxit Reader

are you sure foxit is available in the repos .
```
sudo apt-cache search foxit
```
returns null !!

---

### Post by ubuntu27 on 2012-04-19
> **codemaniac said:**
> are you sure foxit is available in the repos .
```
sudo apt-cache search foxit
```
returns null !!

You have to install manually:

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

---

### Post by al111 on 2012-04-19
And install in 'WINE'

---

### Post by ubuntu27 on 2012-04-19
> **al111 said:**
> And install in 'WINE'

Why use Wine if Foxit provides native deb files?
 for Debian & Ubuntu Linux? And there is RPM for Redhat, Fedora,  and other RPM based distros

[http://www.foxitsoftware.com/pdf/desklinux/download.php](http://www.foxitsoftware.com/pdf/desklinux/download.php)

---

### Post by al111 on 2012-04-19
Foxit 5 for Windows is *full-featured*...

Foxit 1.1 is an early/lite version for Linux

---

### Post by ubuntu27 on 2012-04-20
> **al111 said:**
> Foxit 5 for Windows is *full-featured*...

Foxit 1.1 is an early/lite version for Linux

Ohhh. i see. didn't know that. (never tried runing Foxit in Linux)

---

### Post by codemaniac on 2012-04-21
I am always afraid of WINE and running windows executables in linux natively because of its malicious manipulation of my files, altering startup scripts, or doing other destructive things. ,always tried to keep my system simple , fast and smart .Theoritically there are also ample of security issues associated with windows system call s like  being called in Linux .

---

### Post by atulkakrana on 2012-04-29
> **haqking said:**
> pdfstudio
pdfedit
inkscape
scribus
fipsed
[http://www.pdfescape.com/](http://www.pdfescape.com/)
xournal
okular
foxit ([http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/))


I could go on, but i found those in 30 seconds, i didnt have 2 days ;-)

Plus there are a few that will work under wine.

Peace

Have you tried using any of those you mentioned? Only than you will understand the situation.

AK

---

### Post by haqking on 2012-04-29
> **atulkakrana said:**
> Have you tried using any of those you mentioned? Only than you will understand the situation.

AK

yes i have why ?

The OP asked for a PDF editor that will allow highlighting and one that is "good"

A few of them highlight and annotate, xournal being the most popular i suspect [http://www.webupd8.org/2011/02/highlight-text-or-annotate-pdf-files-in.html](http://www.webupd8.org/2011/02/highlight-text-or-annotate-pdf-files-in.html)

and the ones that dont support highlighting directly are still what i class as "good.

So whats your question ?

Peace

---

### Post by Jivinathejamboree on 2013-03-21
After a lot of searching, I thought I had found a PDF editing solution in inkscape. Basically, i wanted to fill in an application form that had been sent to me in PDF. Inkscape can work with all the elements, but lacks gui support for multiple pages, so not very practical for this purpose. Then I found xournal. So far, I am really impressed. It does everything that is required for form filling in, aswell as adding in blank pages, and won't bug out and crash on you. sudo apt-get install xournal. Do it!

---

### Post by JohnOShock on 2013-04-26
I edit PDFs regularly on ubuntu... 
some of the guys have already suggested lots of usable options. 
Before, at my work, I used Adobe Acrobat 10.X on Windows combined with Adobe Illustrator CS6. The only thing I miss on ubuntu is the inline OCR editor that comes with Acrobat 10. Everything else works the same or better. Illustrator was never handy with PDFs even though it got right deep into the layout, Inkscape does that quite well too. Earlier versions could only do it one page at a time. 
Point is: there is really no need to abandon ubuntu because of a PDF editor, you just need to take a different approach. It does not increase time taken or workflow.

---

### Post by GameX2 on 2013-04-26
> **cortman said:**
> The best one I have ever used is PDF XChange viewer. It's a Windows program but runs well in Wine. Will allow you to highlight, add notes, stamp, you name it. It's a really terrific program.

+1 for PDF X-Change Viewer.  It's powerful, it look great, and is not bloatware (...Adobe Reader...).  Only 20MB, reasonnable for a PDF Reader.
I personnally try to stick with native Ubuntu software, so I use Evince, but I always leave PDF X-Change Viewer installed in Wine.  Evince sometimes does not display my PDF properly.

---

### Post by HermanAB on 2013-04-26
No need to run a wine program.  Xournal does the same.

---

### Post by wittyman37 on 2013-04-29
You can now update libreoffice in Ubuntu 12.04, 12.10, and 13.04 just look here <[http://www.ubuntukiller.com/2013/04/libreoffice-402-release-how-to-install.html](http://www.ubuntukiller.com/2013/04/libreoffice-402-release-how-to-install.html)>.  Add the repo, check for update, and install the dist-upgrade.  This gives you LibreOffice 4.0 and can open PDF files in LibreOffice Draw.  I just used it to enlarge and move around about 80 photos that were on a PDF doc.

---

### Post by zerubbabel on 2013-05-26
> **mike555 said:**
> Xournal will highlight and add text and export as .pdf
 
 also there is portable Master pdf editor" free for non commercial use;
[http://code-industry.net/pdfeditor.php](http://code-industry.net/pdfeditor.php)

I do not see any way in Xournal to annotate a pdf as one can do in Acrobat Pro or pdf-Xchange, that is, highlighting text, striking out, inserting sticky notes, etc., in such a way that the annotations can be exported and sent separately from the original pdf. 

Master PDF Editor is nice, though. I may start using it instead of pdf-Xchange, which I have used under Wine for years.

---

### Post by Buntu Bunny on 2013-05-26
> **oboedad55 said:**
> LibreOffice-pdfimport is in the repos.

> **wittyman37 said:**
> You can now update libreoffice in Ubuntu 12.04, 12.10, and 13.04 just look here <[http://www.ubuntukiller.com/2013/04/libreoffice-402-release-how-to-install.html](http://www.ubuntukiller.com/2013/04/libreoffice-402-release-how-to-install.html)>.  Add the repo, check for update, and install the dist-upgrade.  This gives you LibreOffice 4.0 and can open PDF files in LibreOffice Draw.  I just used it to enlarge and move around about 80 photos that were on a PDF doc.

I didn't know about either of these things. I'm so glad I read this thread. Thank you to Oboedad55 and Wittyman37.

---

### Post by tornadof3 on 2013-05-27
Use inkscape:

```
sudo apt-get install inkscape
```

---

### Post by BrownM on 2013-06-09
Two years later....

It is now possible to install Adobe Reader (8) on a 64bit Linux computer (Debian Wheezy) (Ubuntu7) WITH the FileOpen plugin.

wiki.debian.org/Multiarch/HOWTO... shows you how to run 32bit apps on your 64bit machine

www,apphit.com/Download_Adobe_Reader-27/8_0-161.htm... has Adobe Reader 8 available for download

~and~

plugin.fileopen.com/all.aspx... has the FileOpen plugin.

All thanks to Linux and no thanks to Adobe or FileOpen of course.

---

### Post by boomi89 on 2013-07-06
<p>
    I love foxit reader. It is great for Windows. I missed it a lot when i switch to ubuntu. (linux version of foxit reader is very primitive)</p>
<p>
    After a desperate search for a good pef viewer/editor for ubuntu. I end up using windows version of foxit reader through Wine application.</p>
<p>
    To use wine follow the link&nbsp; <a href="https://help.ubuntu.com/community/Wine">https://help.ubuntu.com/community/Wine</a></p>
<p>
    happy now........</p>

---

### Post by boomi89 on 2013-07-06
I love foxit reader. It is great for Windows. I missed it a lot when i switch to ubuntu. (linux version of foxit reader is very primitive)

After a desperate search for a good pef viewer/editor for ubuntu. I end up using windows version of foxit reader through Wine application.

To use wine follow the link  [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

happy now........

---

