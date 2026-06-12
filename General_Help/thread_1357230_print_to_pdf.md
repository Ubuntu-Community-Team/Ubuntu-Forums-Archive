---
title: "print to pdf?"
date: 2009-12-17
forum: General Help
---

### Post by aaronchall on 2009-12-17
Greetings and thank you in advance for any help here.  I need to print to pdf from a flash program running inside a browser.  I looked in the repositories, couldn't find anything.  It seemed like pdf printing worked by default in 9.04, but I could be dreaming, I need more sleep.  Only problem with sleep is it doesn't feel productive... lol

So I'm specifically looking for a repository solution, but if there's none available, a reputable source is important...

Thanks

Aaron

---

### Post by tacantara on 2009-12-17
Are you running FF as your browser?  If so, you can print content to PDF by selecting File > Print.  When the dialog box opens, create a file name and location where you want the file saved to.  Next, click the PDF radio button.

I tested this procedure, and it worked nicely.  See attached file, which was created using the above info.  I hope this helps :)

---

### Post by aaronchall on 2009-12-17
ok, i found cups, it's already installed on my computer, the problem is that the flash program pops up with a print dialogue box that says "Print to printer: NO PRINTER" which is in turn greyed out.  The print button is also greyed out.  It's a beta version of the flash program, but if someone knows if I can do anything here, it would be nice.  

Thanks!

Aaron

PS Firefox DOES recognize my ability to print to file...

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
I don't know if it's available for GNU/Linux, but I use cutePDF writer for the same functionality in Windows.

Here's a [how-to](http://www.arsgeek.com/2007/05/17/5-steps-to-create-a-pdf-printer-print-to-pdf-in-ubuntu/) I found with a quick Google search.

---

### Post by aaronchall on 2009-12-17
that how-to is old, but I'll give it a shot, maybe the proper program is not listed in the Ubuntu Software Center

---

### Post by aaronchall on 2009-12-17
It pretty much falls apart on step two, where I click on every one of the possible options and there's no "add new printer" option.

---

### Post by smilingfrog on 2009-12-17
```
sudo apt-get install cups-pdf
mkdir ~/PDF
sudo chmod 700 /usr/lib/cups/backend/cups-pdf

```

This installs a PDF printer that you can use to print anything like you would using an attached printer. The last line may need a bit of tweaking depending on your distro, but it worked for me to get it running in 9.10

---

### Post by aaronchall on 2009-12-17
Thank you, that allowed the printing configuration (in the system menu) to find the pdf printer, but the walkthru is outdated, one must click on the "server" menu, go to new, then printer.  It didn't take on the first try, but it did on the second without a reboot, after some patience/distraction.

---

### Post by ethanay on 2010-02-17
I am trying to print to PDF out of [Noteflight]("http://www.noteflight.com")

The flash print dialog is otherwise much too simple:  
1. Printer select
2. Page range

However, when I select the cups-pdf driver, it ignores my selection and still prints to my laser printer!  How annoying!  This seems like a bug, and I will file it on launch pad unless someone already has...

---

### Post by ethanay on 2010-02-17
bug filed:
[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/523436](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/523436)

"flash printer dialog prints only to default CUPS printer"

---

