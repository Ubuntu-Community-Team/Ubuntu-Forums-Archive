---
title: "Firefox fails opening PDF files"
date: 2010-09-14
forum: General Help
---

### Post by kapetr on 2010-09-14
I have since my first Ubuntu 8.04 until now (U10.04) again and again the same problems with Firefox.
So I think, it must be a Bug.

Sometimes if I will open a PDF file link, Firefox fails to run associated application.

See attached printscreen JPEG.

It never happens, if the link is direct - like [http://some.url/file.pdf](http://some.url/file.pdf)

It occur "sometimes" (?!) if the url is indirect - example:

**[http://infodeska.justice.cz/soubor.aspx?souborid=4110](http://infodeska.justice.cz/soubor.aspx?souborid=4110)**

The only possibility to view such file is to save it (NOT open) and then open manually.

I can not understand it. Firefox knows type of file, saves it in /tmp/, but absurdly say, that app does not exist. But it is not true and opening another pdf file (e.g. with direct URL) works with the same app (in my case with evince) without problems.

Can someone help me ?

BTW: I have a question: If I open Edit->Preferences->Applications, then there are just few MIME types (e.g. PDF not !).
So - where gets Firefox info, what to do with sooo many other MIME file types ? Maybe some general (system) MIME config. file ? And how to change firefox actions about such file types ?

Thanks to all ... and sorry please my English.

--kapetr

---

### Post by ajgreeny on 2010-09-14
Go to **Firefox -Edit -Preferences,** where you say you have looked, and if yours is like mine, there are two instances of Portable Document Format (or PDF).

If you click on the first of those, which is the **application/octetstream** and click on the dropdown icon on the right, you can then navigate to **/usr/bin/evince** so as to use that.  For the second instance of Portable Document Format, which is the real pdf file, the choice box may give you the option of **Use Document Viewer (default)**, like mine.  If you choose these as I show in the screenshot, pdf files should open straight away from links in Firefox without saving to disk first.

If Portable Document Format does not show in **Applications**, I am sure there must be a way to add it, but I will leave you to investigate that yourself.

PS:  My preferences dialog shows 75 different content types in the Applications page.  You say there are only a few;  how many is a few?

---

### Post by kapetr on 2010-09-20
Hello and thank you for replay.

I have there only 27 entries.

For luck - now are there also 2 PDF lines (I'm absolutely sure, that before there was no one! - It's changed probably with update of Firefox ?!)

But ... It doesn't work  henceforward :-(

there is .... - see attachment

but if I try to open 
**[http://infodeska.justice.cz/soubor.aspx?souborid=4110](http://infodeska.justice.cz/soubor.aspx?souborid=4110)**

I still get the same behaviour as earlier (as I wrote).

What happens, if you open that link ???

--kapetr

---

### Post by kapetr on 2010-10-09
Could someone test it and help, please ?

---

