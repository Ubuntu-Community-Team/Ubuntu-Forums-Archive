---
title: "problems with revtex4.1"
date: 2010-05-09
forum: General Help
---

### Post by gabibl on 2010-05-09
Hello, My update to ubuntu 10.04 automatically updated my revtex to revtex4.1 but 
I am having a few problems. The first  is that the natbib does not accept the \footnote{} command and so I  cannot put in footnotes in the middle of the text. The second is that  all my old revtex4 files are not being accepted anymore, as revtex4.cls  has now been replaced.
Now I removed the texlive and texlive publishers with "sudo apt-get autoremove" and tried to reinstall them with "sudo apt-et install". I made things even worse because now I not only get the message "revtex4.cls' not found" but also "revtex4.1.cls' not found" when I try using revtex4.1.
I would be very greatfull if someone could help me solve these problems urgently!

---

### Post by Mothinator on 2010-05-10
If you want to use revtex4.1 make sure your document class line reads {revtex4-1}.

If you'd prefer to continue using revtex4.0, download it from [CTAN]("http://www.tex.ac.uk/CTAN/obsolete/macros/latex/contrib/revtex4-0/") and follow the install instructions provided. Then run:

```
sudo texhash
```

from the terminal.

I'm not sure about the \footnote issue. It seems to work fine for me.

HTH!

---

