---
title: "mktexlsr and sudo mktexlsr"
date: 2011-09-13
forum: General Help
---

### Post by C. M .Hughes on 2011-09-13
I followed the texlive installation instructions here: [http://tug.org/texlive/acquire-netinstall.html]("http://tug.org/texlive/acquire-netinstall.html")

In particular, I added this line to my .bashrc file:

```
  PATH=/usr/local/texlive/2011/bin/i386-linux:$PATH 
```

I have a working LaTeX distribution, but wish to put my own package in

```
/usr/local/texlive/texmf-local/tex/latex/
```

If I run mktexlsr, then I get

```
mktexlsr: /usr/local/texlive/2011/texmf: directory not writable. Skipping...
mktexlsr: /usr/local/texlive/2011/texmf-config: directory not writable. Skipping...
mktexlsr: /usr/local/texlive/2011/texmf-dist: directory not writable. Skipping...
mktexlsr: /usr/local/texlive/2011/../texmf-local: directory not writable. Skipping...
mktexlsr: /usr/local/texlive/2011/texmf-var: directory not writable. Skipping...
mktexlsr: Done.

```

If I run sudo mktexlsr, then I get

```
sudo: mktexlsr: command not found
```

Does anyone know how to fix this? Many thanks.

**UPDATE**
I've found that I can put my own packages in 

```

~/texmf/tex/latex

```

and I don't have to run mktexlsr. I suppose this gets round my problem, but I'm still interested in responses.

---

### Post by rafita on 2011-10-26
You probably installed texlive as root (that is, you did some variation of sudo install-tl). The errors you are getting are a consequence that the path of the root user is different from the path of a simple user, and the folder /usr/local/texlive/ is not writeable for a simple user. You could either

1) give the whole path, i.e. sudo /usr/local/texlive/2011/bin/i386-linux/mktexlsr
2) or, better, make /usr/local/texlive writeable to you as a user, saying:
sudo chown -R <your username> /usr/local/texlive

After 2), you should be able to use mktexlsr and tlmgr without sudo. Please report if that is the case.

---

### Post by C. M .Hughes on 2011-10-26
@rafita: You're absolutely right, I installed it as sudo. Thanks for the options, I'll post back if I have any further issues.

Thanks again.

---

