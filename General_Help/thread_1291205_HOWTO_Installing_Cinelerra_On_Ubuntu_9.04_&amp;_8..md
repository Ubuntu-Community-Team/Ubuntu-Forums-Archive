---
title: "HOWTO: Installing Cinelerra On Ubuntu 9.04 &amp; 8.04"
date: 2009-10-14
forum: General Help
---

### Post by mikethedj4 on 2009-10-14
Cinelerra Homepage
[http://cinelerra.org/](http://cinelerra.org/)

This is simply to help others who are having issues installing this specific piece of software.

First off add the code below to software sources.
```
deb http://akirad.cinelerra.org akirad-jaunty main
```(System>Administration>Software Sources)

Then install the file below using GDebi Package Installer.
[COLOR=Blue][http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb)[/COLOR]

Now here are the versions of Cinelerra.

_Comunity Version of Cinelerra _[INDENT] [U]*cinelerracv* (all computers)
*cinelerracv-gl* (best on computer with opengl2.0 shader)
*cinelerracv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)
[/U]  [/INDENT]_ Simeon Völkel merge between CinelerraCV2.1 and CinelerraHV4 _[INDENT] [U]*cinelerrasv* (all computers)
*cinelerrasv-gl* (best on computer with opengl2.0 shader)
*cinelerrasv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)
[/U]   [/INDENT][U] Utility[I]

cinelerra-swtc[/I] (extra Shape Wipe Transitions)[/U]

Install whatever version you want, I installed *cinelerracv*_* and *_[I]cinelerra-swtc.

[/I]So first off open up your terminal (Applications>Accessories>Terminal)

Now I'm gonna type in the code for the versions I'm going to install, you can change my version to whatever you've like to install or use mine, whatever fits you.

```
sudo apt-get install cinelerracv cinelerra-swtc
```Once it's finished installing go ahead and head to Applications>Sound & Video>Cinelerra

[CENTER] ----------------------------------------------------------------------------------------------------------------------
[/CENTER]
 
Now I don't have 8.04, but I did find a .deb file you can use, and hopefully it'll work

Now if you're not a member of the ubuntu forums, you can download the deb file from the link provided below.
[COLOR=Blue][http://www.mediafire.com/download.php?mk0wyqdgjze](http://www.mediafire.com/download.php?mk0wyqdgjze)[/COLOR]

Hopefully this tutorial helped some of you guys.

---

### Post by thesleepymoose on 2009-11-16
Thanks for this quicky, I just wanted to add a way for Ubuntu 9.04 (Jaunty) 64 bit
and FEDORA 11 64 bit to use Cinelerra 4.1 without effecting the akirad installation.

I found this page today:
[http://heroinewarrior.com/cinelerra.php#download](http://heroinewarrior.com/cinelerra.php#download)

At the bottom are source code and binaries.
If you're using Jaunty 64bit simply download the jaunty binary 
([https://sourceforge.net/projects/heroines/files/releases/cinelerra-4.1-ubu_9.04.tar.bz2/download](https://sourceforge.net/projects/heroines/files/releases/cinelerra-4.1-ubu_9.04.tar.bz2/download))
to your home folder.

Untar/extract it, it will create a folder with a similiar name.

Open the folder and doubleclick the 'cinelerra' executable to ... well execute - and voilà - you're running Cinelerra 4.1 from the folder with no install etc. 

I'm not too clued up with dependencies but It seems to work as I've got the 2.1 Akirad release and all it's dependencies through Synaptic already installed. It works better for me on a 2GB+ MPEG-2 file I've been having difficulty with that the Akirad release struggled with.

Any news when the new 4.1 will be available through akirad?
Hope this helps.

---

