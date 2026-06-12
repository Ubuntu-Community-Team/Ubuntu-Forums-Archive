---
title: "VIM questions."
date: 2009-10-17
forum: General Help
---

### Post by munchi3s on 2009-10-17
Ok. I have two computers with ubuntu on them. First I have my server, and it is running Ubuntu 9.10 server beta. Next I have my laptop which I have ubuntu 9.10 desktop beta. My server's VI text editor is different then my laptops. My laptop is default VI and my server has different settings I.E. a colorscheme, 1 line towards the bottom that tells me if I am in Insert mode or normal mode. My arrow keys work in insert mode. I want this for my laptop but I cant get it to work. Does anyone know why my VI editor on my server is different then my VI editor on my laptop. I see a folder in my /usr/share/vim that say addons and registry but I dont really know what that means or how do I get that on my laptop.
Thanks for any help on the subject.

---

### Post by Bachstelze on 2009-10-17
You probably need to install the full version of vim

```
sudo apt-get install vim
```

Then you can edit the config file (/etc/vim/vimrc) to your liking, or just copy it over from your server.

---

### Post by munchi3s on 2009-10-17
> **Bachstelze said:**
> You probably need to install the full version of vim

```
sudo apt-get install vim
```Then you can edit the config file (/etc/vim/vimrc) to your liking, or just copy it over from your server. 

It seems that the special VIM only invokes it self when I load squid.conf Otherwise its the same as normal. Which is weird. Aslo I have lots of color schemes in my vim72 folder but When i type ":colorscheme darkblue.vim" it dosnt work. It says it cant find the colorscheme.

---

### Post by greck on 2009-11-13
> **munchi3s said:**
> It seems that the special VIM only invokes it self when I load squid.conf Otherwise its the same as normal. Which is weird. Aslo I have lots of color schemes in my vim72 folder but When i type ":colorscheme darkblue.vim" it dosnt work. It says it cant find the colorscheme.

After vim instalation (apt-get install vim vim-syntax-gtk) I have to run

```
sudo ln -s -f /usr/share/vim/vim72  /usr/share/vim/vimfiles
```to enable colorschemes.

It's really strange but it works for me

---

