---
title: "Creating PDF files from a command line in 10.04"
date: 2010-09-15
forum: General Help
---

### Post by dbatic on 2010-09-15
Hi,

I'm trying to find a way to generate a PDF file from a text file in a command mode (X is not installed). Is there a simple way to do that?
I don't need anything fancy - no special formatting and no images to include, just simple text converted to a PDF format.

any ideas?

Thanks

Dejan

---

### Post by papibe on 2010-09-16
I don't know any direct command to convert text to PDF, but you can convert text to PostScript and then that to PDF. You need to install one of converters.
Use this:
```
$ sudo apt-get install a2ps
```
or
```
$ sudo apt-get install e2ps
```

Then you can use this commands (a2ps used).
```
$ a2ps file.txt -o file.ps
$ ps2pdf file.ps file.pdf
```

I believe e2ps is easer, but a2ps has more options to format the page
Regards.

---

### Post by HermanAB on 2010-09-16
ls /usr/bin/*pdf*

---

### Post by dbatic on 2010-09-16
To papibe:

Thanks, that worked!


To HermanAB:

Thank you for your reply. I saw those files but which one actually converts text to pdf?

Cheers,

Dejan

---

