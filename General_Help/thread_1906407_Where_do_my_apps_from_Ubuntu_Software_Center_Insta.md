---
title: "Where do my apps from Ubuntu Software Center Install?"
date: 2012-01-09
forum: General Help
---

### Post by BNick on 2012-01-09
Where do my apps from ubuntu software center install???


??:)

---

### Post by misfitpierce on 2012-01-09
The executable file should be under /usr/bin/ most likely I'd assume.

Why are you looking for them? Do they not come up for you in Unity or whatever your using when you search or look through menus?

---

### Post by mcduck on 2012-01-09
> **BNick said:**
> Where do my apps from ubuntu software center install???


??:)

Pretty much all around the filesystem. :D Unlike in Windows, programs aren't installed into single folder "(Program Files") grouped based on the program's name or developer's name. Instead in Linux the files are put to different places in the filesystem based on each file's purpose. All the system-wide configuration files go to /etc, the program's documentation to /usr/share/doc, executable file to /usr/bin, icons to /usr/share/icons and so on. The rest of the files with no specific location usually end in /usr/share/*nameoftheprogram*.

This actually works really well once you learn the couple of important directories. No matter what the program is in question, you'll know you can find it's documentation in /usr/share/doc... And since the package management handles all the install/uninstall/update business you really don't even need to care about where most of the files are.

Anyway, when you for some reason need to find where certain package's files are, there are some helpful tools available:

"which *someprogram*" will tell you the location of the main executable file for *someprogram*. (For example "which firefox" would return "/usr/bin/firefox")

"whereis *someprogram*" gives the locaton of the main executable, documentation, and any additional directories where that program has files.

...And of course, "locate" will search for anything, so "*locate someprogram*" would give you a full list of files and directories (although remember that it searches based on file & directory names, not package information).

In addition you can always use Synaptic Package Manager to list all files that belong to a certain package, and their locations.

Edit: If you just installed something from the Software Center and it didn't appear anywhere in the menus and the Dash search can't find it, make sure it actually was a graphical application. There are plenty of command-line applications, different kinds of libraries and other types of packages for which a menu entry wouldnt even make any sense.

---

### Post by BNick on 2012-01-09
Thx a lot everyone I got I !

---

