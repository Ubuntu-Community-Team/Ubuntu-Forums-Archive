---
title: "imagemagick - need path of this cant find it on the HD"
date: 2010-08-29
forum: General Help
---

### Post by Bushcraft Bill on 2010-08-29
imagemagick I looked at their site and it should be in dir ether /home/lib

or /user/local/lib but no luck finding it I am sure I installed it OK...

I need the path as I have a program that needs the path to it or is their some kind of a command that will show the path to it?

Bill

---

### Post by Vaphell on 2010-08-29
whereis <command> shows where the command is stored
problem with imagemagick is that it's a package of tools and there is no command named imagemagick, thus you get no response

you need to go with updatedb && locate imagemagick to get the list of files/dirs with imagemagick being a part of the name

another option: dpkg -L imagemagick to list the files inside the imagemagick package

---

### Post by Bushcraft Bill on 2010-08-29
I see what you mean the last command worked for me ...

thanks this will help me figure out what I need!

---

