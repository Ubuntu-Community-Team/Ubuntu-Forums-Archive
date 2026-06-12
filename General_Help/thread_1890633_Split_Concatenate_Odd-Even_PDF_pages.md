---
title: "Split Concatenate Odd-Even PDF pages"
date: 2011-12-03
forum: General Help
---

### Post by harakiri1976 on 2011-12-03
Hi Guys!

I have a problem...

I scan a lot of paper documents. Some of them are several pages, dozens. I usually "separate" them one by one, ie, I can split 2-3 pages for instance in evince by just printing the pages I want to PDF format. 

Now, suppose I am scanning 200 sheets of paper. I have two documents:
[INDENT]- Odd pages[/INDENT]
[INDENT]- Even pages[/INDENT]

I want to split both Odd and Even, like 1,2,3, ..., etc, pages. And then concatenate all together to form digital document like the paper version. I must execute to commands. First, separate/split page numbers one by one. Second, combine Odd-Even, Odd-Even...(concatenate)

Should I make a bash script to do that or is it simpler than that using pdftk and I'm not going in the right way?

---

### Post by mike555 on 2011-12-04
Pdf-shuffler might do what you want .......

---

### Post by harakiri1976 on 2011-12-05
Hi Mike!

Not really. But thanks anyway.

I am afraid I'm gonna have to use pdftk.

I must:

Extract Odd pages, split them one by one and transform them like:

1, 3, 5, ...

Do the same for Even:

2, 4, 6, ...

Then,

Concatenate/Combine 1-2-3-4-5-6-...

---

