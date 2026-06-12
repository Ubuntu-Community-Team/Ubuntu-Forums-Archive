---
title: "Help getting my Vim back"
date: 2011-07-09
forum: General Help
---

### Post by ronin78 on 2011-07-09
Hi all,

I was having some difficulties with my Vim installation on my system (Ubuntu Server 9.10), probably due to having a lot of old plugins, and I wanted to do a fresh installation of Vim.  I used aptitude to remove all of the necessary packages, and then (forgetting that there is --purge for this purpose), I went through my system folders and deleted all of the folders containing Vim stuff.  I subsequently also ran Vim purge.

My problem is that my new Vim installation (I have installed vim and some other packages like vim-latexsuite) is missing a bunch of files, probably because I stupidly deleted them.  For instance, when I try to turn on syntax highlighting (either from .vimrc or from inside Vim), it tells me that it cannot find syntax.vim: I checked, and it is missing from the system.  If I try to brute-force it, by creating the necessary folder and adding a stock syntax.vim, it encounters additional errors, which makes me think that this is a much larger problem.

I would have thought that reinstalling the packages would reinstall all files, but I suppose that some of the files might come natively as part of the Ubuntu filesystem?  If that is true, is there any way to get my Vim back to fighting fitness without a full reinstall?  I am in the middle of a critical project, so I would prefer not to have to do a rebuild.


Regards,
Matt

---

### Post by seawolf167 on 2011-07-09
You could try to see if a fix works

```
sudo apt-get -f install
```

or even if a update & upgrade helps

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ronin78 on 2011-07-09
Thanks for the suggestion, seawolf.  I ran both and rebooted, and it did not help.  Any other suggestions?


Regards,
Matt

---

### Post by seawolf167 on 2011-07-09
And you already tried

```
sudo apt-get purge vim
sudo apt-get install vim
```

with no success?

---

### Post by WorMzy on 2011-07-09
syntax.vim is provided by the vim-runtime package. Try reinstalling that.

```
sudo apt-get install --reinstall vim-runtime
```

---

### Post by ronin78 on 2011-07-10
I had tried to purge and reinstall, without success.

WorMzy, I think that reinstalling vim-runtime did the trick!  I thought I had purged it and re-installed it before, with the other packages, but I guess not.

Thanks to both of you for your help.  I can now start Vim with no errors, and syntax highlighting appears to work, so I think I'm all set.


Regards,
Matt

---

