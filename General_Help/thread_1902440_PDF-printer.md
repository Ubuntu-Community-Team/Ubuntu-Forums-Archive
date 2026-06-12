---
title: "PDF-printer"
date: 2011-12-30
forum: General Help
---

### Post by dreamquartz on 2011-12-30
I am trying to figure out how to print a pdf-file under Ubuntu.
The file does not have to be created in LibreOffice 3.4, but from anywhere,
There should be some kind of option that allows to select a pdf-printer, but I can not find it.
Must it be installed?

I am using 11.10.

Dream

---

### Post by howefield on 2011-12-30
You could install the package cups-pdf

```
sudo apt-get install cups-pdf
```

Or install via Ubuntu Software Centre, any documents you print to pdf will be found in your home folder inside a PDF folder.

---

### Post by Bucky Ball on 2011-12-30
Thought you could just choose 'Print to File' in the print Window rather than to your printer ...

I have PDF listed there under printers when I go to print something so maybe that is a matter of having the right packages installed. I've not installed them but am using 10.10 so slightly different I guess.

---

### Post by howefield on 2011-12-30
> **Bucky Ball said:**
> Thought you could just choose 'Print to File' in the print Window rather than to your printer ...

Yes, in a default install of the last few Ubuntu versions I did also, but not in 11.10.

---

