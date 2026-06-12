---
title: "From vi/vim to pdf"
date: 2011-04-28
forum: General Help
---

### Post by Krauser Joestar on 2011-04-28
Hey there everyone, first time posting here.

I've been using ubuntu for a couple of months and i've been loving it.

As for the question, i would like to know if is it possible to convert any text on vi/vim to pdf.

---

### Post by hawthornso23 on 2011-04-28
One option would be to install a pdf printer via cups-pdf. This would let you print directly to pdf file from any program that can print, including vim.

---

### Post by papibe on 2011-04-28
Not directly inside vim, but if you're familiar with the command line you can do it in a couple of steps: you can convert text to PostScript and then that to PDF. First, you need to install one of converters.

```
$ sudo apt-get install a2ps
```
or
```
$ sudo apt-get install e2ps
```

Then you can use this commands (a2ps used).
```
$ a2ps file.txt -o file.ps
$ ps2pdf file.ps file.pdf
```

I believe e2ps is easer, but a2ps has more options to format the page

Regards.

---

### Post by Krauser Joestar on 2011-04-29
Thanks for the answers guys, really appreciate it.

---

