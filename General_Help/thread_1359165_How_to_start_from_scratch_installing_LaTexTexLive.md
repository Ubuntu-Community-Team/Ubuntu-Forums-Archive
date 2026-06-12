---
title: "How to start from scratch installing LaTex/TexLive?"
date: 2009-12-19
forum: General Help
---

### Post by peter_kint on 2009-12-19
Hi,

I'm on LInux now for thee months (newbie)
I'm working with Lyx for my physics and math documents,
and including pgf/tikz scripts for the graphics.

Everytime I want to use an new library or install a pgf/tikz based feature, I encounter many (apparantly unsolvable) problems.

Good people are giving me advice of which I dont know how to implement it.
             Example : use tex-manager (tlmgr) to install this or that.
             Upon checking I see I dont have tex-manager (of which the documentation             says it should be included in teh package.... (sigh)
Apparantly I messed up in previous installations, with Tex unbale to find files, libraries, etc all the time.

Therefore** I want to start from scratch** with Latex/Tex/Livetex/Lyx/pgf/tikz.

Anyone willing to coach me i this process?
Thx
Peter

---

### Post by hugmenot on 2009-12-20
You can save much hassle by installing TeXLive 2009 in a separate tree.

The Ubuntu packages (texlive-*) are installed in a fairly sophisticated system, distributed all over the file system. The main files are under /usr/share/texmf-texlive, the config under /etc, the docs under /usr/share/doc, etc.

The configuration of the official packages is also rather complicated. There are several trees where files can be placed and packages from the CTAN repo extracted. 

Then you have the problem that the TeX stuff that Ubuntu packages is a little old. When you want to install newer stuff, or unpackaged stuff, you have to get your hands quite dirty. And you have to know your way around the setup quite well.

You can download an installer from this website: 
[http://tug.org/texlive/acquire-netinstall.html](http://tug.org/texlive/acquire-netinstall.html)

(perhaps you will need perl-tk from the archives for that)

I would install into a directory like /opt/texlive2009

Afterwards you have to adjust your $PATH, so that when you call programs like 'latex' it will execute the right binaries. E.g in your ~/.profile:
```
export PATH=/opt/texlive2009/bin/i386-linux:$PATH
```

The tlmgr program is not included in Ubuntu, because they cannot figure out a way to make it work properly. It conflicts with the packaging philosophy.

If the installation worked, then installing more packages is very easy with 'tlmgr install'. But maybe you try to get the installation right first.

I can imagine that there will be problems. It depends on how much you customized already. But this should giv you a clean slate.

---

