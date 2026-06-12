---
title: "Ubuntu 10.04 default theme file"
date: 2010-10-04
forum: General Help
---

### Post by Dustout on 2010-10-04
Where can i find the default ubuntu 10.04 theme file?


(i need it so i can make my mandriva computer look like my Ubuntu computer)

---

### Post by smilodonis on 2010-10-04
~/.themes. That's a hidden directory inside your home directory, press Ctrl-h in the file browser to see it.

Themes can also be placed in /usr/share/themes if you want them to be available for all users on the system.

---

### Post by coffeecat on 2010-10-04
The Ubuntu themes will be in /usr/share/themes. You'll need the Ambiance and  Radiance folders + contents. For the icon sets for these you'll need to  look in /usr/share/icons. You'll need the ubuntu-mono-dark,  ubuntu-mono-light, Humanity and Humanity-Dark folders and contents.

These are all owned by root. If you place the folder and contents in the equivalent places in the Mandriva filesystem (make sure they are still owned by root) then the Appearance app should pick them up for you. 

By the way, ~/.themes only contains themes you have installed yourself. It does not contain the Ubuntu themes.

> **Dustout said:**
> (i need it so i can make my mandriva computer look like my Ubuntu computer)

Why not install Ubuntu? :wink:

---

### Post by Dustout on 2010-10-04
Awesome, thanks for the help :popcorn:

Also i wish i could install ubuntu on it, but it is a public computer so no dice :mad:

---

### Post by coffeecat on 2010-10-04
I'm 90%+ sure that copying files from the various /usr locations will work OK. I used to do that quite a bit in my Gentoo days when I wanted to use a theme that caught my eye from another distro. Two small caveats: you sometimes get inconsistencies between versions of gnome, so if the Mandriva you are using has an earlier version of gnome, you might encounter problems. Also, I'm fairly sure I listed everything you need. If anything is missing, simply rummage around in /usr/share and copy anything else you think might be useful.

Of course, to complete things, you need the Ubuntu wallpaper. That's in /usr/share/backgrounds. The default wallpaper is warty-final-ubuntu.png. That's right: warty. Don't ask. :-k

Another way, if you want to have fun, and I can't guarantee it would work - I've only just thought of it - is to download the deb packages for the themes and icons from:

[http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/)

Then you could use alien to convert them to rpm packages for installation in Mandriva.

---

