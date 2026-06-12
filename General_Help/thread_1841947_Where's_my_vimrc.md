---
title: "Where's my vimrc"
date: 2011-09-10
forum: General Help
---

### Post by ASCII234 on 2011-09-10
Hi!  I've just downloaded gvim from the software center, and I have no idea where my vimrc is!  Please help, thanks!

---

### Post by haqking on 2011-09-10
> **ASCII234 said:**
> Hi!  I've just downloaded gvim from the software center, and I have no idea where my vimrc is!  Please help, thanks!

Hi and welcome to the forums

it is probably hidden by default i suspect.

probably .vimrc in  ~/.vimrc 

display hidden files in your home directory

but you will want gvimrc for gvim ?

---

### Post by ASCII234 on 2011-09-10
I don't see a .vimrc in my home folder, even when I enable hidden files.  I have no idea where my vim folder even is!

---

### Post by haqking on 2011-09-10
> **ASCII234 said:**
> I don't see a .vimrc in my home folder, even when I enable hidden files.  I have no idea where my vim folder even is!


/usr/share/vim

---

### Post by ASCII234 on 2011-09-10
Thank you, I've found it, but they're readonly files :-(

---

### Post by CharlesA on 2011-09-10
I thought you had to create your own .vimrc file?

---

### Post by ASCII234 on 2011-09-10
No there's one there by default, but for some stupid reason it's readonly!

---

### Post by haqking on 2011-09-10
> **ASCII234 said:**
> Thank you, I've found it, but they're readonly files :-(


change your permissions with chmod from terminal or right clicking on it or directory. 

Though vim may be owned by root so  You will need to *gksudo nautilus* to change its permissions or from terminal


see here [http://vim.wikia.com/wiki/Keep_your_vimrc_file_clean](http://vim.wikia.com/wiki/Keep_your_vimrc_file_clean)

---

### Post by ASCII234 on 2011-09-10
Yeah I was able to open it with gksudo gedit gvimrc.  
However some of my windows settings didn't carry over well so that'll take some work :/
Also at the moment I can't move my old colorscheme into the colorscheme folder, apparently it's locked.

---

### Post by haqking on 2011-09-10
> **ASCII234 said:**
> Yeah I was able to open it with gksudo gedit gvimrc.  
However some of my windows settings didn't carry over well so that'll take some work :/


you are not in windows ;-)

glad you found it.

remember to use thread tools to mark as solved.

peace

---

### Post by sisco311 on 2011-09-10
Some applications create a default config file if it's missing others don't.

CharlesA is right. You have to create the config file. If you want to use the one from  /usr/share/vim simply copy it to ~/.vimrc:
```
cp /usr/share/vim/vimrc ~/.vimrc
```

---

### Post by haqking on 2011-09-10
> **sisco311 said:**
> Some applications create a default config file if it's missing others don't.

CharlesA is right. You have to create the config file. If you want to use the one from  /usr/share/vim simply copy it to ~/.vimrc:
```
cp /usr/share/vim/vimrc ~/.vimrc
```

+1

but i think it is gvimrc for gvim ?

.vimrc will be used for vim and gvimrc for gvim.

OP initially said gvim i believe unlesss it was a typo, unsure what one he really wants to edit ?

---

### Post by sisco311 on 2011-09-10
> **haqking said:**
> +1

but i think it is gvimrc for gvim ?

.vimrc will be used for vim and gvimrc for gvim.



Yes that's correct. I don't have gvim installed so I'm not sure if the package provides a sample .gvimrc file or not.

---

### Post by kushdilip on 2012-07-09
> **sisco311 said:**
> Yes that's correct. I don't have gvim installed so I'm not sure if the package provides a sample .gvimrc file or not.
GVim provides gvimrc in same folder /etc/share/vim similar to vimrc. 
We can use similar code provided by @haqking to copy it to ~/.gvimrc
```
cp /usr/share/vim/gvimrc ~/.gvimrc
```

---

