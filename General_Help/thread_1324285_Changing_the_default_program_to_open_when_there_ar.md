---
title: "Changing the default program to open when there are several extensions"
date: 2009-11-12
forum: General Help
---

### Post by David López on 2009-11-12
Hi, I have a silly problem. I use Mathematica 7 in Ubuntu Karmic. Mathematica 7 'registers' the extensions *.nb, *.nbp and *.m as "Mathematica Notebook" type, to be opened with the Mathematica program.

I use another software, Octave and Matlab, that work with the *.m extensions. I want to open the *.nb extension with Mathematica, but the *.m extension with gedit. If I change in Nautilus the default program to open the *.m files, then the *.nb extension is also changed, because it's also "Mathematica Notebook".

I've installed assogiate, it says that application/mathematica and application/x-mathematica ares text/plain and they use the filename pattern *.nb, *.nbp and *.m, while text/x-matlab and text/x-octave are text/plain with the pattern *.m. However, assogiate don't allow me to remove the *.m extension from Mathematica, beacuse it only allows add, not to remove (even running assogiate as super-user, is it an error of assogiate?).

I know a way to solve, I can install systemsettings (the panel control of KDE) and remove the *.m extension of Mathematica Notebook. However I don't want to install 143MB to solve a silly problem (in Spain we say that will be '*matar moscas a cañonazos*', that is, '*[I]kill flies* with *cannon* shots[/I]'). 

There must be an easy way to solve it. Can somebody help me? Thanks.

PD: sorry for my English, I'm Spanish. I'd asked this question in the ubuntu-es forum but nobody could help me.

---

### Post by David López on 2009-11-16
Well, I've found an easy way to solve it. The conflict was in /usr/local/share/mime, there were two files (application/mathematica.xml and /packages/Wolfram-Mathematica.xml) with the incorrect asignament of the pattern="*.m" to application/mathematica instead of text/matlab. Removing glob pattern="*.m" from these files and running update-mime-database did the trick, now *.m extension is separated from *.nb and can be open with gedit.

---

