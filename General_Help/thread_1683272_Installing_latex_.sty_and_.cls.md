---
title: "Installing latex .sty and .cls"
date: 2011-02-07
forum: General Help
---

### Post by patchwerkadams on 2011-02-07
I know there are probably a million posts like this but I looked through quite a few, tried all of the suggestions but I'm still having some problems. So, I thought I would just start a new thread and hope that someone has the exact same problem that I do, sorry if this is a repost.

I'm trying to install a .sty, .cls, and a .bst (bibtex) file for latex. I'm currently using **texlive** in Ubuntu 10.10. I have the general idea of where to install these but whenever I try to compile the .tex I get an error that says permission is denied to the .cls file, so I'm not sure what's going on.

I've ran the mktexlsr and everything else, but I still get this problem. If I run sudo pdflatex <filename>  I wind up compiling a pdf document that I can't access. Not sure if I have to add permissions to the .sty and .cls files after they've been copied, and if I do I don't know how to do that and if someone could let me know how I would greatly appreciate it.

 Additionally, the .sty and .cls files I'm using aren't in the official texlive distribution so I would definitely need to install them myself.

Any help on this would be greatly appreciated.

---

### Post by Chronon on 2011-02-07
Assuming the package is located in your LaTeX search path, you need to run "texhash" or "mktexlsr" to refresh package list.

I think you can just run:
```
sudo texhash
```
and it will locate new packages and add them.

---

### Post by P1C0 on 2011-02-07
```
*sudo apt*-*get* install *texlive*-*full*
```

Sit back and enjoy :)

---

### Post by amirfluid on 2012-08-13
> **chronon said:**
> assuming the package is located in your latex search path, you need to run "texhash" or "mktexlsr" to refresh package list.

I think you can just run:
```
sudo texhash
```
and it will locate new packages and add them.

Thanks :ks

---

