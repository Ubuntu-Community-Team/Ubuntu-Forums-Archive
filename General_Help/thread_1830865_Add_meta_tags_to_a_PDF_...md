---
title: "Add meta tags to a PDF ..?"
date: 2011-08-22
forum: General Help
---

### Post by wannabegeek on 2011-08-22
Hi all,

I have a website on a University server that is just for job hunting and I don't want it to be public.

A google bot crawled it recently so I added the meta tags to every page to keep the bots from indexing me.

But,  my pdf's are still indexed by google.

How do I add meta tags to a pdf in ubuntu. I Made them with LaTeX which probably makes this harder...

tia,
wbg

EDIT
I found this:  [https://ubuntuincident.wordpress.com/tag/pdf/](https://ubuntuincident.wordpress.com/tag/pdf/)

pdf mod , anyone like this ?

---

### Post by AlphaLexman on 2011-08-22
The link you posted referenced the pdf toolkit see [http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/]("http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/")

---

### Post by wannabegeek on 2011-08-22
Thanks ...I'll try that one too....it looks more robust.

Having my personal info hanging out on the google laundry line kinda sucks....I've been so careful but never
had a page of my own so didn't I realize that I'd get a bot crawling around....  I kinda freaked...

UPDATE:

I added  <meta name="robots" content="noindex">   to the keyword and title tags on the pdf's I needed to hide from google,
first using pdfmod. Pdfmod is a really simple gui based program, but I didn't trust it. 

I confirmed the addition of the meta tags with pdftk.
```
pdftk filename.pdf  dump_data 
``` 

Hopefully google webtools will remove the pdfs.

---

### Post by AlphaLexman on 2011-08-22
Wouldn't it have been better or easier to set the actual permissions of the file to 64[COLOR="Red"]0[/COLOR] ??

---

### Post by wannabegeek on 2011-08-22
This web page is for plugging myself to employers, who do need to able to download my CV.pdf  .

I am trying to keep it hidden by not allowing google bots to crawl all over it.

Thanks for your input though.

I just check checked goolge webtools and they denied my request to remove the pdf from their cache. No meta tags....

Any ideas ?

UPDATE:

Adding <meta name="robots" content="noindex"> in the keyword, title and author fields of the PDF's tags didn't work. So this time I left off the
<meta    and   >,  thinking that the GUI places them there anyways....

---

