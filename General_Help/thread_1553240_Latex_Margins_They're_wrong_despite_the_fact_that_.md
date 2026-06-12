---
title: "Latex Margins: They're wrong despite the fact that I set them"
date: 2010-08-14
forum: General Help
---

### Post by BCven86 on 2010-08-14
Hi all,

I hope this isn't a RTFM question, but I have been looking around for several hours and I can't figure out where the problem lies.

I have a latex document where I want to set the margins to 0.7in on all sides. I do this by 

```
\usepackage[top=.7in,right=.7in,left=.7in,bottom=.7in]{geometry}
```and
```
\usepackage[hmargin=.7in, vmargin=.7in]{geometry}
```I have tried both. 

The problem is that the left margin still is significantly bigger on the left side than on the right. I have tried setting the paper size to letter in a variety of ways with no success.

/etc/papersize shows 'letter'

I ran sudo texconfig and set the paper size to letter.

The lopsided margin is for both viewing in evince and printing.

Also, when viewing the dvi file in evince, the margins are lopsided the other way, i.e. the right margin is bigger.

I can't think of anything else that might be causing the problem as I am not an expert on the inner workings of LaTeX. Does anyone have any ideas?

Thanks,
Bob

---

### Post by hawthornso23 on 2010-08-14
I'm not a user of this specific package but I've been using latex for around 20 years.

Latex is the best printsetting application around - especially for mathematics. However because it is a printsetting application and because it will do everything a printsetter could ever want it to do, it can be complicated to control layout. The problem is that there are many ways in printsetting that you can end up with space around text. You've got binding offsets, layout offsets and then within the layout you've got margins. You've got spaces for header and footer, and offsets between those and page body. And space can be left for marginal notes or footnotes.  So if extra space is showing up it is sometimes hard to figure out why.

Yes this is a read the manual question, but in this case I don't mind reading the manual with you since I like the look of the geometry package and wouldn't mind using it myself. It looks like a nicer way to set page geometry than changing all the settings manually, which is what I have been used to doing.

First things first. Have you tried 

```
\usepackage[letterpaper,centering,margin=0.7inch]{geometry}
```On skipping through the manual that looks like how I'd try to get it to do what you want to do.

---

### Post by fast_ian on 2010-08-14
Damn! Haven't used LaTeX in years! [I thought, probably mistakenly, I may be able to help.....]

Not being funny, but have you tried using *neither* statement? - It sounds like there's too many apps trying to make too many decisions/obey or ignore rules/etc. "Simplify" (?)

Good luck, sorry to not have the answer,
Cheers,
Ian

---

### Post by BCven86 on 2010-08-14
Hawthornso23,

That command resulted in the same output. Wide left, short right. BTW it was supposed to be 'in' rather than 'inch'. I have a feeling it has something to do with the page choice, but I'm not so sure.

Fast_ian,

Normal latex has very wide margins that are undesirable given the document. I need a way to manually set the margins.

Thanks for trying!
Bob

---

### Post by hawthornso23 on 2010-08-14
Sorry about the 'in' - always use cm myself.

What kind of documentclass are you using.

---

### Post by BCven86 on 2010-08-14
> **hawthornso23 said:**
> What kind of documentclass are you using

Here is the code:
```
 \documentclass[10pt]{article}

```Thanks again,
Bob

---

### Post by hawthornso23 on 2010-08-14
Try adding

```
\setlength{\textwidth}{7.1 in}
 \setlength{\textheight}{9.6 in}

```
to the preamble

---

### Post by BCven86 on 2010-08-14
> **hawthornso23 said:**
> Try adding

```
\setlength{\textwidth}{7.1 in}
 \setlength{\textheight}{9.6 in}

```to the preamble

The output here is the text back to the default margins. Being that the textwidth is what it is, the text now goes off the right side of the page.

I tried combining this last bit of code with a hard setting of each the left and right margins so that it might be aligned, but that just got me back to where I have been. So in all three conditions (i.e. your code alone, your code with left margin set, your code with right margin set) didn't work. This is actually one of the original setups that I had, but that setup didn't work. The original setup I had was:

```
\documentclass[10pt]{article}

\pdfpagewidth 8.5in
\pdfpageheight 11in

\setlength\topmargin{.3in}
\setlength\headheight{0in}
\setlength\headsep{0in}
\setlength\textheight{8.5in}
\setlength\textwidth{6.5in}
\setlength\oddsidemargin{0in}
\setlength\evensidemargin{0in}
\setlength\parindent{0.25in}
%\setlength{\parskip}{0.5cm plus4mm minus3mm}

\usepackage{amsmath}
\usepackage{setspace}
\usepackage{graphicx}
\usepackage{multicol}
\usepackage{lineno}
\usepackage{indentfirst}
\usepackage{hyperref}
\usepackage{makeidx}
\usepackage{ulem}
\usepackage{appendix}

```Thanks,
Bob

---

### Post by BCven86 on 2010-08-14
Perhaps it would be worth while to show you my preamble as it currently exists:

```
\documentclass[10pt]{article}
\pdfpagewidth 8.5in
\pdfpageheight 11in

\usepackage[top=.7in,left=.7in,bottom=.7in]{geometry}
%\usepackage[hmargin=.7in, vmargin=.7in]{geometry}

\setlength{\textwidth}{7.1 in}
\setlength{\textheight}{9.6 in}

\usepackage{amsmath}
\usepackage{setspace}
\usepackage{graphicx}
\usepackage{multicol}
\usepackage{lineno}
\usepackage{hyperref}
\usepackage{ulem}
\usepackage{fancybox}

\usepackage[T1]{fontenc}
\usepackage[scaled]{helvet}
\renewcommand*\familydefault{\sfdefault}

\setlength{\parskip}{0pt}
\setlength{\parsep}{0pt}
\addtolength{\parskip}{-5.5pt}

\setlength\fboxsep{15pt}

\newenvironment{Itemize}{
\begin{itemize}
        \setlength{\itemsep}{1pt}
        \setlength{\parskip}{0pt}
        \setlength{\parsep}{0pt}}{\end{itemize}
}

\pagestyle{empty}

\def\Section#1{\vspace{.02in}\begin{center}{\textbf{\underline{#1}}}\end{center}\vspace{.05in}}
\def\heading#1{\noindent \textbf{#1}}

```

---

### Post by hawthornso23 on 2010-08-14
I've been experimenting. I see your problem. However I don't see your problem when I compile with pdflatex instead of latex. Try compiling with pdflatex and take a look at the
result. Here is my test document

```

\documentclass[12pt]{article}
\usepackage[centering,margin=0.7in]{geometry}

\pagestyle{empty}

\begin{document}

blah blah blah (enough for several pages ) ...

\end{document}

```

Very odd ... it shouldn't be doing that. 

This looks OK to me in pdflatex, but offcenter in plain old latex.

What do you see?

---

### Post by BCven86 on 2010-08-14
> **hawthornso23 said:**
> I've been experimenting. I see your problem. However I don't see your problem when I compile with pdflatex instead of latex. Try compiling with pdflatex and take a look at the
result. Here is my test document

```

\documentclass[12pt]{article}
\usepackage[centering,margin=0.7in]{geometry}

\pagestyle{empty}

\begin{document}

blah blah blah (enough for several pages ) ...

\end{document}

```Very odd ... it shouldn't be doing that. 

This looks OK to me in pdflatex, but offcenter in plain old latex.

What do you see?

Alright, so with your test document I got perfect alignment with both latex and pdflatex. This means that I have some package included in my preamble that is throwing things off. I'll step through each one to find the culprit.

I tried putting your geometry call as the last line before \begin{document} since I figured that putting it there would cause it to trump any other settings. That didn't work though.

I'll let you know the result of removing various packages. Thanks for the help.

-Bob

---

### Post by BCven86 on 2010-08-14
> **BCven86 said:**
> Alright, so with your test document I got perfect alignment with both latex and pdflatex. This means that I have some package included in my preamble that is throwing things off. I'll step through each one to find the culprit.

I tried putting your geometry call as the last line before \begin{document} since I figured that putting it there would cause it to trump any other settings. That didn't work though.

I'll let you know the result of removing various packages. Thanks for the help.

-Bob

It appears that 
```
\setlength\fboxsep{15pt}

```
was the culprit. The purpose of it is to create separation between the text and the borders I have set up, but I guess that it actually pushes the text to the right. I guess then I would need to choose my margins as {.7in-15pt}, although I don't think that LaTeX can do that computation in line. I'll have to wade through the fancybox documentation to get it working. Do you have any quick suggestions on how to do this better than I currently do it?

Thanks again for your help, I appreciate you taking the time.
Bob

---

