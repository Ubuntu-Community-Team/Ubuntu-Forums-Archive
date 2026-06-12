---
title: "LaTeX GUI Editor Wanted"
date: 2009-10-10
forum: General Help
---

### Post by rich1939 on 2009-10-10
I'm looking for a GUI editor for LaTex---something like what is distributed in the TeX live DVD for Windows. The editor has the ability to recognize TeX and LaTex commands, automatically invoke MakeIndex, create TOCs, LOTs, and LOFs, and invokes dvips to display the formatted text on the screen.

I see that some components of LaTeX and TeX are installed automatically here in Jaunty; however, I can't seem to find a GUI editor that will perform all of the features of the Tex Live Windows distribution.

Any suggestions, help will be appreciated.

Thanks.

---

### Post by delcypher on 2009-10-10
If you want a WYSIWYG then try LyX

If you want a GUI for editing LaTeX code then try Kile (warning has KDE dependencies).

Both are available from the ubuntu repositories.

---

### Post by rich1939 on 2009-10-10
> **delcypher said:**
> If you want a WYSIWYG then try LyX

If you want a GUI for editing LaTeX code then try Kile (warning has KDE dependencies).

Both are available from the ubuntu repositories.

I was hoping to find a package like TeXnicCenter, the TeX/LaTex editor distributed with TeXLive for Windows. In addition to *understanding* TeX/LaTex commands, it can directly invoke makeindex, bibtex, etc., and produce the dvips-formatted pages onscreen.

If LyX can do these things, then I'll give it a try; however, what is the way to download the **complete** package using **sudo install**?

I don't really need a WYSIWYG editor. I'd rather just see the raw LaTeX code and then produce the formatted pages in a separate window.

I'd also like access to all of the extra .sty files that are contained in the MikTeX distribution. Does LyX provide these?

I'm converting a book project from Windows to Linux.

Thanks.

---

### Post by XCan on 2009-10-11
Perhaps texmaker? The .sty files aren't provided by the editors, you'll have to install them. Although so far I haven't ran into any .sty files I've missed from miktex' packages.

---

### Post by Stefan_K on 2009-10-15
I'm using [Kile]("http://kile.sourceforge.net/"), that's a great LaTeX IDE. I've never had any problem with the kde libs that would be installed with Kile.

Stefan


--
[TeXblog]("http://texblog.net")

---

### Post by lariosa42 on 2009-10-20
I was using Kile for a long time.  It's a pretty great program once you get used to it and get it configured in a way that you like (and in a way that makes it work).

However, I just switched to TeXMaker.  The newest version (which is not yet available in the repos, but can be downloaded at [http://www.xm1math.net/texmaker/download.html](http://www.xm1math.net/texmaker/download.html)).  The main reason for my switch was that the newest version of TeXMaker has an inline spell-checker (i.e., the little red lines under your misspelling).  TeXMaker used to not even compare with Kile, but I think with the recent improvements in the new version, it may become my permanent TeX editor!

You should also try "Winefish" (available in the repos).  It is a very simple TeX Editor, but sometimes that's all you need/want.  You can also try out the modification to Gedit, available at [here]("http://live.gnome.org/Gedit/LaTeXPlugin").

For DVI viewers, so far I have only found Okular, Kdvi, and Xdvi.  None of them are perfect, but I like kdvi the most so far.  (Xdvi is too ugly and has no continuous-page scroll, Okular is way too slow.)  Of course, you can always view pdfs (try Xpdf, evince, Okular, and more), but then you miss out on the snazzy forward/inverse search features.

---

### Post by rich1939 on 2009-10-22
> **lariosa42 said:**
> I just switched to TeXMaker.  The newest version (which is not yet available in the repos, but can be downloaded at [http://www.xm1math.net/texmaker/download.html](http://www.xm1math.net/texmaker/download.html)).  The main reason for my switch was that the newest version of TeXMaker has an inline spell-checker (i.e., the little red lines under your misspelling).  TeXMaker used to not even compare with Kile, but I think with the recent improvements in the new version, it may become my permanent TeX editor!


I took a look at the TeXMaker site and might give that a try. I have used many different LaTeX editors/GUIs over the years and want some of the same features in my Ubuntu (Jaunty) system, such as one-click PDF creation, command recognition (with coloring), one-click index creation, etc.

I hope to find an appropriate LaTeX GUI editor for my next book project, which is centered around Python development with Qt.

A full-featured environment would be best.

---

