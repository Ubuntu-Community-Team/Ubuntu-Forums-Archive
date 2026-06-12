---
title: "Desktop Searching for text in PDF documents"
date: 2010-01-01
forum: General Help
---

### Post by 55tptag on 2010-01-01
I have PDF files that I would like to be able to search the text of.
I tried the GNOME Search for Files program (Places->Search for Files...)  but it didn't find the PDF files that contained the text.

What do you use to search for text in PDF files?

Thank you.

---

### Post by spiderbatdad on 2010-01-01
grep should do this for you. For example cd into directory containing pdf files:
```
cd Documents
grep 'string to search' *.pdf
```This assumes the pdfs are all in the same directory, Documents, and that .pdf is not the same as .PDF

Edit: using the -r option should search subdirectories as well
```
grep -r 'string to search' /home/useranme
``` Where username gets replaced with your actual username.

---

### Post by 55tptag on 2010-01-01
Thanks for your help!

---

