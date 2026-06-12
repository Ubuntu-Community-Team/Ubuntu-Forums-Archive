---
title: "vim syntax highlighting won't turn on"
date: 2010-01-10
forum: General Help
---

### Post by cvp on 2010-01-10
Vanilla install of vim. Files as they should be in /usr/share/vim/vim72, including a sizable library in the syntax/ directory there.
":syntax on" does nothing.
":syntax enable" does nothing.
Setting VIMRUNTIME fixes nothing, and neither does moving the syntax file to my ~/.vimrc/syntax/ directory and attempting to use it as though I had written it.

I'm using gnome-terminal. Colors otherwise work just fine in my terminal; it's just vim that's the problem. gvim has the same issues that the console version has.

Please help!

---

### Post by andrew.46 on 2010-01-10
Hi cvp,

You may have a cut-down version of vim installed. From memory you can get the fuller version by simply running:
```

sudo apt-get install vim
```

Andrew

---

### Post by cvp on 2010-01-10
Nah, that's not it. I made sure to install the full vim package the first time 'round, including the vim-gnome package. "aptitude show vim" says that it's installed.
Heck, I just uninstalled and reinstalled it just now for S&G's, but the problem persists.

Any other ideas?

---

### Post by cvp on 2010-01-10
Oh. My. Flipping. Christ.

Well, I found the problem!
My .vimrc had a **runtimepath** that included /usr/share/vim/vim71. Problem is, that directory doesn't exist, as I've installed Vim 7.2, not 7.1. Bumping the number up by one (to reference /usr/share/vim/vim72, which does exist) makes everything work happy magic miracles again. Highlighting works and all.

I suppose that's a lesson in keeping your .*rc files updated when you upgrade. :p

Thanks anyway!

---

### Post by andrew.46 on 2010-01-11
Hi cvp,

Well I have to admit I would never have picked that one :).

Andrew

---

### Post by engine on 2010-03-16
Same problem, same circumstances ... and my home directory contains neither .vimrc nor .gvimrc, so I can't check there for a faulty version-reference. (thinks: don't we use nice user-friendly packages so we don't have to chase this sort of thing?)

Around the edges of the same problem, it seems I don't have an environment variable for vimruntime either
> > echo $VIMRUNTIME
>


I'm trying to use Vi - IMproved 7.2, "huge version" with GTK2-GNOME GUI. Syntax [highlighting] is included.

Thanks in advance for any farther advice.

---

### Post by geirha on 2010-03-16
Have a look at /etc/vim/vimrc  either edit it or copy the relevant parts from it to your local .vimrc.

---

### Post by engine on 2010-03-18
For whatever reason, I don't even _have_ a local .vimrc :-{

---

### Post by geirha on 2010-03-18
> **engine said:**
> For whatever reason, I don't even _have_ a local .vimrc :-{

That's normal. It's not created automatically. If you don't have a local .vimrc, it will use /etc/vim/vimrc instead. Just copy it to your homedir and edit it to your liking (it has comments explaining what the options do).

```

cp /etc/vim/vimrc ~/.vimrc
vim ~/.vimrc

```

---

### Post by engine on 2010-03-21
Thanks! local .vimrc now installed, and tweaked to match brackets 'cause that's a harmless and easy way to check whether it's being read on start-up; looks like Yes.

Still no closer to having a $VIMRUNTIME, though ... so (if it's really as easy as that) still no syntax higlighting. More tips, ideas and patient instructions please!

N

---

### Post by ibuclaw on 2010-03-21
> **engine said:**
> Thanks! local .vimrc now installed, and tweaked to match brackets 'cause that's a harmless and easy way to check whether it's being read on start-up; looks like Yes.

Still no closer to having a $VIMRUNTIME, though ... so (if it's really as easy as that) still no syntax higlighting. More tips, ideas and patient instructions please!

N

If you've installed the vim package, syntax highlighting should appear for certain file types (but not all).

A simple test would be:
```
vi /var/log/messages
```
Regards
Iain

---

### Post by geirha on 2010-03-21
Maybe post your current vimrc? There shouldn't be any need for setting VIMRUNTIME as it'll just default to /usr/share/vim/vim72. You need to make sure though, that 

```
runtime! debian.vim
```

is at the start of your vimrc.

---

### Post by engine on 2010-04-18
Well ... full reinstall since last posting, and one visible benefit is that syntax highlighting per se is now working; I followed the idea of opening /var/log/messages and there is indeed higlighting visible.

Next step, then: I have been given a higlighting file for mup (music typesetting). Given that I'm using 9.10, and that "which vim" tells me "/usr/bin/vim", where should I store the mup.vim file if I want to apply that highlighting to .mup files?

---

### Post by ibuclaw on 2010-04-20
> **engine said:**
> Well ... full reinstall since last posting, and one visible benefit is that syntax highlighting per se is now working; I followed the idea of opening /var/log/messages and there is indeed higlighting visible.

Next step, then: I have been given a higlighting file for mup (music typesetting). Given that I'm using 9.10, and that "which vim" tells me "/usr/bin/vim", where should I store the mup.vim file if I want to apply that highlighting to .mup files?

You can store it locally in your home folder.

ie:
```
mkdir -p ~/.vim
```
then copy it to that directory
```
cp mup.vim ~/.vim
```

And ensure that it is added to your runtime in ~/.vimrc
```
set runtimepath+=$HOME/.vim
```

Regards

---

### Post by engine on 2011-02-05
Thanks; that looked clear enough to follow! so I did ... and still no syntax highlighting.

q1: shouldn't all the syntax definition files be in the same directory?

q2: why does >echo $runtimepath just show me an empty line and then another prompt?

If you need any more information, just ask &#8210; I'd really like to get this sorted out.

---

### Post by ibuclaw on 2011-02-06
> **engine said:**
> Thanks; that looked clear enough to follow! so I did ... and still no syntax highlighting.

q1: shouldn't all the syntax definition files be in the same directory?

q2: why does >echo $runtimepath just show me an empty line and then another prompt?

If you need any more information, just ask &#8210; I'd really like to get this sorted out.

(10 months later ;))

My ~/.vimrc has this, which turns syntax highlighting on for all supported files.
```

if has ("syntax")
    syntax on
endif

```

Custom Syntax files go into ~/.vim/syntax/
```
mkdir -p ~/.vim/syntax
cp **mup**.vim ~/.vim/syntax

```

Sometimes detection is needed for the files, so you set them in ~/.vim/ftdetect
```
mkdir -p ~/.vim/ftdetect
vi ~/.vim/ftdetect/syntax.vim

```

And definitions are written as so:
```

"
" Custom syntax highlight defined here
" Syntax files go in ~/.vimrc/syntax
"

au BufRead,BufNewFile *.**mup**  set filetype=**mup**

```

Different reply to last time, but what you know changes drastically over long periods of time. Hope you finally resolve it. ;)

Good luck!

---

