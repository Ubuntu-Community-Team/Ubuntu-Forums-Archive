---
title: "LaTeX Forward/Inverse DVI search on TeXMaker with kdvi"
date: 2009-10-20
forum: General Help
---

### Post by lariosa42 on 2009-10-20
Hello fellow LaTeX-nerds,

First, a quick note (skip if desired, question below):
I just switched to TeXMaker after using Kile for a long time.  The newest version of TeXMaker (1.9.2, which is not yet available in the repos, but can be downloaded at [http://www.xm1math.net/texmaker/download.html]("http://www.xm1math.net/texmaker/download.html")) looks great.  The author has clearly put some hard work into the new version.  The best improvement in my mind is TeXMaker now has an inline spell-checker (i.e., the little red lines under your misspelling).  This is a much desired feature that has been missing from all other Linux TeX-editors so far.

My question:
I am trying to set up the forward/inverse search with TeXMaker and kdvi (xdvi is ugly and terrible, okular is too slow, evince has poor dvi font rendering).  This seems to be partially missing in the [TeXMaker documentation]("http://www.xm1math.net/texmaker/doc.html#SECTION37"), which recommends inserting
```
kdvi "file:%.dvi#src:@ %.tex"
```
into the dvi section of "Configure Texmaker" -> "Commands."  However, you also need to configure 

(1) The Latex build command.
and
(2) kdvi's settings.

For (1), I tried several commands, the most exotic being
```
latex --src -interaction=nonstopmode %.tex %0 "%N%T"
```
For (2), in kdvi, you have to go into "Settings" -> "Configure KDVI" -> "DVI Specials" and change "Editor" to "User-Defined Editor."  Then you have to put something in the text field.  I haven't been able to fully test the settings for (1) as I haven't figured out (2) yet.

I have done many Google searches and looked on the Forums here, with no luck yet.  Can anyone provide some insight as to how to get this to work?

---

### Post by leorolla on 2009-11-02
Hi!

Good news is that (1), (2) and (3) are totally independent.

(1) as above
(2) as above
(3) your tex editor passes the correct line number to the dvi viewer.

So if you can open the DVI with evince, okular or xdvi, click on the dvi and have some editor opened in the correct line, you are done with (1).
Include
```

\includepackage{srcltx}

```in the preamble and that will do the job.

To set up (2), again, see if evince, okular or xdvi allow you to call texmaker, and if yes, see how they call texmaker. Otherwise I guess you will have to go into the texmaker documentation...

As for (3), I don't know what command you must pass to kdvi.

---

### Post by lethalfang on 2009-11-05
> **lariosa42 said:**
> Hello fellow LaTeX-nerds,

First, a quick note (skip if desired, question below):
I just switched to TeXMaker after using Kile for a long time.  The newest version of TeXMaker (1.9.2, which is not yet available in the repos, but can be downloaded at [http://www.xm1math.net/texmaker/download.html]("http://www.xm1math.net/texmaker/download.html")) looks great.  The author has clearly put some hard work into the new version.  The best improvement in my mind is TeXMaker now has an inline spell-checker (i.e., the little red lines under your misspelling).  This is a much desired feature that has been missing from all other Linux TeX-editors so far.

My question:
I am trying to set up the forward/inverse search with TeXMaker and kdvi (xdvi is ugly and terrible, okular is too slow, evince has poor dvi font rendering).  This seems to be partially missing in the [TeXMaker documentation]("http://www.xm1math.net/texmaker/doc.html#SECTION37"), which recommends inserting
```
kdvi "file:%.dvi#src:@ %.tex"
```
into the dvi section of "Configure Texmaker" -> "Commands."  However, you also need to configure 

(1) The Latex build command.
and
(2) kdvi's settings.

For (1), I tried several commands, the most exotic being
```
latex --src -interaction=nonstopmode %.tex %0 "%N%T"
```
For (2), in kdvi, you have to go into "Settings" -> "Configure KDVI" -> "DVI Specials" and change "Editor" to "User-Defined Editor."  Then you have to put something in the text field.  I haven't been able to fully test the settings for (1) as I haven't figured out (2) yet.

I have done many Google searches and looked on the Forums here, with no luck yet.  Can anyone provide some insight as to how to get this to work?

For Kile, to enable Forward/Inverse DVI, I needed to change the latex build with the following option:

--src-specials -interaction=nonstopmode '%source'

It should be the same for TeXMaker, since both editors just execute that command?

---

### Post by lariosa42 on 2009-11-10
It looks like Forward/Inverse search has been disabled in TexMaker 1.9.2 due to stability issues.  I guess we'll just have to wait until the next release.  In the mean time, I'm back to Kile, although I'll spell-check my final copies in TeXMaker.

---

### Post by leorolla on 2009-11-10
Before 1.9.2, the current version in Karmic is not fine?

---

### Post by reia on 2009-12-15
The command to configure KDVI is

texmaker %f -line %l

Anyway, the inverse search works only in XFCE, not
in Gnome\Kde.

---

