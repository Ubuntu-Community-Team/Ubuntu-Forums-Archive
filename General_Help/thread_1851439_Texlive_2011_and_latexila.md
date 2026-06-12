---
title: "Texlive 2011 and latexila"
date: 2011-09-28
forum: General Help
---

### Post by bluefly on 2011-09-28
So, I'd like to use Texlive 2011 (ubuntu natty only has 2009 in the repository).  I downloaded it from their website, installed it, and added the requisite directories to my path.  Now I would like to install Latexila to edit my tex files.  However, when I install latexila using the usual

```
apt-get install latexila
```

it wants to install texlive along with it.  So I guess it doesn't "know" that I've already installed a newer version.  I can download Latexila from their website and install it, but then it won't install the dependent libraries that I don't have (like rubber -- which if I try to install with apt-get, also wants to install the older version of texlive).

How do I use Texlive 2011 with an editor?  

(suggestions of alternate editors are also good; I have tried gedit, and it's ok.  I like Latexila better).

---

### Post by milind_21_03 on 2011-10-05
You may use Equivs to inform the Package Manager about the dvd TeXLive installation. Have a look at the following post [http://milindpadalkar.wordpress.com/2011/06/06/inform-synaptic-package-manager-about-locally-compiled-packages/](http://milindpadalkar.wordpress.com/2011/06/06/inform-synaptic-package-manager-about-locally-compiled-packages/)

---

### Post by pjd99 on 2011-10-05
Tried Winefish a few years ago, wasn't a fan.

Did my undergrad thesis with Kile, it was OK but didn't suit the GTK themes (its a KDE app).

Currently use Texmaker. I make use of custom commands as I do most of my work with XeTeX/XeLateX and ConTeXt. My favourite these days.

---

### Post by jksai on 2011-10-16
> **bluefly said:**
> So, I'd like to use Texlive 2011 (ubuntu natty only has 2009 in the repository).  I downloaded it from their website, installed it, and added the requisite directories to my path.  Now I would like to install Latexila to edit my tex files.  However, when I install latexila using the usual

```
apt-get install latexila
```

it wants to install texlive along with it.  So I guess it doesn't "know" that I've already installed a newer version.  I can download Latexila from their website and install it, but then it won't install the dependent libraries that I don't have (like rubber -- which if I try to install with apt-get, also wants to install the older version of texlive).

How do I use Texlive 2011 with an editor?  

(suggestions of alternate editors are also good; I have tried gedit, and it's ok.  I like Latexila better).

I am new to Linux/Ubuntu. I wish to use Texlive 2011. Can you please tell me step by step installation procedure. I downloaded the install-tl-unx.tar.gz (2.4MB) file but was not able to install textlive. Please help.

---

### Post by nienaber on 2011-10-24
> **jksai said:**
> I am new to Linux/Ubuntu. I wish to use Texlive 2011. Can you please tell me step by step installation procedure. I downloaded the install-tl-unx.tar.gz (2.4MB) file but was not able to install textlive. Please help.

From: [https://launchpad.net/~latexila/+archive/ppa](https://launchpad.net/~latexila/+archive/ppa)

```
sudo add-apt-repository ppa:latexila/ppa
sudo apt-get install latexila
```

Other option is to get the package: 
[http://packages.ubuntu.com/search?keywords=latexila](http://packages.ubuntu.com/search?keywords=latexila)

---

