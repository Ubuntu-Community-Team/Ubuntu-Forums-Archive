---
title: "Very weird thing about PDF (pdf not really portable?)"
date: 2009-10-31
forum: General Help
---

### Post by kajman on 2009-10-31
Hi all!

I have an interesting problem. I've been doing some work recently with LaTeX for my studies, and I came to this conclusion:

Pdf format is not really a portable format! (or correct me if I am wrong)

I made (using Kile under KDE) a simple LaTeX file, and it is different if seen under Windows than it is under my Linux. Why is that, and how it is even possible!?

The problem is (in this example) with indentation (the thing that tab does under Word or some other text processors). I attach two pictures of the same pdf file seen under Windows (no indentation) and under my Linux, the difference is clearly seen. I aslo give the *.tex file of this compilation (in *.txt format, also sorry for polish characters which may be not viewed properly, I don't time to change the file).

Also some time ago, when I tried to print a pdf file compiled on my machine under a Windows XP system, the the print was really messy. Many of mathematical equations were completely wrong and unreadable, but when printed from my Linux everything was good. Also the pdf viewed under WinXP showed no mistakes at all. What is happening? What's wrong!?

This situation is veeeery weird to me as pdf, by definition, should be a Portable Document Format, which apparently is not true.
Any thoughts?

kajman

PS. Attached the pdf file also, for you to see what version you have. Also, my friend says that if viewed under google docs (from gmail) this he sees this pdf the same as from Windows. I cannot see it that way, and I don't know why (google docs just doesn't show the file).

---

### Post by kajman on 2009-10-31
Another wierd thing.

I've sent the pdf file as well as tex file to another friend of mine. First he viewed pdf file with foxit reader (no indentations), and then he recompiled the tex file without making any changes. What's weird is that, after compilation the file looks exactly as mine. I just don't understand it! What's happening?

---

### Post by lilbill on 2009-10-31
On Windows in the .pdf you attached I see indentation.  There should be indentation from the way you have typed your .tex file.  To number things in LaTeX try:
```

\begin{enumerate}
\item This will be number one
\item Add the item command for every new number in the list you   want
\end{enumerate}
``` 

Are the two pics attached of the same .pdf file or did you compile the same .tex file in windows and linux?

What editors are you using to type the text files?

---

### Post by kajman on 2009-10-31
Well, I know that structure, but that's not my point (thanks for advice though). I didn't use that because of my laziness ;) 

My concern is the portability issue. Why is this so weird?

---

### Post by djbon2112 on 2009-10-31
> **kajman said:**
> Well, I know that structure, but that's not my point (thanks for advice though). I didn't use that because of my laziness ;) 

My concern is the portability issue. Why is this so weird?

Well, I always though that PDFs weren't *completely* portable, in that they used the system's fonts when being viewed (I find this to be the case when I 'Download as PDF' from online Word Processors and the like). I could be wrong there, but that might explain your situation.

---

### Post by lilbill on 2009-10-31
Sorry, I didn't mean to insult you if I did!:D You didn't answer these:
> **lilbill said:**
> Are the two pics attached of the same .pdf file or did you compile the same .tex file in windows and linux?

What editors are you using to type the text files?

---

### Post by kajman on 2009-10-31
Sorry, missed that question somehow.

The pics attached are from the same pdf file (I've just sent it to my friend by email, and he made the *.gif attachment, and I made the other screenshot, but the pdf file is the same)

As for *.tex file I made it with Kile (which uses Kate, I suppose, to edit text), and just changed the extension to txt, because this forum didn't allow a tex extension.

---

