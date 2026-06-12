---
title: "LaTeX finnish hyphenation"
date: 2006-04-07
forum: General Help
---

### Post by Tom^ on 2006-04-07
Hi

How to get finnish hyphenation to work in LaTeX?

I've tried "\usepackage[finnish]{babel}" and that without the finnish -option but everytime I get following error: "Package babel warning: no hyphenation patterns were loaded for"

These two files exist: /usr/share/texmf-tetex/tex/generic/babel/finnish.ldf /usr/share/texmf-tetex/tex/generic/babel/finnish.sty and I haven't changed my config.  texconfig -> hyphenation does not solve this because I can't finnish mentioned anywhere.

---

### Post by JoeMetal on 2006-04-07
If you put those files in there after you installed it, you'll need to type "texhash" to let tex know it's there.

---

### Post by Tom^ on 2006-04-07
Those files came with the apt-get installation. Running texhash for "just in case" scenario didn't help. Thanks for help though.

---

### Post by JoeMetal on 2006-04-07
Apparently another thing that works for some people is this;

> For Finnish hyphenation launch texconfig in a console after installation. Select Hyphenation, and then Latex. Find the string "finnish" in the text. The line is usually commented out; uncomment it. Save and exit.

---

### Post by Tom^ on 2006-04-07
JoeMetal, please re-read my post.

---

### Post by hartl_vienna on 2006-04-10
Hi Tom^!

I've the same problem with ngerman. Did you find a solution for this problem?

---

### Post by Tom^ on 2006-04-10
hartl_vienna, no I haven't found a solution. Although I did realize that the finnish hyphenation is mentioned in /etc/texmf/language.d/10tetex.cnf and is uncommented I just can't get it to work. Here's what .log file for tex says:

```

Package babel Warning: No hyphenation patterns were loaded for
(babel)                the language `Finnish'
(babel)                I will use the patterns loaded for \language=0 instead.

```

---

