---
title: "Default save location for vim?"
date: 2010-11-01
forum: General Help
---

### Post by fmuise on 2010-11-01
I saved a file with vim, but not really sure where it is.

I didn't specify a save location, just :w filename.

---

### Post by eric_1982 on 2010-11-01
It will save the file in your current working directory, If you did not do a cd to another dir it will more then likely be in your home dir. 

cd ~

Note: to find your current working directory do a **pwd** command in the terminal.

---

### Post by matt_symes on 2010-11-01
Hi

... or search for it. In a terminal...

sudo updatedb  (to update locates db)
locate <filename> (to find the file)

or use find

Kind regards

---

### Post by maxsideburn on 2010-11-01
home directory

---

