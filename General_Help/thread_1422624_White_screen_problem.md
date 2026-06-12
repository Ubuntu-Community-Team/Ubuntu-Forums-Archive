---
title: "White screen problem"
date: 2010-03-05
forum: General Help
---

### Post by goldengriffin on 2010-03-05
i am using acer 5738 laptop(intel GMA 4500MHD) on ubuntu 9.10....my problems are i 
cannot set the visual effect...and a blank white screen comes every time i was going to set the visual effect(which force me to make a restart) after entering the string in terminal....help me plzzzzzzzzzzzzzzzzzzzzzzzzzzzz
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

---

### Post by Intrepid Ibex on 2010-03-05
Well first off, are you actually even using the intel drivers? Also could you please post the output of "glxgears".

---

