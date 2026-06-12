---
title: "Tex Live installation help"
date: 2009-12-16
forum: General Help
---

### Post by astrobob.tk on 2009-12-16
Hello,

I've recently followed the instructions from the "TeX Users Group" page to install TeX Live. The installation took a long time installing 1973 packages as can be seen in the code below:

```
Installing [1973/1973, time/total: 02:24:30/02:24:34]: zwpagelayout [520k]
Time used for installing the packages: 144:53
running mktexlsr /opt/texlive/2009/texmf-dist /opt/texlive/2009/texmf
mktexlsr: Updating /opt/texlive/2009/texmf-dist/ls-R... 
mktexlsr: Updating /opt/texlive/2009/texmf/ls-R... 
mktexlsr: Done.
writing fmtutil.cnf data to /opt/texlive/2009/texmf-var/web2c/fmtutil.cnf
writing updmap.cfg to /opt/texlive/2009/texmf-config/web2c/updmap.cfg
writing language.dat data to /opt/texlive/2009/texmf-var/tex/generic/config/language.dat
writing language.def data to /opt/texlive/2009/texmf-var/tex/generic/config/language.def
running mktexlsr /opt/texlive/2009/texmf-var
mktexlsr: Updating /opt/texlive/2009/texmf-var/ls-R... 
mktexlsr: Done.
running updmap-sys... done
re-running mktexlsr /opt/texlive/2009/texmf-var
mktexlsr: Updating /opt/texlive/2009/texmf-var/ls-R... 
mktexlsr: Done.
pre-generating all format files (fmtutil-sys --all), be patient...done
running package specific postactions
finished with package specific postactions

 See
   /opt/texlive/2009/index.html
 for links to documentation.  The TeX Live web site (http://tug.org/texlive/)
 contains any updates and corrections.

 TeX Live is a joint project of the TeX user groups around the world;
 please consider supporting it by joining the group best for you. The
 list of groups is available on the web at http://tug.org/usergroups.html.

 Add /opt/texlive/2009/texmf/doc/man to MANPATH.
 Add /opt/texlive/2009/texmf/doc/info to INFOPATH.
 Most importantly, add /opt/texlive/2009/bin/i386-linux
 to your PATH for current and future sessions.

 Welcome to TeX Live!

Logfile: /opt/texlive/2009/install-tl.log


```The next step as posted on the TeX Users page was to set the PATH which is also stated in the code above.

Franky I am not an advanced Linux user but here is what i've done:

```
$ PATH=/opt/texlive/2009/texmf/doc/man/MANPATH
$ PATH=/opt/texlive/2009/texmf/doc/info/INFOPATH
$ PATH=/opt/texlive/2009/bin/i386-linux
$ PATH=/opt/texlive/2009/bin/i386-linux:$PATH

```Now what I would like to know, is if i did things correctly or not? Furthermore, no I couldn't find any launcher for TeX (which to note is my first installation & to be my first use).

You help is greatly appreciated.

thx

Yours,
BOB

---

### Post by Chronon on 2009-12-16
It doesn't look like you set the environment variables properly.  

BTW, if you didn't need the 2009 version you can get TexLive from the repositories using a package manager and it will handle the configuration for you.

I use the 2007 version in the repositories and it works fine with zero fuss to install.  If you really want the 2009 version there is a thread [here](http://ubuntuforums.org/showthread.php?p=8511592#post8511592) explaining how to get it installed and configured in Ubuntu.

Also, there's no launcher for it per se.  You simply generate a source file containing the desired content and build it using a CLI compiler (e.g. latex document.tex).  There are various external programs that can provide a GUI interface to the compiler (e.g. Winefish, Geany, Kile) if you prefer.

---

### Post by astrobob.tk on 2009-12-17
well I didn't require the 2009 one but this is what i followed on Tex Live website.

here is a snapshot of the installed packages as viewed on synaptics:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=5361[/IMG]

As i mentioned in the previous thread, I followed instructions as posted on the [Tex Live website]("http://tug.org/texlive/quickinstall.html"). As also can be seen in the picture above, Tex 2007 seems to be installed isn't it ?

What is missing? & being my first time to use, should I see a launcher or menu icon?

by the way, I am not an advanced Linux user, so please help with the commands ;D

Thanks

---

### Post by Chronon on 2010-06-10
I'm really sorry that your topic got lost in the shuffle.  You can always bump it back up to the top if you don't get a response in a day or so.  

I don't see any attached picture, so I can't verify what you have done.

I *can* verify that no launchers will appear on your desktop or in menus.  TexLive provides compilers, packages, document classes, etc.  You will have to edit source files with an editor of your choice.  I have found Winefish to be a pretty nice editor for LaTeX.  It provides syntax highlighting and has configurable hotkeys for running the latex (or pdflatex, etc.) compiler/interpreter on the current file.

I have also used geany and had good experiences with that as well.  Even gedit will do an adequate job.

The best way to verify if everything is set up properly is to use a sample file and run "latex -v" from the terminal.  If the system can find the latex interpreter then it will print version information.

If you do have TexLive 2009 then you probably need to at least set the PATH variable properly.  Here's a page that suggests that doing so was necessary and sufficient for installing TexLive 2008 under Ubuntu.  [http://neoarch.wordpress.com/2008/08/16/tex-live-in-ubuntu-without-the-packages/](http://neoarch.wordpress.com/2008/08/16/tex-live-in-ubuntu-without-the-packages/)

---

### Post by astrobob.tk on 2010-07-13
> **Chronon said:**
> I'm really sorry that your topic got lost in the shuffle.  You can always bump it back up to the top if you don't get a response in a day or so.  

I don't see any attached picture, so I can't verify what you have done.

I *can* verify that no launchers will appear on your desktop or in menus.  TexLive provides compilers, packages, document classes, etc.  You will have to edit source files with an editor of your choice.  I have found Winefish to be a pretty nice editor for LaTeX.  It provides syntax highlighting and has configurable hotkeys for running the latex (or pdflatex, etc.) compiler/interpreter on the current file.

I have also used geany and had good experiences with that as well.  Even gedit will do an adequate job.

The best way to verify if everything is set up properly is to use a sample file and run "latex -v" from the terminal.  If the system can find the latex interpreter then it will print version information.

If you do have TexLive 2009 then you probably need to at least set the PATH variable properly.  Here's a page that suggests that doing so was necessary and sufficient for installing TexLive 2008 under Ubuntu.  [http://neoarch.wordpress.com/2008/08/16/tex-live-in-ubuntu-without-the-packages/](http://neoarch.wordpress.com/2008/08/16/tex-live-in-ubuntu-without-the-packages/)


Well first thx for you reply.

I just recently read another thread stating this as well. I thought something was wrong. Anyways this is my first time to learn LateX & I think LYX will be a great application to start with. specially that I read it shows me the latex code simultaneously along with what I am writing, isn't it ?

btw here's what I got for the command:

```
pdfTeX 3.1415926-1.40.10-2.2 (TeX Live 2009/Debian)
kpathsea version 5.0.0
Copyright 2009 Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
There is NO warranty.  Redistribution of this software is
covered by the terms of both the pdfTeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the pdfTeX source.
Primary author of pdfTeX: Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
Compiled with libpng 1.2.42; using libpng 1.2.42
Compiled with zlib 1.2.3.3; using zlib 1.2.3.3
Compiled with poppler version 0.12.4

```

I think thigns are ok, right ?

---

