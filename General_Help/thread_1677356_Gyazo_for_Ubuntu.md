---
title: "Gyazo for Ubuntu?"
date: 2011-01-28
forum: General Help
---

### Post by goyle on 2011-01-28
Hi all, i'm new here and some help.

I want to install gyazo (a popular screen grabbing tool for windows and mac) but not for ubuntu!

Any help would be appreciated!

---

### Post by Nismine on 2011-02-02
Hey,
I was in the same situation as you a couple of months ago when I migrated to Ubuntu but I've managed to make Gyazo work (although it can be a little buggy if you're using Gnome).

First you will need to install Ruby and Imagemagick (you can get them from the software center or using the terminal).
Then you go to this page [http://yaa.no-ip.org/~yaa/ddata/gyazo]("http://yaa.no-ip.org/%7Eyaa/ddata/gyazo") and save it as a .rb file.
Now you make have to allow the file to be executed as a program (right click>Properties>Permissions or use chmod +x).
And that is it, it should be working.

I hope that is not too confusing, let me know if you need something more detailed.

PS: The script I gave you is pre-configured to open with Firefox. If you want to use another browser just open it with a text editor and change the "browser_cmd" line.

---

