---
title: "XeLaTeX minor math font issue"
date: 2010-01-24
forum: General Help
---

### Post by Timtro on 2010-01-24
Hi All,

I'm using XeLaTeX in an up to date Koala.

I have a document where there is a large brace set using \left\}. I'm using Adobe Garamond Pro font and the glyphs of the brace are wrong (see attached screenshot)

This has been a problem since 8.04 or so, but there's always been a quick fix that I search for which involves changing a line of a config file somewhere. I think it ovrrides the use of dvipdfmx or something. Anyhow, I can't seem to find that fix any more and I lost my text file where I document such things.

Does anyone know of this fix that I'm talking about?

---

### Post by Timtro on 2010-01-24
Actually, writing that post reminded me that it was something to do with dvipdfmx. I added that to my google search and found: [https://bugs.launchpad.net/ubuntu/+source/texlive-bin/+bug/364627](https://bugs.launchpad.net/ubuntu/+source/texlive-bin/+bug/364627)

The fix there has always worked. I'm not sure why the bug hasn't been fixed.As it is said in the post by Andrew Whyte:
> In brief, edit the configuration file: /etc/texmf/dvipdfm/dvipdfmx.cfg
Comment the line "f pdftex.map" by adding a percent symbol at the beginning of the line.
Uncomment the line "f dvipdfm.map" by removing the percent symbol.
Save and run xelatex again.

---

