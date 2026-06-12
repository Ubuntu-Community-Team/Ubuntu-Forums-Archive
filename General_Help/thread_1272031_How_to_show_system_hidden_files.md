---
title: "How to show system hidden files?"
date: 2009-09-21
forum: General Help
---

### Post by Syriano on 2009-09-21
Hey there

I used to use "Properties Plus" program in Windows to give "System" and "Hidden" attributes to some files so nobody can see them normally without enabling the "view system files and folders" option.
I burned these files to a CD, then I tried to view them in Ubuntu without a chance, I tried to press Ctrl+H but it didn't work also.
so any idea how to make nautilus view them?

---

### Post by scouser73 on 2009-09-21
It is **Ctrl & H**

---

### Post by Syriano on 2009-09-21
> **scouser73 said:**
> It is **Ctrl & H**

[quote="me"]I tried to press Ctrl+H but it didn't work also.[/quote]-

---

### Post by fishyf on 2009-09-21
Can you open a terminal in the folder and type

ls -al

If there are too many files to fit in a screen, try

ls -al | less

---

### Post by s.fox on 2009-09-21
Hi,
1)** Edit -> Preferences -> View Tab**

2) Select** Show hidden and backup files**

-Silver Fox

---

### Post by ajgreeny on 2009-09-21
I don't think files that are hidden in windows will also be hidden in ubuntu.  The only way to hide them in ubuntu is to name them with a leading period/stop, ie .

Are you certain the files were actually burned to CD on windows, as if so they should be visible even without using Ctrl+H.

---

### Post by J.F. Machado Mão de Ferro on 2009-09-21
> **Syriano said:**
> Hey there

I used to use "Properties Plus" program in Windows to give "System" and "Hidden" attributes to some files so nobody can see them normally without enabling the "view system files and folders" option.
I burned these files to a CD, then I tried to view them in Ubuntu without a chance, I tried to press Ctrl+H but it didn't work also.
so any idea how to make nautilus view them?

Open a Terminal and write

gksudo nautilus

after your password

do not forget your password not apear while is writing

JFMMF

---

### Post by Syriano on 2009-09-22
this pic will expain everything:
[img]http://i38.tinypic.com/donxh3.jpg[/img]

I gave a file that "System" attribute, then burned it to a DVD. I tried to view it using nautilus but I can't find it. How I can view it?
all above mentioned methodes are tried even before telling me to try them, but nothing worked.

---

