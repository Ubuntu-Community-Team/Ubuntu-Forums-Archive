---
title: "CUPS-PDF landscape printing"
date: 2010-10-22
forum: General Help
---

### Post by Maymee on 2010-10-22
G'day!

Recently I've made the bold decision to change from Windows Vista to Ubuntu. I've overcome almost every obstacle that previously withheld me from using Linux, and now I'm left with only one issue, which is not an "end-of-the-world" problem, but surely affects my productivity.

In brief: I want to print a web page from my browser to PDF in A4 landscape. In Windows, I could do this with CutePDF, but after trying for ages and Googling, I've come to the conclusion that CUPS-PDF (the virtual PDF printer in Linux) cannot do this correctly. The result I get (in all applications, so it must be CUPS), is a landscape document with A4 content. In other words, the full width of landscape format is not being used.

As a result I've ended up installing Opera, Foxit PDF reader and CutePDF in a VirtualBox. This works, but of course not very efficient. 

My question: is there a fix for this that I'm not aware about? (I use the CUPS provided by the Ubuntu distro) or is there any other virtual PDF printer that _does_ support landscape printing.

I'd appreciate any help and suggestions.

Cheers,
Remy

---

### Post by monkster on 2010-11-03
I also recently became disappointed that the CUPS-pdf printer failed to print a couple of landscape jobs I had. I was not trying to print from a browser, but from .ps files. The .ps files displayed as landscape in Document Viewer (evince), but when I went to print them out via CUPS-pdf, they printed portrait, even though landscape had been selected before printing (and showed up in the document properties).I found this site to be very helpful:

[http://www.troubleshooters.com/linux/gs.htm](http://www.troubleshooters.com/linux/gs.htm)

In fact, using the author's example commands, I was able to solve my problem using ghostscript. 

Hopefully this bug will be fixed in a future release of CUPS-pdf printer, which has always been cool to me otherwise.

---

### Post by coldraven on 2010-11-03
I have not tried this and my printer is out of ink but would "Reader 0.2.5" add-on for Firefox help?
Depending on which bits of the web-page you are trying to print.

---

### Post by spider_0k on 2010-12-28
This problem has been driving me nuts for ages. I was trying to print a PDF landscape but it insisted in printing portrait!

So I chose to print to a PS (Post Script) file then open it in The Gimp.

Perfect result! (well near enough)

HTH someone.

Philip

---

### Post by alexwi on 2011-10-01
Well, it's September of 2011 now and the problem hasn't been solved.

I don't mean to stray, but it's past midnight, I've been working for 19 hours straight, I need to print a number of documents in landscape and, of course, this crap's not helping at all, along with a number of other annoyances. I need to vent.

I wonder if those who write software for Linux use it at all in a normal setting: there are a number of minor bugs, such as this, that after taking the time to track them down, seem to remain un-fixed for several years.

My impression of the OS so far is that it has all the robustness that others (i.e. windows) lack, it has a reasonable memory and resources footprint, and it does esoteric things amazingly well (apache, mysql, postfix, etc.), but somehow none of those characteristics are prevalent on the desktop.

Alex <stepping off the soapbox and away from the virtual punching bag>

---

### Post by alexwi on 2011-10-01
Still September 2011. I found a workaround and I'm sharing it here, although I'm using Debian, so it might be different in Ubuntu.

On the top menu bar of the screen, click on System/Administration/Printing

Select your printer and change the orientation in the Job Options section.

Print your landscape document.

Set back to portrait.

Go on with your life. Eventually the developer of eVince or CUPS will find him or herself in the same quagmire and will fix it.

Alex

---

### Post by metafaniel on 2011-10-27
October 2011...
As AlexWi said, his workaround works. However it's not enough to change to landscape in Administration>Printing, it's also necessary to change from portrait to landscape in the properties settings from the application you're printing. Otherwise you'll print in a landscape page indeed BUT your text will be printed as if sent to a portrait page and thus be truncated...

Hopefully it will be fixed someday ;)

---

### Post by zapstrap on 2012-06-05
Hmm, old thread, and nobody's winning. I'll add my voice to the din.  I print from a windows machine to a cups-pdf device on a linux machine. In my pre-cups universe, I created a samba printer to handle this, and it automagically got the orientation right, provided there was text on the screen. It would use the orientation of text as a clue to which way was up. The new cups system doesn't handle this right, and always prints portrait, changing the orientation of the content on the page, but not the orientation of the page.

As a work-around, I created a little batch file to fix the problem, which could easily be adapted to a bash script. Come to think of it, it started as a bash script on the print server, and I got tired of logging in to run it every time I needed to flip the page around, so I morphed into a dos shell script (sacrilege I know). The printout directory is shared via samba.

What it does is look in the current directory for a file with the specified name, and if it doesn't find it, it checks the user's printout directory. If that doesn't work, it barfs; but if it does find it, it will convert it back to postscript, add a line to it to force the orientation to landscape, and take it back to pdf.

```
@echo off
rem #!/bin/sh
rem # rotate the pdf file 90 degrees, since cups keeps screwing up autocad files.
rem # -ported from the linux version, which was MUCH easier, only 3 lines.
rem # -this script assumes if the pdf file isn't in the current directory, it 
rem #  must be in the \\linuxprintserver\user\pdf directory.

if "%1" == "" goto usage

if not defined gsc call setgspath
if not defined pdftops set pdftops=c:\util\xpdf\xpdf-3.02pl5-win32\pdftops.exe

set pdfdocpath=.
if not exist "%pdfdocpath%\%1.pdf" set pdfdocpath=\\linuxprintserver\%username%\pdf
if not exist "%pdfdocpath%\%1.pdf" goto nofile

rem pdftops is part of xpdf, and is a lot better than pdf2ps, which is part of ghostscript.
rem most noteably, pdftops preserves fonts instead of making them bitmaps.

%pdftops% %pdfdocpath%\%1.pdf %pdfdocpath%\%1.ps

%gsc% -sDEVICE=pdfwrite -sOutputFile#%pdfdocpath%\%1.pdf -dNOPAUSE -f c:\batch\rot90.ps %pdfdocpath%\%1.ps -c quit

rm %pdfdocpath%\%1.ps

goto end

:nofile
echo Error: File %1.pdf not found.

:usage
echo Usage: %0 ^<filename^>
echo        A .pdf extension is assumed, so don't include it.
echo        If the pdf document is not in the current directory,
echo		the application will look in the pdf printer directory.

:end
set gspath=
set pdfdocpath=
```

So...you must have pdftops installed, and know where it is.  The other file called, setgspath.bat, just creates the environment variables in a windows command shell, which I nuke at the end of the script. The last piece is the rot90.ps file:

```
<</Orientation 3>> setpagedevice
```

Finally, I have added all of the bash commands to the windows command shell, which is why there's an rm instead of a del in there.

Does anybody know how to get cups to rotate the page properly? It would eliminate the need to do all this post processing.

---

