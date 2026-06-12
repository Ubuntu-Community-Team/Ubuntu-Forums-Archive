---
title: "MikTex"
date: 2010-01-12
forum: General Help
---

### Post by Lonnie82 on 2010-01-12
Hi,

I'm completely new to linux, but have been working with MikTex in windows and know this should work with ubuntu 9.10.

I have tried downloading the .deb and the .tar.gz but when i compile the using 

sudo dpkg -i ~/Downloads/miktex-tools-2.8_beta_2-1-i386-linux.deb

I get an error (last few lines before stop):

initexmf: Unexpected condition.
dpkg: error processing miktex-tools (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 miktex-tools

Does anyone know what I have done wrong?

Lonnie

---

### Post by audiomick on 2010-01-12
If you have a deb file, you can install it directly.  A right click should offer you the option "install with gdebi"

---

### Post by Lonnie82 on 2010-01-12
Hi,

Just tried that, but I still get an errormessage as before.

Lonnie

---

### Post by hawthornso23 on 2010-01-12
miktex is the windows version of TeX. 

As a TeXnician and ex miktex user myself let me tell you the good news is that TeX is native to a unix environment which means it is actually a lot easier to user TeX and friends on linux than on windows. There are heaps of linux tools and front ends to get the job done - a lot more than in windows actually. My advice to you would be to try out the native linux tools rather than trying to get the windows stuff you have been using working. 

In particular it makes no sense to try to use MikTeX (the windows release) on linux. The linux tex releases are texlive (the new thing we are supposed to be switching to) and tetex (the old thing which many of us are still using and which continues to work just fine).

Suggest you go into System-Administration-Synaptic and type `tex' into the search area to see what kinds of things are available. Install texlive plus whatever else takes your fancy. There are heaps of front ends to choose from. Have fun.

---

### Post by VCoolio on 2010-01-12
As above. If you want a full-featured latex editor, check out lyx. If you more or less know how it works, I recommend gedit with the gedit-latex-plugin, which has pdf preview and everything also.

---

### Post by Lonnie82 on 2010-01-13
So I installed LiveTex but now i cant save new packages when they are needed... 

I downloaded sistyle.sty and wanted to make a new directory, which i for some reason can't. I tried using the following command:
sudo mkdir usr/local/texlive/2009/texmf-dist/tex/latex/sistyleAnd also going to the directory manually but this does not work either.

Do you know how to fix this?

Lonnie

---

### Post by infestor on 2010-01-13
I would *strongly* recommend **kile** (it is in repos)

---

### Post by Lonnie82 on 2010-01-13
How do I use Kile? Just install it?

---

### Post by Lonnie82 on 2010-01-13
Sorry dum question - but I still need to download the sistyle package

---

### Post by hawthornso23 on 2010-01-13
Try to install through a proper package manager as much as possible. That way all the files will go to the right places automatically. They'll also be automatically updated whenever a new version comes out. 

Sistyle is found in the texlive-science package in synaptic. Just click to install that package and it should all go into the right directories by itself.

---

### Post by hawthornso23 on 2010-01-13
Note that pretty much everything in CTAN can be installed via synaptic. You shouldn't need to be downloading stuff from CTAN as you can install all of that stuff through synaptic. The only things you might have to deal with manually would be local things like style files specific to your university or to a particular journal which wouldn't be found on CTAN.

---

### Post by Lonnie82 on 2010-01-13
Perfect that solved it - and many other things im sure - thanks so much!!!

---

