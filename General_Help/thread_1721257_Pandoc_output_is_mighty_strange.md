---
title: "Pandoc output is mighty strange"
date: 2011-04-04
forum: General Help
---

### Post by tiggsy on 2011-04-04
I read an article on markdown, which looks like a really neat, easy of setting up straight html files, so I had a look around, and it seems the easiest way to implement this on linux is by using Pandoc as a converter. So i installed it.

But the results are pretty strange.

Here's the input file 
```
#Heading 1

This is a [sample][1] of output from **Pandoc**. *Pandoc* uses some fairly simple stuff to format text, which is converted to your formatting language of choice (default html) when you tell it.

[1]: http://www.default.com/sample.html
##How to use it

I think I got this right. I may be wrong, though[^f1] and I would really like it if the footnoting thingy works.

* well shall we try it out?
  * is it really worth it?
* always worth a go imho

1 Possibly
2 Probably
  2.1 Very probably
  2.2 Just probably
3 Not likely

[^f1] This is a footnote, if it works


```

As it happens the footnote doesn't work (it's part of an extension called multimarkdown), but that isn't the problem. The rest of the output is also pretty bad:

```
<div id="heading-1"
><h1
  >Heading 1</h1
  ><p
  >This is a <a href="http://www.default.com/sample.html"
    >sample</a
    > of output from <strong
    >Pandoc</strong
    >. <em
    >Pandoc</em
    > uses some fairly simple stuff to format text, which is converted to your formatting language of choice (default html) when you tell it.</p
  ><div id="how-to-use-it"
  ><h2
    >How to use it</h2
    ><p
    >I think I got this right. I may be wrong, though[^f1] and I would really like it if the footnoting thingy works.</p
    ><ul
    ><li
      >well shall we try it out?</li
      ><li
      >is it really worth it?</li
      ><li
      >always worth a go imho</li
      ></ul
    ><p
    >1 Possibly 2 Probably 2.1 Very probably 2.2 Just probably 3 Not likely</p
    ><p
    >[^f1] This is a footnote, if it works</p
    ></div
  ></div
>
```

And it's much too much work to fix it, so the whole thing is worse than useless.

Anyone any idea how to get this working/where there's an actual working version available? Or alternatively, can anyone recommend a different script, preferably one that supports multimarkdown.

---

