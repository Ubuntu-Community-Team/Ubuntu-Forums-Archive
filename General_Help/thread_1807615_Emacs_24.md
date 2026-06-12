---
title: "Emacs 24"
date: 2011-07-19
forum: General Help
---

### Post by flebber on 2011-07-19
Hi

Is there an easier way than this guide [http://al-ix.blogspot.com/2011/02/get-emacs24-for-linux-now.html]("http://al-ix.blogspot.com/2011/02/get-emacs24-for-linux-now.html") to get emacs 24 running on ubuntu.

Emacs 24 has builds for windows available but I can't find any ready packages for ubuntu?

---

### Post by Brooksy_FC on 2011-07-19
Seems like a long process for an update. I've just installed 23 from the Software Centre

> **flebber said:**
>  Emacs 24 has builds for windows available but I can't find any ready packages for ubuntu?

I've searched around and there's nothing officially released yet. I'm not sure how long 23 has been out for, but something might get released soon.:)

---

### Post by FormatSeize on 2011-07-19
> **flebber said:**
> Hi
 
Is there an easier way than this guide [http://al-ix.blogspot.com/2011/02/get-emacs24-for-linux-now.html](http://al-ix.blogspot.com/2011/02/get-emacs24-for-linux-now.html) to get emacs 24 running on ubuntu.
 

 
If there aren't any ready-made packages for Emacs 24, then this is about as easy as it's going to get. As such, it's just a matter of following the guide and installing the program from sources. 
 
The guide in and of itself doesn't seem to contain anything in particular that looks daunting. Ubuntu is a pretty standard Linux distribution, so the directions should work as they appear as long as you have all of the things that the guide references installed (Python, the libraries, a C compiler), which I can't imagine why you wouldn't, or can't easily.
 
Is there any aspects of the guide that you can't seem to get by? Perhaps getting help completing the guide is an avenue that you'd like to follow.

---

### Post by flebber on 2011-07-19
No I wouldn't have too much issue following the guide I envisage, there were just a lot of packages to install and I didn't want to 'bloat' the system just to get emacs 24.

But having tried emacs 24 on windows I know its worth the upgrade so I guess I will complete the guide and report back how it goes.

---

### Post by flebber on 2011-07-20
Solved I have emacs 24 working. There were only a couple of minor errors that affected me during the install. One I could not find these packages to install.
```
xul-ext-adblock-plus conkeror conkeror-spawn-process-helper 
```

and the guide missed one step going straight to ./configure, I had to use ```
sudo sh autogen.sh
``` first and then was able to proceed with the compilation and make.

---

### Post by pbuckley on 2011-09-24
I followed the steps at [http://al-ix.blogspot.com/2011/02/get-emacs24-for-linux-now.html](http://al-ix.blogspot.com/2011/02/get-emacs24-for-linux-now.html) with my natty desktop and it worked well except for a few minor discrepancies that were pretty easily figured out. I commented on that blog post with the slight differences that I found. 

But today while setting up my natty laptop (installing emacs24 again) I found [http://alexhenning.github.com/blog/2010/11/05/emacs24-on-ubuntu/](http://alexhenning.github.com/blog/2010/11/05/emacs24-on-ubuntu/) which details how to get the source right from git (savannah.gnu.org) and it was much fewer steps. A lot less to install when not having to pull down the BZR repo. It too worked with just some minor discrepancies, i.e. I needed to run autoconf to create a ./configure script, install libtools, and autogen to make ./configure run without errors.

---

### Post by mboldt on 2011-11-30
Easiest way I found was to use [Damien Cassou’s emacs snapshot PPA]("https://launchpad.net/~cassou/+archive/emacs"). Instructions down to the commands to run to install [here]("http://www.mikeyboldt.com/2011/11/30/install-emacs-24-in-ubuntu/").

---

### Post by BenB1 on 2011-12-01
Have any real improvements been made to the program meriting updating it? Using 23 currently, it seems to function well for my purposes. Unless there are major bug squashing corrections, or vast functional improvements, do not usually upgrade functional software. Helps in keeping things simple and simple is beauty.

---

### Post by flebber on 2011-12-01
Well there are a lot of minor improvements to it. The functionality for importing packages ELPA/Marmalade is better integrated and allows users easier access to including extra's into their emacs. for the theme lovers it's integrated no need to rely on color-theme.

there is a good list here [http://batsov.com/articles/2011/08/19/a-peek-at-emacs24/]("http://batsov.com/articles/2011/08/19/a-peek-at-emacs24/")

As you can see there are a lot of improvements to completion, gtk, scrolling, improvements to search and deletion when editing and a lot more.

It brings a lot of improvements making it well worth the upgrade.

---

### Post by BenB1 on 2011-12-03
Thank you flebber. Upgrading to snapshot as typing here. Seems like there have been a few changes meriting the upgrade, according to what is read. S'all I really needed, "yeah, man it's more groovy now, upgrade." :)


Checks it out:  "Nice. Need to reconfigure .emacs, but that's no drama."

---

### Post by twinoatl on 2012-07-19
Your comment is awaiting moderation.

[My PPA]("https://launchpad.net/~cassou/+archive/emacs/") now has both emacs24 and emacs-snapshot:

[LIST]
[*]emacs24 will be updated only when I change the build process or when new emacs24 are realeased
[*]emacs-snapshot are updated between once a week or once every two weeks on average.
[/LIST]

Enjoy

---

