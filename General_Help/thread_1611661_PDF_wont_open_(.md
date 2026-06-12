---
title: "PDF wont open :("
date: 2010-11-02
forum: General Help
---

### Post by Engin33r on 2010-11-02
Hey
I have always wanted to switch to Ubuntu and finally got the guts to do it and completely removed windows to install UBUNTU netbook edition.
I was having a couple of issues but after searching around i found fix for most of them except for this!
I cant seem to open PDF files...ive tried evince, gnome-open, xpdf but nothing worked
here is what I get in terminal:

```

zubair@zubair-Inspiron-1525:~/Downloads$ gnome-open Programming_Linux_Games.pdf zubair@zubair-Inspiron-1525:~/Downloads$ Error: May not be a PDF file (continuing anyway)
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table

zubair@zubair-Inspiron-1525:~/Downloads$ evince Programming_Linux_Games.pdf 
Error: May not be a PDF file (continuing anyway)
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
zubair@zubair-Inspiron-1525:~/Downloads$ open Programming_Linux_Games.pdf 
Couldn't get a file descriptor referring to the console

```

While i got some attention, i also wanted to know if I could switch from ubuntu netbook to regular ubuntu without burning another CD for regular ubuntu? 

Thanks :)

---

### Post by Engin33r on 2010-11-02
Hey
does anyone know the solution for this?
> **Engin33r said:**
> Hey
I have always wanted to switch to Ubuntu and finally got the guts to do it and completely removed windows to install UBUNTU netbook edition.
I was having a couple of issues but after searching around i found fix for most of them except for this!
I cant seem to open PDF files...ive tried evince, gnome-open, xpdf but nothing worked
here is what I get in terminal:

```

zubair@zubair-Inspiron-1525:~/Downloads$ gnome-open Programming_Linux_Games.pdf zubair@zubair-Inspiron-1525:~/Downloads$ Error: May not be a PDF file (continuing anyway)
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table

zubair@zubair-Inspiron-1525:~/Downloads$ evince Programming_Linux_Games.pdf 
Error: May not be a PDF file (continuing anyway)
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
zubair@zubair-Inspiron-1525:~/Downloads$ open Programming_Linux_Games.pdf 
Couldn't get a file descriptor referring to the console

```While i got some attention, i also wanted to know if I could switch from ubuntu netbook to regular ubuntu without burning another CD for regular ubuntu? 

Thanks :)

---

### Post by aeronutt on 2010-11-02
Have you tried opening a different pdf file? It looks like the copy of Programming_Linux_Games.pdf you're trying to open may be corrupted.

---

