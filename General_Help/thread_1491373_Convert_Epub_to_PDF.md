---
title: "Convert Epub to PDF"
date: 2010-05-23
forum: General Help
---

### Post by Nonno Bassotto on 2010-05-23
I have a bunch of books in Epub format which I'd rather have in PDF. Is it possible to do a conversion? Of course Epub does not specify some information, like the screen size, but I guess it should be possible to provide sane defaults for these and to override them as needed.

It would be better to have a small command line utility, like pdf2ps, dvipdfm, pdf2djvu and so on, but I would be happy even with a graphical program.

---

### Post by jamesisin on 2010-05-23
You might look at Calibre.  If you watch this tutorial closely you will see it should also be able to do what you want:

[http://www.youtube.com/watch?v=SwA6eXv1Lz4](http://www.youtube.com/watch?v=SwA6eXv1Lz4)

However, ePub is an open standard while PDF is owned by Adobe.  Wouldn't it be preferred to use ePub?

---

### Post by luigi_mb on 2010-05-23
Get epub2pdf from 

[http://epub2pdf.com/](http://epub2pdf.com/)

/luigi

---

### Post by Nonno Bassotto on 2010-05-23
According to [Calibre site]("http://calibre-ebook.com/user_manual/faq.html#what-formats-does-app-support-conversion-to-from"), it seems that it can only convert the other way round.

As for the format wars, note that PDF is an ISO standard anyway. Whichever is more free, it is more convenient for me to have books in PDF, which has better support on every platform. If Evince read Epub, I may reconsider this, but I'm not sure.

---

### Post by Nonno Bassotto on 2010-05-23
@Luigi: thank you very much. It is sort of a burden to have to install Java just for this, but I guess I can remove everything later.

---

### Post by Nonno Bassotto on 2010-05-23
Sadly epub2pdf does not really work in any reliable way. :-(

---

### Post by jamesisin on 2010-05-23
Perhaps there is bad information on their site.  At 2:38 in the video I linked there is a very clear view of a drop-down list of Output formats in which you will find PDF.  If you can't find anything else, I would look into this one.

(I suspect that Evince will eventually support ePub files as their express goal is to be the de facto viewer in Gnome.)

---

### Post by maiaymistru on 2010-08-07
> **Nonno Bassotto said:**
> Sadly epub2pdf does not really work in any reliable way. :-(

Sorry for bumping the thread, but I stumbled on this because of a similar problem. I have found epub2pdf very reliable. The only thing is that there can not be any spaces in the PDF file name before conversion.

---

### Post by brightthings on 2010-10-09
You could install okular-extra-backends and open up epub files with Okular, then export as PDF.

---

### Post by DenisonChapin on 2010-10-20
> **brightthings said:**
> You could install okular-extra-backends and open up epub files with Okular, then export as PDF.

This worked well for me!  Not a command line solution but whatever!

Cheers.

---

### Post by namsilat on 2010-11-16
I stumbled onto this thread because of same issue with conversion from ePub to PDF format. In order to use Okular for ePub files, ebook-tools are needed. Doest anybody know how to install ebook-tools under KDE? Thanks.

---

### Post by clockworkpc on 2010-12-03
> **namsilat said:**
> I stumbled onto this thread because of same issue with conversion from ePub to PDF format. In order to use Okular for ePub files, ebook-tools are needed. Doest anybody know how to install ebook-tools under KDE? Thanks.

I think you might be looking for this:

libepub0 (= 0.2.1-1) [Maverick]

It should be in Synaptic by default.

---

### Post by namsilat on 2010-12-03
I apologize for sounding like an idiot, but I have no clue what those lines mean. I am running KDE on Windows XP, should I be entering those lines into KDE somewhere?

---

### Post by nirpius on 2010-12-08
> **namsilat said:**
> I apologize for sounding like an idiot, but I have no clue what those lines mean. I am running KDE on Windows XP, should I be entering those lines into KDE somewhere?

Not an idiot at all, I remember how hard it can be to find everything at first and most people around here do too dw :)

There is a guide here that explains many ways to do it

[https://help.ubuntu.com/community/InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware")

The way I found easiest back when I used Kubuntu was to use Adept ( [https://wiki.ubuntu.com/AdeptHowto]("https://wiki.ubuntu.com/AdeptHowto") )

Adept should be accessable from kickoff (start menu). Simply search for the programs **okular** and **libepub0** and then install them from inside Adept. Then you can open your .epub files with okular.

You can also open up a terminal (command prompt) and install it that way. The terminal program used in Kubuntu is called konsole and the code you need to input is:

```
sudo apt-get install okular libepub0
```

You will be prompted to input your password and BEWARE! You don't get little asterisks or anything appearing on the screen when you type it in, it just stays blank so don't go mashing the keyboard when you think it's not being entered; just type your password calmly and hit enter. :P

---

### Post by namsilat on 2010-12-08
Thanks very much for the information. It took me a while to figure out that KDE and Ubuntu are two different software packages. I managed to download Ubuntu and installed it within Windows. But for the idiot of me there's no start menu item that I can find to start the program. I checked the folder and the only executable file is an uninstall file.

---

### Post by nirpius on 2010-12-09
In that case, it's normally just a case of holding alt and f2 to bring up the run progam dialogue and then typing in the program name.

Eg alt+f2 then type in okular.

---

### Post by namsilat on 2010-12-09
Just tried Alt-F2 but nothing poped up. To clarify, I should be hitting Alt-F2 within Windows desktop, not when the machine boots up before entering Windows, correct?

---

### Post by nirpius on 2010-12-09
Oh I'm sorry. Did you mean how to run Ubuntu. I cannot answer this without speculating unless I know how you installed Ubuntu.

Did you install Ubuntu inside a virtual machine on your windows install or did you use Wubi to install Ubuntu directly onto your computer? If it is the second then I can help you but if it the first I have no experience there and I'd recommend starting a new thread as you'll get more visibility from guys who know about this stuff as they'll recognise your title.

---

### Post by namsilat on 2010-12-09
My apology I forgot to describe how Ubuntu was installed on my machine. I ran wubi.exe and selected "Install inside Windows" option. After installation, it created a folder named "ubuntu" but has no executable files to run. I could not find any entry in the start menu to initiate the program either.

---

### Post by nirpius on 2010-12-09
You should be able to select Ubuntu from a boot loader screen when you first power on your computer.

If it is not there you may have to press f1 f2 f8 f10 f11 or f12 depending on your computer to start it up. If that doesn't work, there is also the possibility it could be another function key but I've not heard it before.

If you have a boot loader menu and there is no entry for Ubuntu, this guide may help [http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/")

---

### Post by namsilat on 2010-12-09
I finally got Ubuntu installed properly after restarting with boot loader. Thank you.

Coming back to this topic on converting epub files, I was unsuccessful using Okular for epub files despite having extra backend was installed. Upon opening epub file, it just displayed 1 or 2 lines of jumbled characters on top of each page, with rest of page blank. Does Okular work with all epub files, or it's a "hit and miss" situation?

---

### Post by nirpius on 2010-12-10
Hooray.

Food to here you got it going. I have only a few epub files on here but okular's worked fine for me on all of those so it may just be a bad file. You can check it easily by also installing fbreader which is another epub reader program and see if that gives you the same issue.

---

### Post by pooja on 2012-05-04
Hi there!
I want to convert an epub file into a pdf. I downloaded epub2pdf.zip from the website, unzipped it into the home folder. Next, via the command line, I entered the folder and did the following:
```

epub2pdf.sh <path to epub> convertedfile.pdf

```
Unfortunately, it's telling me:
```

epub2pdf.sh: command not found

```
Can you help me?
I have java 6 installed and am using Ubuntu 11.10

---

### Post by mkstallings1 on 2012-05-04
I do this kind of thing with calibre all the time.  It is super easy.

---

### Post by pooja on 2012-05-05
Hi **mkstallings1**,
I have Calibre too but when I try to convert epub>>pdf, the final pdf is really ugly to look at. Some pages are cut or oddly placed i.e. the page ends exactly on a text line therefore it is impossible to understand the text.
Are there some specific settings that I am ignoring? Could you suggest some?
Thank you.

---

### Post by JKyleOKC on 2012-05-05
> **pooja said:**
> Hi there!
I want to convert an epub file into a pdf. I downloaded epub2pdf.zip from the website, unzipped it into the home folder. Next, via the command line, I entered the folder and did the following:
```

epub2pdf.sh <path to epub> convertedfile.pdf

```
Unfortunately, it's telling me:
```

epub2pdf.sh: command not found

```
Can you help me?
I have java 6 installed and am using Ubuntu 11.10Try the command this way:
```

./epub2pdf.sh <path to epub> convertedfile.pdf

```
Unlike Windows, Linux systems look only in the $PATH directories for executable files when an explicit path to the file doesn't appear on the command line. Adding the "./" in front of the script name makes the path explicitly the current working directory.

---

### Post by pooja on 2012-05-06
> **JKyleOKC said:**
> Try the command this way:
```

./epub2pdf.sh <path to epub> convertedfile.pdf

```
Unlike Windows, Linux systems look only in the $PATH directories for executable files when an explicit path to the file doesn't appear on the command line. Adding the "./" in front of the script name makes the path explicitly the current working directory.

Tried that too - doesn't work.
As to Calibre, can anyone suggest some way to get a pdf with the following features?
[LIST]
[*]A4 page size
[*]2 cm margins overall (top, bottom, left, right)
[*]12 pt font size
[*]correct page breaks (not on text lines, making it impossible to read)
[/LIST]

---

### Post by smurphy on 2012-05-06
> **Nonno Bassotto said:**
> According to [Calibre site]("http://calibre-ebook.com/user_manual/faq.html#what-formats-does-app-support-conversion-to-from"), it seems that it can only convert the other way round.

As for the format wars, note that PDF is an ISO standard anyway. Whichever is more free, it is more convenient for me to have books in PDF, which has better support on every platform. If Evince read Epub, I may reconsider this, but I'm not sure.
Actually no. Calibre can also convert from any format to PDF.
Check it out. Easy to handle. From the FAQ:

```
What formats does calibre support conversion to/from?
calibre supports the conversion of many input formats to many output formats. It can convert every input format in the following list, to every output format.

Input Formats: CBZ, CBR, CBC, CHM, DJVU, EPUB, FB2, HTML, HTMLZ, LIT, LRF, MOBI, ODT, PDF, PRC, PDB, PML, RB, RTF, SNB, TCR, TXT, TXTZ

Output Formats: AZW3, EPUB, FB2, OEB, LIT, LRF, MOBI, HTMLZ, PDB, PML, RB, PDF, RTF, SNB, TCR, TXT, TXTZ

```

Ah - a little hint. Before converting - fix the epub file with epub-fix

---

### Post by mkstallings1 on 2012-05-07
Don't know if this is what you really need, but it may help.

[http://kanyimbe.ethnolinks.com/2011/03/using-calibre-to-convert-epub-to-pdf/](http://kanyimbe.ethnolinks.com/2011/03/using-calibre-to-convert-epub-to-pdf/)

---

### Post by Varad Vyapari on 2012-05-16
use calibre

---

### Post by 73ckn797 on 2012-08-26
I was looking to convert epub to pdf and with a google search found this link: [http://www.epub-to-pdf.com/](http://www.epub-to-pdf.com/)

It is a free online converter and seems to work just perfectly.

---

