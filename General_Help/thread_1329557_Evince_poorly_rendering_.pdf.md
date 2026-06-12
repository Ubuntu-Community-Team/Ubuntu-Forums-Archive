---
title: "Evince poorly rendering .pdf"
date: 2009-11-17
forum: General Help
---

### Post by goldencako on 2009-11-17
Hello peoples,

I was wondering if anyone has been having Evince render their documents poorly. As they say, an image is worth a thousand words, so here goes the same document opened with Evince, Okular and Acroread.

[LIST]
[*][[COLOR="RoyalBlue"]Evince[/COLOR]]("http://imgur.com/H5wpP.png")
[*][[COLOR="RoyalBlue"]Okular[/COLOR]]("http://imgur.com/FLyYu.png")
[*][[COLOR="RoyalBlue"]Acroread[/COLOR]]("http://imgur.com/fkwRS.png")
[/LIST]

The Evince image is clearly inferior, more so at lower zoom values (it's at 175% in the image). I used to think this was a problem with the document but after trying out other viewers, that possibility is ruled out.

I'm running 9.10, Gnome, Evince 2.28.1 with poppler 0.12.0 (cairo). Any input is appreciated.

---

### Post by ohzopants on 2009-11-17
That looks like a pdf that is actually an image, as in just a simple page scan.  Can you select the text?

If that's the case I suspect it comes down to which image smoothing algorithm (if any) the different viewers use.  This may in turn be an issue with running a gnome app in kde (yes, the dependancies should work themselves out but mistakes happen).

Hope this helps and enjoy that calculus!  (Is it sad that I actually miss having to do calculus?)

---

### Post by goldencako on 2009-11-17
Yes, you are correct, the .pdf is an image. The first page that has all the publishing details of the article renders perfectly, since it is text. The following pages render like the image I posted. I'm actually on the Gnome desktop, Okular is the outsider here. So I'm a bit stumped. I've actually had this problem for quite a while, in other versions of Ubuntu, I just figured it was a problem with the articles, since the text .pdf renders flawlessly.

And no, calculus is awesome. But this is actually for a little exposition I have to prepare about, well, differentiation under the integral sign, for my analysis class. So yea, it's calc :)

Thanks for the help.

---

### Post by EtherBunny on 2010-01-30
I have the same problem, and it's existed for at least 4 releases of Ubuntu that I can remember.

Evince's rendering sucks, plain and simple.

It has sucked for years, and apparently nobody has cared enough to fix it.

Sorry to be so blunt, but you can't argue with those images.

Here's another: [http://img130.imageshack.us/img130/8351/evincevsacroread.png](http://img130.imageshack.us/img130/8351/evincevsacroread.png)

Top = Acroread
Bottom = Evince

both zoomed at 100%

---

### Post by Alexandre Putt on 2010-01-30
I have the same problem, and it is in fact common across different viewers (on occasion I do not have good rendering even in Acrobat and have to use other software). IMHO pdf is not always well suited for on screen viewing. I prefer using Evince for viewing .dvi, and for external documents post script (.ps) if possible, though not all post script files look good on the screen either.

EDIT: the quality of rendering depends on the fonts in the document. It is possible to achieve good quality for any viewer if the document uses embedded type 1 fonts, but this is not always the case. Also some fonts look bad on the screen no matter what (that is, in any viewer).

---

### Post by jordilin on 2010-01-30
I've never had any problems with evince in terms of font rendering. Evince is by far faster than acroread as well.

---

### Post by dcstar on 2010-01-30
> **jordilin said:**
> I've never had any problems with evince in terms of font rendering. Evince is by far faster than acroread as well.

Mine seems to work fine, I suspect it is an issue of what rendering subsystem the particular app is using and if it is set up correctly on a system.

[http://bugs.freedesktop.org/show_bug.cgi?id=5589](http://bugs.freedesktop.org/show_bug.cgi?id=5589)

---

### Post by EtherBunny on 2010-02-21
That would make sense, except that Evince is packaged with Ubuntu, so if there's a problem with how it's set up, then it's Ubuntu's fault, and someone should fix it.

Until then, I'm running acroread.

---

### Post by hnrkg on 2010-02-23
I have compared an article from JSTOR viewed in Google Docs and Evince, respectively. The difference seems be that Evince is not using fonts to display the document, except when text is selected, while Google Docs (and other viewers, I suppose) does. 

It would, however, be nice to be able to choose how you want to view your documents: In original image view or in "font mode".

If this is not the case, then I do not understand why selected text in Evince has such better quality than unselected text?

EDIT: Ignore the "font-jibberish", but the question still stands.

---

### Post by cokicd on 2010-02-23
Try FoxitReader, I think it's the best  option.

---

