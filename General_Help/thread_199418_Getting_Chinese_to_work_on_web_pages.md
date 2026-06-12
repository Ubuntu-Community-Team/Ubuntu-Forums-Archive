---
title: "Getting Chinese to work on web pages?"
date: 2006-06-18
forum: General Help
---

### Post by neoaddict on 2006-06-18
What packages would I have to reinstall to get Chinese to work on web pages?  Accidentally removed them while I was on a cleaning spree.

---

### Post by neoaddict on 2006-06-20
Bump.

---

### Post by neoaddict on 2006-06-21
Bump.

---

### Post by aysiu on 2006-06-21
What web browser are you using?

What command did you use to remove them? Were they installed already when you installed Ubuntu, or did you have to install them yourself?

---

### Post by neoaddict on 2006-06-21
Using Epiphany and Galeon at the moment.

I used Synaptic and removed a whole bunch of TTF fonts.

---

### Post by aysiu on 2006-06-21
I don't know. You can try any one of these packages: ```
apt-cache search chinese fonts
ttf-arphic-ukai - "AR PL ZenKai Uni" Chinese Unicode TrueType font Kaiti style
ttf-arphic-uming - "AR PL ShanHeiSun Uni" Chinese Unicode TrueType font Mingti style
chdrvfont - Kuo Chiao 16x16 font for CHDRV Chinese console terminal
cjk-latex - A LaTeX macro package for CJK (Chinese/Japanese/Korean)
emacs-intl-fonts - Fonts to allow multi-lingual PostScript printing from Emacs
qemacs - Small emacs clone editor with HTML and DocBook editing support
qemacs-nox - Small emacs clone editor (without X support)
ttf2pt1-chinese - Chinese fonts encoding maps for ttf2pt1
xcin - Chinese input server in X11
xfonts-cmex-big5p - Big5+ Chinese Mingti bitmap font (by CMEX & DynaLab) for X11xfonts-intl-chinese - International fonts for X -- Chinese
xfonts-intl-chinese-big - International fonts for X -- Chinese big
cmap-adobe-cns1 - CMaps for Adobe-CNS1
cmap-adobe-gb1 - CMaps for Adobe-GB1
gs-cjk-resource - Resource files for gs-cjk, ghostscript CJK-TrueType extension
```

---

### Post by neoaddict on 2006-06-22
xfonts-cmex-big5p seemed to be the key, thanks.  :D

---

