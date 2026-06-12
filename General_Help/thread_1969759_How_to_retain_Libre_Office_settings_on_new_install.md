---
title: "How to retain Libre Office settings on new install?"
date: 2012-04-30
forum: General Help
---

### Post by Paddy Landau on 2012-04-30
I have made a fresh installation of 12.04 today, and gosh there are plenty of problems!

Here goes my first one:

I installed 12.04 and restored all my data.

I also restored the folder [FONT=Lucida Console].libreoffice[/FONT] from my backups (I have a full backup of my original home folder, including dot-files and dot-folders).

However, my toolbar and keyboard customisations and my macros have disappeared.

How do I retain my settings from my backups?

---

### Post by uylug on 2012-04-30
> **Paddy Landau said:**
> I have made a fresh installation of 12.04 today, and gosh there are plenty of problems!

Here goes my first one:

I installed 12.04 and restored all my data.

I also restored the folder [FONT=Lucida Console].libreoffice[/FONT] from my backups (I have a full backup of my original home folder, including dot-files and dot-folders).

However, my toolbar and keyboard customisations and my macros have disappeared.

How do I retain my settings from my backups?

What version of LibreOffice are you using? And what happens if you copy everything inside your old home into your new home folder?

---

### Post by Cheesemill on 2012-04-30
Settings are in ~/.config/libreoffice/ :)

---

### Post by Paddy Landau on 2012-04-30
> **Cheesemill said:**
> Settings are in ~/.config/libreoffice/ :)
This did it, thank you.

I copied the old ~/.libreoffice to the new ~/.config/libreoffice (obviously replacing what was there).

---

