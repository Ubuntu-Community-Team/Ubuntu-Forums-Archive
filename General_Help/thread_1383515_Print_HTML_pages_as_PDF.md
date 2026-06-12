---
title: "Print HTML pages as PDF"
date: 2010-01-17
forum: General Help
---

### Post by karmic-koala on 2010-01-17
Anybody know of a good free utility/app that converts webpages to PDF? There are several for Windows but I know none for Ubuntu :(

---

### Post by howefield on 2010-01-17
cups-pdf

It's in the repository, so can be installed with Synaptic Package Manager.

---

### Post by karmic-koala on 2010-01-17
Just found this you can print a web page as pdf without installing cups-pdf. In Firefox go to print, select 'to file' and output format as PDF. Don't know if the option is available in production version of Firefox. I am using Shiretoko 3.5.8

---

### Post by llamabr on 2010-01-17
Yes, firefox will print to file, either as ps or pdf.

openoffice will also export an html file to pdf.  Though in my experience, it doesn't always render html perfectly.

---

### Post by karmic-koala on 2010-01-17
Agree, open office does the job, though not quite as well. It would appear some formatting and images get lost whilst saving the document as HTML, opening it in Open Office and printing as PDF.

I am inclined to believe whilst trying to use the print option in Shiretoko the page's print style comes into effect. What I am trying to do is create a PDF from the page as it appears in the browser and not as it is rendered by the print styles. 

Anybody any ideas?

---

### Post by howefield on 2010-01-18
> **karmic-koala said:**
> Just found this you can print a web page as pdf without installing cups-pdf. In Firefox go to print, select 'to file' and output format as PDF.

Thanks for that, I've used cups-pdf for a while and missed that it wasn't required for Firefox now.

I'll probably keep it installed though for Opera.

---

### Post by karmic-koala on 2010-01-19
Strangely though the option doesn't seem to exist in Firefox for Windows (or may be it just because I am on Shiretoko).

---

### Post by Ahriman on 2010-01-19
> **karmic-koala said:**
> Agree, open office does the job, though not quite as well. It would appear some formatting and images get lost whilst saving the document as HTML, opening it in Open Office and printing as PDF.

I am inclined to believe whilst trying to use the print option in Shiretoko the page's print style comes into effect. What I am trying to do is create a PDF from the page as it appears in the browser and not as it is rendered by the print styles. 

Anybody any ideas?
The only way that comes to mind (when you consider that most methods of creating a PDF are by 'printing') is to copy the webpage as it is, then pasting into an OpenOffice document. Alternatively, you could save the page, edit the page's HTML to not include the CSS stylesheet for printing, then open yoru local copy and print it to PDF using the aforementioned procedures above.

---

### Post by SirBismuth on 2010-01-19
If you install cups-pdf, you can print to pdf from any application, and avoid any format loss when importing html into OpenOffice, for example.

At least that's been my experience.  

B

---

### Post by karmic-koala on 2010-01-19
Just tried this on Chromium and Epiphany. Both have the same print to file option with PDF as one of the output formats. 

Agree with [howefield]("http://ubuntuforums.org/member.php?u=186490"), the option seems to be missing from Opera.

---

