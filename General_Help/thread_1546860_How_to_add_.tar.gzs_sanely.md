---
title: "How to add .tar.gzs sanely"
date: 2010-08-06
forum: General Help
---

### Post by unit335 on 2010-08-06
Noob issue here:

I know how to download and unzip .tar files...my questions are:

1) Is there a "best" place to unzip the archive? i.e. - a place I should think of as an analog to /Program Files in Windows?

2) How do I add a shortcut to the downloaded program to, say, the Applications>Games list?

3) Is the way to delete the program simply to delete the unzipped data?

Many thanks in advance!

---

### Post by PeEllAvaj on 2010-08-06
Other people are going to have other preferences, but I will answer your question according to my opinions.  Keep in mind that there are A LOT of valid ways of doing this.

1. If you are extracting a binary program, you can either leave it in your home director, or I like to place these type of "untracked" binaries in /opt/, so that I know I need to save them, as they will not be managed by the package management system.

2. In KDE you can just right click the icon and click on "edit menu", someone else will have to chime in if you use Gnome.

3. Yes, deleting the extracted archive will remove the program.  Keep in mind that a lot of programs will place configuration files in your home directory when you run them, so you may need or want to remove those files too, it's up to you.

Does that help?

---

### Post by prshah on 2010-08-06
> **unit335 said:**
> 
1) Is there a "best" place to unzip the archive? i.e. - a place I should think of as an analog to /Program Files in Windows?

3) Is the way to delete the program simply to delete the unzipped data?

Usually, .tar.gz programs are source code that needs to be compiled. The usual trio of commands is ```
./configure && make && make install
``` in such a situation, you cannot control where the files are installed.

If you have a particular package that does not use the "make install" route, you can use (as suggested) either /opt or /usr/local/bin. "/opt" is usually not included in the $PATH; /usr/local/bin is though, so this should probably be your preferred destination. However, it is trivial to add "/opt" to your path, or just preface the programname with "/opt/", eg, "/opt/someproggy". And, to delete it, just delete the unzipped files, and related config files, as suggested.

If your package DOES use "make install", you have two options:

a) SOME "make install" packages can be uninstalled using "make uninstall"

b) Or you can use the "checkinstall" utility (it's in the repos) to create a customised .deb file which can then be easily installed / uninstalled using the dpkg package utility (or graphically by just double clicking the .deb file); this makes it analogous to an .msi file (Microsoft Installer).

---

### Post by unit335 on 2010-08-06
Thank you. Those suggestions are very helpful! One final question...

If I follow your suggestions and place my unzipped prog in /opt or /usr/local/bin then, if I'm not mistaken, certain execute/read/write permissions change since the prog is then outside my home folder.

For example, I unzipped my prog to /usr/local/bin and it would crash as soon as it ran. I assume this happened because as soon as the prog ran it tried to update. (the prog runs from /home just fine)

If I choose to unzip the prog to the /usr folder, how do I work around the above issue? 

Thanks again!

---

