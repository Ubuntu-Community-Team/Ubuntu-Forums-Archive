---
title: "Extracting work lists from documents"
date: 2011-10-19
forum: General Help
---

### Post by Yumi on 2011-10-19
I need to translate professional terms. To get help I want to compile a list of such words from websites and documents like pdf doc txt or odf.

I will sort the lists alphabetically and remove duplicate words. Then I delete common word manually and are hopefully left with a list of terms relating to Cable-Cars.

Question: Does such a Program exist for Linux or can anyone advice on a methode.

Thanks, Michael

---

### Post by Lars Noodén on 2011-10-19
There are several programs that you can put together in a script or something.  [pstotext](http://packages.ubuntu.com/oneiric/pstotext) will extract text, if there is any, from PS and PDF files.  [odt2txt](http://packages.ubuntu.com/oneiric/odt2txt) will extract text from ODF text files.  [html2text](http://packages.ubuntu.com/oneiric/html2text) will do it for (X)HTML.

There are dozens of different formats under the .doc filename extension.  You are on your own there.

Then you can use sed to split the lines and sort to order them. e.g.

```

pstotext afile.pdf | sed -e 's/[ \t\.,;:][ \t\.,;:]*/\n/g' | sort --unique

```

---

### Post by Yumi on 2011-10-19
Thanks. I had to try immediately but get an Error on 
> pstotext afile.pdf | sed -e 's/[ \t\.,;:][ \t\.,;:]*/\n/g' | sort --unique 

GPL Ghostscript 9.04: Unrecoverable error, exit code 1

Maybe a problem with the 11.10 version of Ubuntu or the context of the command?

Michael

---

### Post by crdlb on 2011-10-19
Does pstotext work on a different PDF file? You could try pdftotext from poppler-utils instead. To work in that command line, you'll need to use ```
pdftotext afile.pdf -
```

---

### Post by Yumi on 2011-10-20
Reliably creates text files from pdf. This part is quite successful.

But the SED part does not seem to do anything. The output file shows the text as it was written, not in a list form, one word per line.

Michael

---

### Post by Lars Noodén on 2011-10-20
The sed part works for me still.  Are you copy/pasting it or rekeying?

The sort could use some modification:

```

| sort --unique --ignore-nonprinting --ignore-case

```

---

### Post by Yumi on 2011-10-20
Thank you for your patients! The problem is most likely the lack of understanding of the process on my side!

The "pdftotext" part creates a text file of the same name as the original pdf. This works fine.

Does the sed command manipulate the text in that text file or does it send its output to another file somewhere? In this case it would be working, I would just be looking at the wrong place.

I was using copy/past as the syntax is a little complicated. Used typing today and promptly had a error.

Michael

---

### Post by crdlb on 2011-10-20
By default pdftotext does create a .txt file, but if you use```
pdftotext afile.pdf -
``` (note the '-'), it will behave like pstotext and print the output to the screen, allowing it to work in that pipeline. Alternatively, you could use ```
cat afile.txt | sed ... 
```

---

### Post by Yumi on 2011-10-21
Well that little (-) was missing! I need a new set of eyeglasses!

But two new problems.
The text appears in some sort of new format on the screen but is not saved in a file

It is not strictly in single words, but sometimes words, sometimes part of sentences and sometimes whole sentences.

But - are getting closer.

Michael

---

### Post by Lars Noodén on 2011-10-21
> **Yumi said:**
> Well that little (-) was missing! 


If you found the dash (-) then give it a try again with the pipes (|).

(Faster than getting new eyeglasses is increasing the default font in the browser.)

---

