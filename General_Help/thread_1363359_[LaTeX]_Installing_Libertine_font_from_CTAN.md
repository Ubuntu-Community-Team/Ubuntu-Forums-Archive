---
title: "[LaTeX] Installing Libertine font from CTAN"
date: 2009-12-24
forum: General Help
---

### Post by Eider on 2009-12-24
I'm trying to install the Libertine font that I found on CTAN.
[http://www.ctan.org/tex-archive/fonts/libertine/](http://www.ctan.org/tex-archive/fonts/libertine/)

I've followed the second post in this thread:
[http://ubuntuforums.org/showthread.php?t=893490](http://ubuntuforums.org/showthread.php?t=893490)

But unfortunately it doesn't seem to work. 

Is there a manual anywhere available how to install a font from CTAN?

Thanks in advance!

---

### Post by gs777 on 2009-12-24
Are these fonts ttf. If yes then create a folder named .fonts in your home directory. Then put the files which have ttf extentions here and run the following command "sudo fc-cache -f -v".

---

### Post by Eider on 2009-12-24
Well I also have the ttf fonts of Libertine, which I can use in OpenOffice. But I can't use them in LaTeX.

Is there a guide to install all the files of a font from CTAN? I've tried to place them into texmf in my home directory, but that doesn't work.

---

### Post by gs777 on 2009-12-25
Try [this lin]("https://wiki.ubuntu.com/Fonts")k for fonts installation.

---

### Post by Eider on 2009-12-25
I can't use that. I need to know how to install the fonts from CTAN, that are not ttf fonts or something like that.

---

### Post by afbase on 2010-01-01
> **Eider said:**
> I'm trying to install the Libertine font that I found on CTAN.
[http://www.ctan.org/tex-archive/fonts/libertine/](http://www.ctan.org/tex-archive/fonts/libertine/)

I've followed the second post in this thread:
[http://ubuntuforums.org/showthread.php?t=893490](http://ubuntuforums.org/showthread.php?t=893490)

But unfortunately it doesn't seem to work. 

Is there a manual anywhere available how to install a font from CTAN?

Thanks in advance!

From [http://www.ctan.org/tex-archive/fonts/libertine/](http://www.ctan.org/tex-archive/fonts/libertine/)
download [libertine.zip](http://mirror.ctan.org/fonts/libertine.zip).

unzip the folder in your home directory for personal usage.  If its system wide, unzip the doc, dvips, fonts, & tex folders to /usr/share/texmf folder.

assuming you have unzipped to your personal directory: /home/user  do the following:
```

cd ~/libertine/tex/latex
latex libertine.sty
sudo texhash
sudo updmap-sys

```


in your .tex file, add in the preamble:
```
\usepackage{libertine}
```


I'm a mild newb so let me know if this works or not.

---

