---
title: "Vim Latex problem"
date: 2010-09-16
forum: General Help
---

### Post by hwong557 on 2010-09-16
Hi,

I just started using Vim-Latex. The default dvi output didn't work for me, so I changed the default to pdf by adding "let g:Tex_DefaultTargetFormat = 'pdf'" to my tex.vim. The only problem is that I need to save my document first (:w) before compiling it (\ll) and viewing in in Evince (\lv). If I do not save it, and run \ll and \lv, latex is run on the saved file before I started editing it, and not on the buffer containing my edited file. How do I make it so that vim saves my file and compiles my document when I hit \ll? Thanks!

---

