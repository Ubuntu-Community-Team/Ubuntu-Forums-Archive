---
title: "Simple lyx question"
date: 2010-10-06
forum: General Help
---

### Post by oldmankit on 2010-10-06
I'm posting here because I don't really want to be signed-up to the lyx mailing lists in order to ask one simple question.

From a lyx FAQ it says to make all quotes/quotations small, add the following to preamble:
```
\let\oldquote\quote
 \renewcommand\quote{\small\oldquote}
 \let\oldquotation\quotation
 \renewcommand\quotation{\small\oldquotation}
```I don't want my quotes small, I want them in italics.  I tried changing \small to \emph, but it gave me an error.  What do I have to do?

---

### Post by oldmankit on 2010-10-08
I found a forum especially for lyx at [http://www.latex-community.org/forum](http://www.latex-community.org/forum) which gave me the answer.

I used  **\itshape** instead of **\emph** command for italic quotes/quotations.

There was more detail too: [http://www.latex-community.org/forum/viewtopic.php?f=19&t=10391&p=40228#p40228](http://www.latex-community.org/forum/viewtopic.php?f=19&t=10391&p=40228#p40228).

---

