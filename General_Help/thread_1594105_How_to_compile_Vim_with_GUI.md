---
title: "How to compile Vim with GUI?"
date: 2010-10-12
forum: General Help
---

### Post by mahado051 on 2010-10-12
Hi Everyone!

I want to learn how to compile vim from the sources, because there are some additions that I want to add, and learn how to deal with this situations, but until now I didn't have success doing it, I can compile vim, but without its GUI

I think it's a dependencies problem, but I can't figure out which packages I have to install, what are the dependencies to compile vim with its gui?

I found an article [COLOR="Navy"]**[about how to compile gvim]("http://aufather.wordpress.com/2010/08/15/building-gvim/")**[/COLOR], but I don't have the packages for install in my ubuntu 10.10 repositories, I hope to find some help with this

Greetings

---

### Post by stano sitar on 2010-10-16
I was looking for the same thing as you.

I used to use FreeBSD, then PC-BSD and there the compilation of Vim with graphical interface was very simple.

I found something at:
[http://ubuntuforums.org/showthread.php?t=1558288](http://ubuntuforums.org/showthread.php?t=1558288)
They sent me to vim.org, to their Wiki
[http://vim.wikia.com/wiki/Building_Vim](http://vim.wikia.com/wiki/Building_Vim)

> You need the required development packages on Ubuntu to build the GUI: 
 ```

sudo apt-get install libncurses5-dev libgnome2-dev libgnomeui-dev \ 
libgtk2.0-dev libatk1.0-dev libbonoboui2-dev \ 
libcairo2-dev libx11-dev libxpm-dev libxt-dev 
``` Commands to build and install GUI Vim: 

cd into the directory where you put the Vim source

 ```
$ cd src $ make distclean 
$ ./configure --with-features=huge --enable-gui=gnome2 
$ make 
$ sudo make install 

```it worked for me on Mint Linux Isadora. Isadora is based on Ubuntu 10.4

---

