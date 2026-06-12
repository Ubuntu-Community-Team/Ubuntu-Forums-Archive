---
title: "neatly installing things"
date: 2006-06-16
forum: General Help
---

### Post by maniacmusician on 2006-06-16
this is a pretty newbie question....but i was wondering how and where you guys install programs when you download them from somewhere other than synaptic.

I don't really want to install them right there in my personal folder cuz thats just ******* messy, and plus, I wouldn't know how to get them to appear in my menu. So where are they supposed to go? and i've actually never (successfully) installed a program by just unpacking it and installing it, so...yeah.  What are the steps you would take to install it? 

Obviously you would first unpack, and then what? How do you compile it, where do you put it, how do you get it to run properly, and show up in the menu?

---

### Post by glotz on 2006-06-17
See for example [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by x64Jimbo on 2006-06-17
Most of the time, you'll be installing from source.
A friend of mine came up with a neat idea to keep the home directory clean. Any directory that starts with the 'dot' character will be invisible in ls and in konqueror. He decided to create a directory in his home directory called ".source" 
It's hidden all the time except when he wants to use it. I'd recommend making a directory like that and keeping your source files in there. Also, remember to keep the tarballs when you download them. Once you've compiled a program and installed it, the directory you installed from is pretty much locked to your system. If you wanted to install that same program somewhere else, you'd have to go find it and download again. 
Next, when you're installing from source, you do three commands:
./configure
make
sudo make install
If you're installing from a .deb file, (be CAREFUL - debs are usually compiled for Debian, which is what Ubuntu is based on, but they're not completely the same) you type sudo dpkg -i filename.deb

---

### Post by professor_chaos on 2006-06-17
[QUOTE=glotz]See for example [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)[/QUOTE]

When installing from source, I would recommend using the "checkinstall" command. You can see the howto from glotz's link above. This way to uninstall you can use the package manager and it keeps your system more organized.

---

### Post by maniacmusician on 2006-06-17
At that link, it describes how to install the debian menu (by installing menu-xdg). I installed that (with sudo apt-get install menu-xdg), and it told me I already have the latest version...but there is no Debian menu in my normal Apps menu.

---

### Post by professor_chaos on 2006-06-17
[QUOTE=maniacmusician]At that link, it describes how to install the debian menu (by installing menu-xdg). I installed that (with sudo apt-get install menu-xdg), and it told me I already have the latest version...but there is no Debian menu in my normal Apps menu.[/QUOTE]

This should still be applicable... [http://ubuntuforums.org/showthread.php?t=80394](http://ubuntuforums.org/showthread.php?t=80394)

---

### Post by maniacmusician on 2006-06-17
well, still no debian menu....but when i used update-menus, it added a category called "Others" to my applications menu, with all the missing apps in there...but its not organized at all, its pretty worthless that way. I should be able to move them into their proper categories using the menu editor, but the Xfce menu editor is odd, I don't really know how to use it. For instance, things like "setttings", "terminal", "File Manager", and "Web Browser", but it doesnt show any of the categories (ie. Accessories, Graphics, Multimedia, Games), so I can't edit those at all (and those are the ones I need to edit). Any suggestions?

---

### Post by maniacmusician on 2006-06-18
anyone?

---

