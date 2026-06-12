---
title: "Help converting ODT to PDF"
date: 2010-01-24
forum: General Help
---

### Post by smdawson on 2010-01-24
I need to convert an ODT file to a PDF file in OpenOffice. I cannot use the "export as PDF" option because this is to submit homework, and the teacher will not except it that way. He says it looks crappy. So where can I get a good add-on that does this?

---

### Post by hawthornso23 on 2010-01-24
If I were you I'd ... ask your teacher.

Your teacher is the one who thinks `export as pdf' looks crappy. Yet that is precisely the tool designed to do this job. While there are other ways to do it I think you really need to understand the nature of your teachers objections better because most of `em are probably going to look exactly the same if not worse.

However maybe your teacher knows something I don't. So ask! As a teacher myself I can tell you that any good teacher should be more than happy to answer such a question.

---

### Post by mikewhatever on 2010-01-24
> **smdawson said:**
> I need to convert an ODT file to a PDF file in OpenOffice. I cannot use the "export as PDF" option because this is to submit homework, and the teacher will not except it that way. He says it looks crappy. So where can I get a good add-on that does this?

What looks crappy, the pdf or the original odt? I doubt there is a converter to pdf that prettifies too.

---

### Post by smdawson on 2010-01-24
He said the PDF looks crappy, because we will be using Matlab and the equations get all jumbled. Something like that. He mention doPDF will convert things to PDF, but when I checked it out it looks like it is only for Microsoft Word. So I need something for OpenOffice. I guess I can let him know doPDF is Word/Excel/PowerPoint only

---

### Post by hawthornso23 on 2010-01-24
It sounds to me like he is thinking of a problem specific to windows and word.  I am a mathematician and math typesetting is always tricky. I know where he is coming from with regard to the problems with people who insist on trying to typeset mathematics using word.

Word has always had a problem dealing with maths. For a long time the default formatting was appalling - so ugly and badly spaced you could hardly bear to look at it. It was so bad in part because MS wanted people to shell out $$$$ for a mathtype addon. But even that was pretty awful. It was just expensive and awful. Consequently mathematicians don't use word at all and have a very poor opinion of its ability to typeset mathematics, although I understand in recent years it has improved. 

Your maths professor almost certainly uses LaTeX himself for all his typesetting. If you typeset all your assignments in LaTeX he is probably going to kiss you (so be careful). MATLAB will export equations in latex format, so pasting equations into LaTeX is easy and they will typeset perfectly - beautifully even.

Exporting equations from MATLAB into word is not so easy. The problem is that Microsoft has consistently refused to support standards properly. Rather than supporting MATHML as ODF and MATLAB both do, it invented its own math markup language in OOXML. Its support for pdf was also very grudging and minimal - it tried to make everyone use XDF instead. And there is no support for LaTeX at all as I understand it.

Anyway I think what your teacher is saying is that if you export an equation from matlab into a word document and then try to save it as pdf it is probably going to look really crappy. I agree with your teacher there. However you shouldn't have the same problem using open office because both MATLAB and open office support standards properly.

You should be able to export equations from MATLAB in either LaTeX format or MATHML, and import them into odf. And they should look just great. I'd still recommend you have a look at LaTeX though. Just remember to stay out of kissing range when you hand in your assignments.

---

### Post by smdawson on 2010-01-25
Wow. Thanks for all that info. So, I found LyX, which apparently mimics LaTeX almost completely, and can import LaTeX files. If I understand what you were saying I can use this to import ODT files from OppenOffice and then export in one of the three PDF files. dvipdfm, pdflatex, and ps2pdf. I haven't tried it yet, but this seems like it should work well. I'll jump on testing it out a.s.a.ap

---

### Post by computerguts on 2010-01-25
there are many free software programs were it installs as a printer and you can print it to a pdf file. It also looks great, just google it

---

### Post by hawthornso23 on 2010-01-26
> **smdawson said:**
> Wow. Thanks for all that info. So, I found LyX, which apparently mimics LaTeX almost completely, and can import LaTeX files. If I understand what you were saying I can use this to import ODT files from OppenOffice and then export in one of the three PDF files. dvipdfm, pdflatex, and ps2pdf. I haven't tried it yet, but this seems like it should work well. I'll jump on testing it out a.s.a.ap

I think you are making this more complicated than it needs to be, and maybe my over long and detailed answer contributed to that. Sorry about that. I think the main thing is regardless what software you use, just use your common sense and make sure the result looks good before you hand it in. Ultimately the method really doesn't matter. It is what the result looks like that counts. 

Your math professor really doesn't care what software you use to produce your assignments. He/she just wants to be able to look at your equations and see properly formatted nice looking mathematics, and not some weird garbled cruft, which is what you used to get if you copied an equation from matlab and tried to paste it into word.

The pdf export function from openoffice is probably fine. Openoffice and Matlab should work together nicely as they both support the same standards. In any case openoffice does maths much better than word. It isn't the way I do it (I use latex) but it SHOULD all just work. 

Before you put yourself to all the time and effort of trying to learn some other complicated ways to do it, try that first and have a look at the result. If the equations look nice, then that is all your professor cares about. Honest.

It is not some great mystery. It is a simple question - do the equations look nice (and are they correctly formatted) in the resulting pdf? If the answer is yes, stop mucking about. You are done.

---

### Post by odttopdf on 2010-07-17
If you need help converting ODT to PDF files please visit:

[http://www.odttopdf.com](http://www.odttopdf.com)

All the information you need to know is there and it's always FREE.
If you have any specific comments please send me a Private Message through the forum, it's always nice to hear comments and do as much as possible to help other users to learn what can be done for free without spending money on it! (And unfortunately many people do pay for softwares to do their jobs that can be done much easier and for free!)

Goodluck! ;)

---

### Post by lyall on 2010-07-17
if you got scanner or access to a scanner then just print your document out in Open Office and scan it to a pdf file

good luck and have fun learning

---

### Post by hawthornso23 on 2010-07-18
The original post was made in January. It is now July. He's probably handed in his assignment by now. At least I hope so ;-)

---

### Post by odttopdf on 2010-07-18
> **hawthornso23 said:**
> The original post was made in January. It is now July. He's probably handed in his assignment by now. At least I hope so ;-)

Indeed, perhaps that one who created the post has already done it properly, but it's good to have information available for other users who want to know how to convert these files to each other (most of them can come accross this post by doing a Google search).

Just my 2 cents ;)

---

