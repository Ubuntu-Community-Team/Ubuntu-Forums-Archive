---
title: "Online Vidoes Function Wrong"
date: 2010-04-24
forum: General Help
---

### Post by Tanner2007 on 2010-04-24
Megavidoes.com
youtube.com
etc..

I have to click about a thousand times on play or any thing else to make it work and half the times dont even work no matter how many times I click on it

I have ubuntu 64 bit 

please help?

---

### Post by klemes on 2010-04-24
If you installed flash player through the official repos for amd64 then you have the 32bit flash plugin with nspluginwrapper installed.
I personally prefer in 64bit systems the 64bit Adobe flash plugin that can be downloaded from here:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

and it does not require the use of nspluginwrapper.
But before installing it you must uninstall the version that currently have installed.

---

### Post by Tanner2007 on 2010-04-24
I have no clue on how to install tar.gz on ubuntu...

---

### Post by klemes on 2010-04-24
CD to the directory you have downloaded the tar file

ie ```
cd ~/Downloads/
```then untar the package

ie ```
gzip xzvf libflashplayer*.tar.gz
```this will create a directory with libflashpayer*.so

move it to ~/.mozilla/plugins

ie ```
mkdir ~/.mozilla/plugins && mv install*/libflashplayer*.so  ~/.mozilla/plugins/

```and finally restart your browser.:popcorn:

Oh and before that uninstall any previous versions:

sudo apt-get remove --purge adobe-flashplayer  flashplugin-nonfree (or something like that-if it doesn't work use Synaptics)

---

### Post by 3rdalbum on 2010-04-24
If you encounter this problem, click outside the Flash content and then your next click in the Flash content will work.

---

