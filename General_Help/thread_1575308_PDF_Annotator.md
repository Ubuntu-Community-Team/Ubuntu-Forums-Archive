---
title: "PDF Annotator"
date: 2010-09-15
forum: General Help
---

### Post by munthe on 2010-09-15
Hi,

Have spend I while searching the net for at PDF annotator for Linux, but can't seem to find any.

Most of the forum and blog post I found on the subject suggested different programs, Common for these though, is that they don't do annotations in the pdf, but rather import the pdf as a background for writing on top and then saving your notes separately.

This have to problems:
1. You can't comment a pdf and mail it to your co worker.
2. You can't switch between programs freely...

As far as I know the pdf format has capabilities for annotations/comments.

So anybody know how to take advantage of this, for note taking?

My use for this would mostly be notes on slides during lectures etc.

Hope for some good suggestions
/munthe

---

### Post by luigi_mb on 2010-09-15
Check pdfedit in the repositories. It works as you expect.

/luigi

---

### Post by munthe on 2010-09-16
I have been looking at pdfeditor, but is too much of a editor.
What I'm really looking for is a pdf viewer, where you can write comments, put sticky notes on top and highlight text, and save everything back into the pdf file.

---

### Post by jpfle on 2010-10-26
With the last version of Evince, we can read and add annotations in PDF files. See this [video demo]("http://carlosgc.linups.org/gnome/evince-annotations.html").

We can read annotations with Evince in Ubuntu 10.10, but I think that adding annotations will be available in the next Ubuntu version.

---

### Post by munthe on 2010-10-26
> **jpfle said:**
> With the last version of Evince, we can read and add annotations in PDF files. See this [video demo]("http://carlosgc.linups.org/gnome/evince-annotations.html").

We can read annotations with Evince in Ubuntu 10.10, but I think that adding annotations will be available in the next Ubuntu version.

That looks great. Thank you.

Will text highlighting also be availble?, I don't know if it is part of the pdf spec.

---

### Post by jpfle on 2010-10-26
> **munthe said:**
> Will text highlighting also be availble?, I don't know if it is part of the pdf spec.

It's part of the PDF spec. See [Document Management – Portable Document Format – Part 1: PDF 1.7, First Edition]("http://www.adobe.ca/content/dam/Adobe/en/devnet/pdf/pdfs/PDF32000_2008.pdf"), page 390.

Highlight annotation will be added in Evince. See this [comment of an Evince developer]("https://bugzilla.gnome.org/show_bug.cgi?id=168304#c43").

---

### Post by parrimin on 2010-12-11
Woooowwww, this is just what I need! Is there any way to do the same than [http://carlosgc.linups.org/2010/Jul](http://carlosgc.linups.org/2010/Jul) ???

I mean, i would like to have that version, although i think is not the release version. Do you know guys if we could use that version, compiling the last version or... I don't know, I just need what this guy is showing us in the video, and I am not able to find how to install that on my ubuntu or upgrade or whatever

---

### Post by parrimin on 2010-12-11
Ok, I have searched a little bit, but my skills are very poor...
I found here [http://askubuntu.com/questions/1529/how-can-i-highlight-pdfs](http://askubuntu.com/questions/1529/how-can-i-highlight-pdfs) that we need to compile the lates version of git
```
git clone git://git.freedesktop.org/git/poppler/poppler
```
When I type this in terminal it says i dont have git installed. So the first is
```
sudo apt-get install git
```
Ok, then I retype the first command git clone ..., and I have some files downloaded on ~/poppler/
Ok, now I need to compile it. So I only have compiled in linux following step by step guides, so I am not able to find a make file, and looking the files I can see an autogen.sh, so I try
```
sudo sh autogen.sh
```
Then it says that it has not found automake. So
```
sudo apt-get install automake
```
And it says something like, looking for automake 1.7, automake 1.11 found, testing it.... and some error messages.

This is all I was able to achieve with my poor knowledge, can anybody give some guidance on making, installing, and being able to test the new feature of evince?

---

