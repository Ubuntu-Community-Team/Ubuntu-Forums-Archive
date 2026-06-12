---
title: "ps2pdf printed page margins"
date: 2010-08-30
forum: General Help
---

### Post by BCven86 on 2010-08-30
Hey all,

I am having trouble converting a latex file to pdf with the precision I am looking for. I want strict control of the margins for both the outputted pdf and the printed page but currently it looks like there is a discrepancy between the two.  I set the margins with the geometry package, i.e. 

```

\usepackage[left=.5in,right=.5in,top=.5in,bottom=.5in]{geometry}

```and then have tried converting to pdf by both the dvipdf route and the dvips --> ps2pdf route. All of these output files look identical through evince, however when I physically print the pdf the margins are roughly double the size I want. When I print the ps version the margins are *exactly* what I want. Therefore I expect the problem is obviously in ps2pdf. 

I am printing on letter paper (8.5 x 11), which I have tried to explicitly set using

```

ps2pdf -sPAPERSIZE=letter foo.ps

```with no luck. 

My goal is to have a pdf for the sake of compatibility. I also do not want to use pdflatex for various reasons. Does anyone have any idea why this would be happening? What options have to be set that I don't know about. I tried searching around for a while but mostly found solutions involving a mistake papersize (a4 vs letter) changes, so sorry if this is RTFM. Thanks for the help in advance!

-Bob

---

### Post by BCven86 on 2010-08-31
Another note, I am printing on a network printer that is connected to an XP computer and run by samba. Perhaps this could be a source of the problem too?

---

