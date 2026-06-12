---
title: "Tex can't find nonstandard fonts."
date: 2012-01-04
forum: General Help
---

### Post by Randy Schilling on 2012-01-04
I use tex, editing out of kile.
I also tex and preview (okular) from kile.
I was very happy with my tex/kile system.

Yesterday, I created and successfully ran an amstex document.
I processed the document from my bash shell using the amstex executable; 
this because kile does not include amstex among its menu and shortcut options.
[As a distant second issue,  I wonder if kile can be extended to include the  amstex
executable among its menu options and shortcuts.]

Everything went fine until this morning when I tried to work with ordinary tex.
My source file loads many fonts which are not loaded automatically with plain tex.
You can see from the attached log file that tex is unable to find certain font files (.tfm files).
I searched (using nautilus) my directory /usr/local/texlive/2011/ for  cmcsc7 files  and, yes,  there are none.

Tex never had a problem finding the required font files, till this morning.
[I'm pretty sure that the only thing I did out of my normal rountine was to work with amstex,
didn't modify any environment variables or open any files like  ~/.profile.]

What could have possibley happened?

Thanks - Randy

---

### Post by carranty on 2012-01-04
I use tex a lot myself and have had similar issues over the years, though unfortunately not this exact one.  

What exactly is it that's not working, if you create a brand new blank tex file in kile, does it compile, or will it not even do that?  If the blank file compiles, try (by a process of elimination) to find what command(s) in your texfile are causing the problems, if you post those maybe I can be more help.  

Also, have you tried compiling in something other than kile?  I don't know why, but sometimes a tex document will compile in one program and not in another.  Try using pdflatex, simply open a terminal and type

```
pdflatex file.tex
```

and it will compile the tex file to a pdf. It also creates a log file, can you attach this also, if it fails to compile.

---

### Post by Randy Schilling on 2012-01-07
Hello Carranty and thanks for looking into my problem.
My apologies for taking so long to get back to this thread, been getting over a very bad cold.
I hope you're still following this thread.

An example of a command that is failing is this,
	\fdef\sevencsc{cmcsc7},
where \fdef is previously defined by this 
(a mechanism for defining macros within macros):
     \def\fdef#1#2{\font#1=#2\dcs#1\app\of\wps##1\tobe{\hbox{#1##1}}},
     \def\dcs#1\app#2\wps#3\tobe#4{\xpda\def\csname\dslash#1\dslash#2
                                                                                              \endcsname#3{#4}}
	\def\dslash#1{\xpda\drp\string#1}
	\def\slash#1{\xpda\csname#1\endcsname}
and \xpda = \expandafter.
I've been working with these macros for years, without trouble,  until the other day when I used amstex.  

The problem is not with kile either.  I know this because I get the same  error log by texing from both kile and the bash shell.

I'm convinced that my problem is caused by amstex, that using it can disrupt elements of a working tex system.
Probably about the biggest reason for working with amstex is to gain access to amsfonts, cmcsc7 is one such font.  
I am backtracking through what I did the other day with amstex,
specifically by \inputting files amssym.def, amssym.tex and amstex.tex, trying to figure what happened.

I wish I hadn't looked at amstex, I was just satisfying a curiosity.

Regards - Randy

---

### Post by carranty on 2012-01-07
Hey Randy,

I'm not sure how much help I'll be, I don't use Tex so much as LaTex (I'm not sure what differences there are between them), however I think the dependencies are mostly the same.  How did you go about using amstex?  Did you download install anything?  If so, what?

Am I right in thinking Kile (and Tex) is working fine unless you try to use additional fonts?

---

### Post by Randy Schilling on 2012-01-08
[I'm not sure how much help I'll be, I don't use Tex so much as LaTex (I'm not sure what differences there are between them), 
however I think the dependencies are mostly the same. How did you go about using amstex? 
Did you download install anything? If so, what?]

You probably installed the texlive package (using synaptic or apt at the command line).  
Texlive is a huge thing (can't think of a better word) that includes tex, 
latex, amstex and much much more (more than most of us will ever use).
Latex and amstex are "macro packages" with tex lying at their core.
This means that latex and amstex provide their users with tools, built from tex,
special ways of handling  the elements of writing articles and books 
such as indentation, figures, tocs, and so on.  Latex and amstex represent different
approaches to the same thing, articles, books and whatever.

Latex seems by far to be most popular among all such macro packages.
This is evidenced by the fact that there are hundreds of packages built for latex.
I'm familiar with latex  packages for using color and rotating characters, for instance.
I think the popularity of amstex might be limited to mathematicians, if that, not sure anymore.

If you are using latex I would encourage you to stick with it.  
I don't know what editor you're using but I think kile is just great.
Everything you might want from amstex (and much more) 
would be at you fingertips within your latex/kile system.
You can easily setup keyboard shortcuts to latex your document and 
to preview your document (using your previewer of choice, evince, okular,...)

My background is in math.  I wrote manuscripts with amstex in the 80s and 90s.
I got away from writing for many years and since getting back to it,  I've been using
tex.  I got curious about amstex again so I dug up its documentation.  If you have texlive, its on your system already.  On my system:
  /usr/local/texlive/2011/texmf-dist/doc/amstex/base/amsguide.pdf
As with latex, amstex requires certain opening or preamble statements.
Most of us use about the same such statements at the beginning of all our documents.

I followed the guide carefully and successfully processed a simple amstex document.
What I did not realize is that by using amstex once, I was expected to use it forever more.
In other words, using it somehow crippled tex's ability to process fonts.
I never intended to give up using tex, just wanted to recall how to use amstex.

I could not figure out how to recover from the problems amstex created for my tex system.
So I reinstalled texlive and have vowed not to screw with amstex again.
I hate this approach because the original problem is not solved.   Its just avoided and forgotten.

[Am I right in thinking Kile (and Tex) is working fine unless you try to use additional fonts?]

Now that I've reinstalled texlive, kile and tex are working fine, even when I load special fonts (using \fdef as mentioned in an earlier post to this thread).

I'm up and running, happy again.  If you have any more questions just try me at
[email]rjschilling@comcast.net[/email].

Regards - Randy

---

