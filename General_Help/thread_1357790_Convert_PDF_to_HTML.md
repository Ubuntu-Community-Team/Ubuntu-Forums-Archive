---
title: "Convert PDF to HTML"
date: 2009-12-17
forum: General Help
---

### Post by aktiwers on 2009-12-17
I need to convert about 35 large PDF documents to HTML. I already have stylesheets that needs to be used.
 The PDF's contains text, pictures and tables.

I was wondering if there was any nice tools or commands that could help me speed up the process?
 In the end I want them to validate with W3C, but first I just need some tips or tricks to speed up the process. 

How and what tools would you use?

Thanks

---

### Post by s.fox on 2009-12-17
Hi,

[This]("http://www.ubuntugeek.com/howto-convert-pdf-files-to-html-files.html") may be of some use to you.  Have fun :)

-Silver Fox

---

### Post by kwd on 2010-06-29
I have tried pdf2html and several other methods including converting it to text and then to html.  The BIG problem is that all of the software to convert pdf files to a "text based" format like html screw up the paragraphs, add extra text (perhaps some kind of hidden text embedded in the pdf file), and drop text--among several other things.  All of this is a lot of work to fix.

I just recently discovered that Kword allows you to import pdf files which you can then edit, restructure the layout, and then export to several other formats including html.

If you decide to export a pdf from Kword I recommend that you first open "Style Manager" and under "Indent & Spacing" add some spacing before and after the paragraphs.  This seems to help with paragraph problems in the html export but not as much in the plain text export. Be sure and click OK afterward.

In the last step of saving the html export it will ask you questions about the versions of html, CSS and external style sheets that you want it to use.  I chose HTML 4.01, Basic transitional HTML" and to use an external style sheet.  That way you can use your own HTML header and use an external or internal CSS style without having to delete theirs. I have not experimented with the other choices.

If you use your own CSS styling you will need to strip the formating arguments inside the <p> tag as well as all <font> tags like:

```

  <p align="left">
  <font face="Times New Roman" size="3" color="#000000">
  </font>

```
from the exported file.

The following regular expressions (if used in kate or any other editor that supports regex expressions) will clean out the <p> tags and remove all <font> and </font> tags.

These are for kate but "should oughta" work in other regex activated editors.

Using the "replace" feature put

 ```
<p[^>]*>
``` 

in the "search for box" and <p> in the "replace with box". This will clean out the format arguments <p> tags

Using the "replace" feature put

 ```
</?font[^>]*>
``` 

in the "search for box" and NOTHING in the "replace with box". This will remove all <font> and </font> tags

If you only have a couple of images it will do a good job of inserting them in the html file it creates.  BUT a complex page with columns and lots of pictures will have a very messy output.

I know this works with Kubuntu and Ubuntu 8.04 but rumor has it that the version of Kword in 9.10 has dropped this feature.

Check it out.

---

### Post by aktiwers on 2010-06-30
I'm already done with my project, but thanks a lot for the input kwd!
I will try this out next time I need to do something similar.

---

