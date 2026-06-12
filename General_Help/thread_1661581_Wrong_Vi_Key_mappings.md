---
title: "Wrong Vi Key mappings"
date: 2011-01-06
forum: General Help
---

### Post by Celcius on 2011-01-06
Wrong VI key mappings.

I have a fresh install of Ubuntu 10.10 on my Dell and I think the key mappings for VI are wrong.
Everything seems ok, but then once I enter insert mode it all goes screwy,

My arrow keys type characters like 'A', 'B', 'C', 'D'
My backspace key moves me back a space, without deletion
Insert seems to capitalise the current letter I am on.
Who knows what else is going on.
I really need my arrow keys, delete, and backspace to work more than anything.

Any ideas?

---

### Post by cmoraes on 2011-01-07
Hi,

The problem is most likely *not* with your vi settings.  It is related to your terminal configuration.  Can you open a terminal and post the output of 
1. "echo $TERM"  
2. "echo $0"

Try setting TERM to "xterm" and reseting the terminal - 
1. export TERM=xterm
2. reset

---

### Post by loarf on 2011-01-29
That did not fix it for me.  Two things that did are the following:

in vi type
    ```
:set nocompatible
```or just upgrade to vim.
    ```
sudo apt-get install vim
```Hope that helps!

edit: Forgot to mention I found that here: [http://linuxblog.pansapiens.com/2007/10/31/fixing-the-arrow-keys-in-vim/](http://linuxblog.pansapiens.com/2007/10/31/fixing-the-arrow-keys-in-vim/)

---

