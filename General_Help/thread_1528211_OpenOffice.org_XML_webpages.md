---
title: "OpenOffice.org XML webpages?"
date: 2010-07-10
forum: General Help
---

### Post by quequotion on 2010-07-10
So close and yet so far...

I figured this would be easy, since openoffice files are basically xml... but I can't find any way to render an openoffice document into a webpage.

Everything necessary is there, xml pages for style, content, and metadata (extract an ooo file)... but nothing to bind them together and make a "webpage"

For some reasaon, OOo has no functionality to render  it's own XML format into a web-ready XML format.. All the options to make HTML/XHTML pages result in a single HTML file with images of all the pages of the document on it... useless gif/jpg/png images...

Am I missing something? Is there another program I could use to plug in content.xml, styles.xml, and meta.xml and get a webpage?

---

### Post by bryanl on 2010-07-10
you can save the document as html. That will imbed the CSS and do fairly well for creating static web pages. 

'soffice -web' aka ooweb runs the editing function in 'web page' mode so you don't get margins or page breaks and such truck.

---

### Post by quequotion on 2010-07-18
> **bryanl said:**
> you can save the document as html. That will imbed the CSS and do fairly well for creating static web pages. 

'soffice -web' aka ooweb runs the editing function in 'web page' mode so you don't get margins or page breaks and such truck.


I had never heard of ooweb before!

Unfortunately it's not that much help. I really want to find a way to convert the documents I have painstakingly created in Impress *and* Writer into multipage, interactive web pages.

This feature is available in Microsoft Powerpoint. When you save a presentation as a website, you get a fully interactive HTML version of your presentation. OOo only gives you an ugly menu and pictures of your slides.
By default, writer produces a similarly useless web page which is a picture of your document.. If you save a document as a web page in Microsoft Word, you get an HTML page with embedded CSS formatting.

the Web Page wizard makes an even more pointless list of the files I  want to make webpages out of...

I hope I've just missed a button or something somewhere... I mean, doesn't it seem really strange that things would work the way the do for me? Why on earth would anyone want an html file with *pictures* of their content rather than the actual content...

---

