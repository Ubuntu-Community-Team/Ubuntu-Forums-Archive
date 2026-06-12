---
title: "Printing with Cups-PDF"
date: 2009-08-05
forum: General Help
---

### Post by interestinfellow on 2009-08-05
Hey, I have a problem.

I run autocad 2k under wine, and need the ability to print to file (PDF).  However, 9.04 doesn't support this OOB, and you have to install it.  So I  found out it's
> sudo apt-get cups-pdf and it installs fine, and shows up in my printers(PDF).  However, if I watch the printer properties for "PDF" while printing (and not watching), it fails every time.  From gedit, firefox, or acad, it shows "processing", "printing", and "failed".  

How do I print to PDF from the print command in a program  that doesn't have "export as PDF" as a file command?

TIA!

---

### Post by XCan on 2009-08-05
Umm, I'm running Jaunty over here, and I am quite certain that in even older versions the "Print to file" printer in my apps have worked good and is installed by default. Actually I just tried printing this page in Firefox and it worked as supposed.

---

### Post by interestinfellow on 2009-08-05
Ahh. but install acad 2k under wine..... no export function.

I did, however, succesfully install Varicad Viewer, and after some effor, figured out the correct voodoo to get the dwg to pdf.

And if I'm not mistaken, there is a PDF printer installed by default in 8.04.

---

### Post by SeanBlader on 2009-08-17
The solution to this one that I found was to create a PDF folder under your home folder, so open up a Terminal window and do this:

```
mkdir PDF
```

Or you could do it though Nautilus.

And you should be good to print. Unfortunately the cups-pdf driver doesn't appear to allow you to select where it's getting saved, and during install doesn't create the folder for you.

---

### Post by tukus on 2009-11-06
> **SeanBlader said:**
> The solution to this one that I found was to create a PDF folder under your home folder

Sometimes the best solutions are also simple.  This worked for me - thanks!

---

### Post by WaNaBePi on 2009-11-21
I have this e book via "webassign.com" for my chemistry class and I want to "pdf print" some key pages to study off line.(If I save the page I have to scroll around this super small screen {imagine pandora.com} but you have to read the interface area for a class, super annoying to see 1/3 of a page at a time when you need to see diagrams and example problems!)

After several attempts at toying with the print dialog window that comes up (which is different for this page only, thus far anyway)  the pages of the book won't print. The viewing format while online is flash based (the book), I'm using Firefox 3.0.15. If I don't use the flash button provided(by the web page for printing pages of the book) and print the page through Firefox; I get a pretty much a blank page with the url and some other useless stuff no book page.

cups pdf printer works great for all my other needs, but the flash seems to be tripping it up, or there is some security thing that they(webassign.com) didn't mention cause they figure people only use paper printers. Which is likely as education is becoming more and more of a racketeering scheme by the second. God forbid they should have to charge $300 for a new edition with that comma added on page 417 cause a few e-pages are leaked.

Yes bitter a bit, frustrated.....Sorry

I hope I included enough info thanks in advance

---

### Post by WaNaBePi on 2009-11-24
Please someone? help?

---

### Post by XubuRoxMySox on 2009-11-24
Wow... I think no one has replied for so long because so few people attempt what you're trying.

I'm not sure if this helps, but there's a nice graphical way to edit your CUPS file that may allow you to do what you want...

Open a browser and go to [http://localhost:631/](http://localhost:631/)

Click on the **Administration** tab, enter computer username and password (if prompted), and it should immediately recognize your printer. If not, add it from a list that opens when you click on "Add Printer." There are options for sharing the printer on a network, etc. 

Explore there a bit and see if there's an option for printing to pdf including flash content.

And let us know if it helped or not.

-Robin

---

### Post by brm on 2009-11-24
I am using the 64-bit version of Kubuntu 9.10 (karmic).

The cups-pdf package does not work, and has never worked, in my environment. cups-pdf is the package which nominally installs a PDF printer from the [http://localhost:631](http://localhost:631) interface.

It used to be possible to install a "Print to a PDF" function from the KDE control center (in lower case; the current incarnation is called System Settings). I am no longer able to find that function. If it is there but I have missed it, I would be grateful that someone point out to me where to find it.

I need to attach several recent e-mail messages to a new e-mail currently in draft. Because I use a webmail client, the easiest way to do so is to print them as PDFs.  At the moment, I am completely unable to print to PDF from this configuration. I will have to start another machine with an older version of Kubuntu in order to do so.

I have submitted the cups-pdf problem to Launchpad. It is Bug 487629. I have also submitted it to the CUPS bug tracker as STR 3427 (STR == Software Trouble Report, i.e. bug). The link is:
[http://www.cups.org/str.php?L3427+P0+S-2+C0+I0+E0+M20+Q](http://www.cups.org/str.php?L3427+P0+S-2+C0+I0+E0+M20+Q)

---

### Post by WaNaBePi on 2009-11-28
dixiedancer,
thank you the reply was quite informative i didn't even know that existed however after playing with the "Basic Server Settings:" check boxes i still do not seem to have the ability to print from a flash button on a page.

I noticed that there is a "Edit Configuration File" button could there be some thing in there that i could change to make thins work?


[http://naturesfractal.blogspot.com/](http://naturesfractal.blogspot.com/) ..............for a screen shot

that "printer" window comes up after the window below it and that window comes from that picture of the printer in the upper right of the flash area

I click print and nothing happens(regardless of what numbers I put in the text boxes of the "print window") the two printing related windows diapper and no file in the "PDF" floder

---

### Post by WaNaBePi on 2009-12-02
Can anyone else offer any suggestions?

---

### Post by aaronchall on 2009-12-17
I think this is also what I am looking for, a pseudo printer that prints to pdf, that would fool another program into thinking it IS a printer.

---

### Post by ender4 on 2010-01-09
> **WaNaBePi said:**
> I have this e book via "webassign.com" for my chemistry class and I want to "pdf print" some key pages to study off line.(If I save the page I have to scroll around this super small screen {imagine pandora.com} but you have to read the interface area for a class, super annoying to see 1/3 of a page at a time when you need to see diagrams and example problems!)

After several attempts at toying with the print dialog window that comes up (which is different for this page only, thus far anyway)  the pages of the book won't print. The viewing format while online is flash based (the book), I'm using Firefox 3.0.15. If I don't use the flash button provided(by the web page for printing pages of the book) and print the page through Firefox; I get a pretty much a blank page with the url and some other useless stuff no book page.

cups pdf printer works great for all my other needs, but the flash seems to be tripping it up, or there is some security thing that they(webassign.com) didn't mention cause they figure people only use paper printers. Which is likely as education is becoming more and more of a racketeering scheme by the second. God forbid they should have to charge $300 for a new edition with that comma added on page 417 cause a few e-pages are leaked.

Yes bitter a bit, frustrated.....Sorry

I hope I included enough info thanks in advance


I have a very similar problem, and looking at your screenshot I have the exact same print dialog, some help would be greatly appreciated.

---

### Post by brm on 2010-01-09
> **brm said:**
> I am using the 64-bit version of Kubuntu 9.10 (karmic).

The cups-pdf package does not work, and has never worked, in my environment. cups-pdf is the package which nominally installs a PDF printer from the [http://localhost:631](http://localhost:631) interface.

It used to be possible to install a "Print to a PDF" function from the KDE control center (in lower case; the current incarnation is called System Settings). I am no longer able to find that function. If it is there but I have missed it, I would be grateful that someone point out to me where to find it.

I need to attach several recent e-mail messages to a new e-mail currently in draft. Because I use a webmail client, the easiest way to do so is to print them as PDFs.  At the moment, I am completely unable to print to PDF from this configuration. I will have to start another machine with an older version of Kubuntu in order to do so.

I have submitted the cups-pdf problem to Launchpad. It is Bug 487629. I have also submitted it to the CUPS bug tracker as STR 3427 (STR == Software Trouble Report, i.e. bug). The link is:
[http://www.cups.org/str.php?L3427+P0+S-2+C0+I0+E0+M20+Q](http://www.cups.org/str.php?L3427+P0+S-2+C0+I0+E0+M20+Q)

I worked out the solution to this particular problem. It was one of those "well, this makes sense, but it isn't documented anywhere." After installing the cups-pdf printer, one goes into the CUPS interface ([http://localhost:631](http://localhost:631)) and clicks on adding a new printer. A new choice has appeared: a virtual PDF printer. One configures in normal CUPS fashion. I thought I should use the same name and driver as my physical printer. WRONG! One has to use a Generic Postscript Printer.

---

### Post by ender4 on 2010-02-10
The web-book that I have trouble with is a Flashpaper SWF.

---

### Post by brm on 2010-02-10
> **ender4 said:**
> The web-book that I have trouble with is a Flashpaper SWF.

For what it is worth, I have never managed to get a Flashpaper SWF to print to any printer driver that I have tried. I am currently in dispute with a vendor who insists that this is an acceptable method to provide documentation.

---

