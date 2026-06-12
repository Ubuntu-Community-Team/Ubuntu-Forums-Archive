---
title: "beamer autostart and poster"
date: 2009-09-29
forum: General Help
---

### Post by g.a. on 2009-09-29
Hi,

I have a problem with the beamer class (latex) with the command \movie and I'm not sure if this is a ubuntu issue or not.

I can use the command in its basic syntax, i.e., I can see a black square and, once clicked over it, the movie starts (both mpg and avi)

The option autostart and poster do not work.

the command

```
\movie[height=5cm,width=66mm,poster]{}{myvideo.mpg}
```


makes the same as

```
\movie[height=5cm,width=66mm]{}{myvideo.mpg}
```


I use:

```
ubuntu 9.04
okular 4:4.2.2-0ubuntu2
latex-beamer 3.07-1.1ubuntu1

```

and I compile with the sequence latex - dvips - ps2pdf (in order to use the psfrag packet).

I have not found any other information from the beamer manual.

Any suggestion is welcome.

g.

ps the manual clearly says that it is not possible to move around the logo... any one that did it instead? I do not really like where it is placed.

---

