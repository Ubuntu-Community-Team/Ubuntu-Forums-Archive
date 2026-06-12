---
title: "Can not open PDF"
date: 2011-07-08
forum: General Help
---

### Post by ntlam on 2011-07-08
Hi,

I have a big PDF file which can be open in Windows. However I really have trouble opening it in Ubuntu 11.04. If I open it with the document viewer (default) I get the message: 

For the best experience, open this PDF portfolio in Acrobat 9 or Adobe Reader 9, or later.

Then I go ahead installing acroread 9.4.2. Now when I open the file, it just shows a black screen. Other PDF files can be open just fine.

I wonder if this is because the file is too big? 

Any suggestion?

Lam

---

### Post by JC Cheloven on 2011-07-08
I think that message is merely advertisement? 

What actually happens if you ignore the message and open the pdf?

EDIT ... also, what happens if you run evince from terminal? copy the file to your home folder, open a terminal and run ```
evince yourbigfilenamehere.pdf
```

---

### Post by ntlam on 2011-07-08
> **JC Cheloven said:**
> I think that message is merely advertisement? 

What actually happens if you ignore the message and open the pdf?

The message is all I get when trying to open the file with the document viewer. And if I use adobe reader 9, it gets blank (black) screen.

---

### Post by JC Cheloven on 2011-07-08
OK... you answered while I edited :)

What happens if you run evince from terminal? copy the file to your home folder, open a terminal and run

```
evince yourbigfilenamehere.pdf
```

---

### Post by ntlam on 2011-07-08
> **JC Cheloven said:**
> 
EDIT ... also, what happens if you run evince from terminal? copy the file to your home folder, open a terminal and run ```
evince yourbigfilenamehere.pdf
```

The same result as using document viewer:  For the best experience, open this PDF portfolio in Acrobat 9 or Adobe Reader 9, or later.

---

### Post by JC Cheloven on 2011-07-08
> **ntlam said:**
> The same result as using document viewer:  For the best experience, open this PDF portfolio in Acrobat 9 or Adobe Reader 9, or later.
I mean, what is the output in the terminal. Is it also that same parafraph? (if so, little help from here :( )

---

### Post by ntlam on 2011-07-08
If I use pdf2ps to convert it. I can open the PS file fine. However it's annoying that I would have to do that many times.

---

### Post by ntlam on 2011-07-08
> **JC Cheloven said:**
> I mean, what is the output in the terminal. Is it also that same parafraph? (if so, little help from here :( )

There is no message in the terminal when doing that. It just opens the document viewer and the message is on the viewer. I close the viewer to see there is any message left in terminal. But no message.

---

### Post by JC Cheloven on 2011-07-08
Well, some additional ideas:

- Is there any strange character in the title? If so, try renaming the file to something simple, without spaces, and try again.

- There are several other pdf viewers you can try: mupdf, xpdf, okular, epdfview... It's cheap to test, they're in the repos ;)

- For investigation purposes, if your file is really big (btw, how big are we talking about?), you can try to chunk it in pieces of, say, 100 pages, using the command-line tool called "pdftk" (also in the repos), and then checking whether the smaller pieces are displayed correctly or not.

Hope something of the above helps

---

### Post by hawthornso23 on 2011-07-08
This is a portfolio - Adobe's proprietary extension to the pdf format designed to get you to use Adobe stuff. It has undocumented extensions to the pdf standard in it. It consists of a bunch of pdf's embedded in an interactive menu structure. If you get it to open, it'll probably turn out to be some sort of slideshow. They have been described as being like a flash application vomited into a pdf file. In any case it isn't standard pdf.

My google-fu tells me that okular does the best job of any open source pdf reader with these things. Apparently it open them and see all the parts but it can't play them as a slideshow.

---

### Post by ntlam on 2011-07-08
> **JC Cheloven said:**
> Well, some additional ideas:

- Is there any strange character in the title? If so, try renaming the file to something simple, without spaces, and try again.

No, the file name is simple.

> 

- There are several other pdf viewers you can try: mupdf, xpdf, okular, epdfview... It's cheap to test, they're in the repos ;)

I think I tried all of these without luck.

> 
- For investigation purposes, if your file is really big (btw, how big are we talking about?), you can try to chunk it in pieces of, say, 100 pages, using the command-line tool called "pdftk" (also in the repos), and then checking whether the smaller pieces are displayed correctly or not.

Hope something of the above helps

I has 15 pages (images) and the size is 6 Mb. I tried to split it with pdftk but it just split into one file :(. Maybe the file is not too long, but it's just too big?

---

### Post by JC Cheloven on 2011-07-11
Perhaps hawthornso23 is right, and there's nothing to do if we are dealing with something different from a pdf, which is propietary format.

Nevertheless, what the pdftk program does with the burst option?:
```
pdftk yourfilename.pdf burst verbose
```
And what the doc_data.txt file contains? 
(the command should split your document into single pages, named pg_0001.pdf, pg_0002.pdf, etc, and generate that doc_data.txt file)

---

