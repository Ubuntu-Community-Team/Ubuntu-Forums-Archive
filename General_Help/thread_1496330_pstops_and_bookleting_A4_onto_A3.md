---
title: "pstops and bookleting A4 onto A3"
date: 2010-05-29
forum: General Help
---

### Post by Nick Payne on 2010-05-29
I found the fprint script at [http://ubuntuforums.org/showthread.php?t=244715]("http://ubuntuforums.org/showthread.php?t=244715") which does a nice job of producing A5 booklets on A4 paper from my Epson 1290 printer. I've been trying to modify the pstops command in the script to booklet a ps output file of A4 pages onto A3 paper, to produce an A4 size booklet, but I can't get the pstops parameters correct.

The command in the original script which rotates and shrinks two A4 pages onto a single A4 page is:

```
pstops -q -pa4 "4:1L@0.7(21.0cm,14.95cm)+0L@0.7(21.0cm,0.6cm),3L@0.7(21.0cm,14.95cm)+2L@0.7(21.0cm,0.6cm)"

```

I first attempted to get this to rotate and shrink two A3 pages onto a single A3 page by using

```
pstops -q -pa3 "4:1L@0.7(29.7cm,21cm)+0L@0.7(29.7cm,0),3L@0.7(29.7cm,21cm)+2L@0.7(29.7cm,0)"
```

but this causes output to run off the page and be too large, and trying to get A4 output bookletted onto A3 has been similarly unsuccessful.

Can anyone tell me what I am doing wrong with trying to put two A3 pages onto a single page in the code above?

---

