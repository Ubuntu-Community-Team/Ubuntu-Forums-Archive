---
title: "Weird Results from pdftotext"
date: 2009-10-17
forum: General Help
---

### Post by bar338 on 2009-10-17
I'm having trouble getting the pdftotext extension to work.  It is being utilized by a search engine on my site, sphider.eu, to index pdfs.  It works nearly perfectly except for one small thing.  For some reason unknown to me it seems to be having trouble with words in the pdfs.  There is nothing strange about the words as they are just plain text so I can't quite understand why pdftotext is having the problem. 
Here is an example:

[IMG]http://babbage.cs.missouri.edu/%7Ebar338/pictures/questionmark.jpg[/IMG]

In the above line it should read: convection Heat transfer from fluid flow though the system and radiation... But for some reason the letters fl are replaced by the symbols above.   This also happens to other words and is not confined to just the fl combination.

Any ideas on what could be causing this problem or how to fix it?

---

### Post by unutbu on 2009-10-17
This is just a guess:

Some typesetting programs recognize letter combinations like 'fl' and replace them with a specially designed character. 'fl' for example, gets replaced with a character that connects the top of the f to the l. This so-called "ligature" might be what pdftotext is having problems with. See [http://en.wikipedia.org/wiki/Typographic_ligature](http://en.wikipedia.org/wiki/Typographic_ligature)

---

### Post by lswb on 2009-10-17
It may be an encoding problem. See the man page for pdftotext and look at the -enc and the -listenc options.

---

### Post by bar338 on 2009-10-17
I'm not the best linux guy but i'm trying to figure this out.  I'm having trouble finding the list of possible encoding to use.

I've tried this this command and it still produced the same error:
pdftotext -enc UTF-8 pdfFile outputFile

What are some other encodings I should try?

---

### Post by lswb on 2009-10-17
I don't know if the -enc option will solve your problem or not but it is worth trying. UTF-8 is the default encoding that pdftotext uses. So the command line "pdftotext -enc UTF-8" would have the same effect as not using the -enc option at all. 

To see available decodings, use the command pdftotext -list. On my system this returns:

```

$ pdftotext -listenc
Available encodings are:
UCS-2
ASCII7
Latin1
UTF-8
ZapfDingbats
Symbol

```

Try some of these where you used "UTF-8" in your example and see if it makes any difference.

---

### Post by bar338 on 2009-10-17
there we go. Switching to ASCII7 did the trick

---

### Post by mike-g2 on 2009-10-26
Hi all,

I'm glad to have found this thread. I've been annoyed by this behavior and similar behavior in "less", which I use more often.  In fact, I can't seem to figure out how to set less's options correctly.   The documentation indicates that there is an LESSCHARSET=ascii option, but that doesn't remove the lignatures.

Do any of you know if less invokes pdf2txt or pdftotext or have any suggestions for solving this problem w/in less?

Many thanks in advance.

Mike

---

