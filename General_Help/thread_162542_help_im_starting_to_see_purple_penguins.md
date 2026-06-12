---
title: "help im starting to see purple penguins"
date: 2006-04-19
forum: General Help
---

### Post by cosmoshell on 2006-04-19
I think im starting to go insaine i cant seem to get help with running mupen64-0.5 . I feel as if im being surrounded by these meen evil creatures. HELLLLLLLLLP how do i use or install mupen64-0.5!!!!!!!

---

### Post by Ramses de Norre on 2006-04-19
[http://mupen64.emulation64.com/down.htm]("http://mupen64.emulation64.com/down.htm")
Download the file for linux, then do: ```
tar -xvjf /path/to/file -C ~/.mupen64
```
You can then make a menu item for it, applications > system tools > menu applications editor add entrie and for command do ~/.mupen64/mupen64
There is an icon in the folder for it too.

What's the program for?

---

### Post by cosmoshell on 2006-04-19
[QUOTE=Ramses de Norre][http://mupen64.emulation64.com/down.htm]("http://mupen64.emulation64.com/down.htm")
Download the file for linux, then do: ```
tar -xvjf /path/to/file -C ~/.mupen64
```
You can then make a menu item for it, applications > system tools > menu applications editor add entrie and for command do ~/.mupen64/mupen64
There is an icon in the folder for it too.

What's the program for?[/QUOTE]


it makes it so i can play games that are for the n64 on my computer

---

### Post by cosmoshell on 2006-04-19
when i try to open the executeable it does nothing

---

### Post by localzuk on 2006-04-19
How do you open it? Do you use the terminal and run ./mupen64 from the mupen directory?

---

### Post by cosmoshell on 2006-04-19
[QUOTE=localzuk]How do you open it? Do you use the terminal and run ./mupen64 from the mupen directory?[/QUOTE]

ive tried double clicking the icon and ./mupen64 from its directory. nothing happens

---

### Post by Ramses de Norre on 2006-04-19
I just double clicked it and it worked.. I untared it with the command I gave you, went into the directory and ran it.

---

### Post by cosmoshell on 2006-04-19
now im getting this when trying to open it from the terminal
root@ubuntu:/home/god/Desktop/downloads/mupen64-0.5# ./mupen64
./mupen64: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
root@ubuntu:/home/god/Desktop/downloads/mupen64-0.5#

---

### Post by Ramses de Norre on 2006-04-19
sudo apt-get install libgtk2.0-0 libgtk2.0-bin
I already had these.

---

### Post by cosmoshell on 2006-04-19
root@ubuntu:/home/god/Desktop/downloads/mupen64-0.5# sudo apt-get install libgtk2.0-0 libgtk2.0-bin
Reading package lists... Done
Building dependency tree... Done
libgtk2.0-0 is already the newest version.
libgtk2.0-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

---

### Post by Ramses de Norre on 2006-04-19
This is the full list of libgtk files on my system, it will be some of them I guess..
```
ii  libgtk2.0-0                            2.8.6-0ubuntu2.1     The GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.8.6-0ubuntu2.1     The programs for the GTK+ graphical user int
ii  libgtk2.0-common                       2.8.6-0ubuntu2.1     Common files for the GTK+ graphical user int
ii  libgtk2.0-dev                          2.8.6-0ubuntu2.1     Development files for the GTK+ library
ii  libgtkhtml2-0                          2.6.3-1     HTML rendering/editing library - runtime fil
ii  libgtksourceview-common                1.4.2-0ubuntu1     common files for the GTK+ syntax highlightin
ii  libgtksourceview-dev                   1.4.2-0ubuntu1     development files for the GTK+ syntax highli
ii  libgtksourceview1.0-0                  1.4.2-0ubuntu1     shared libraries for the GTK+ syntax highlig
ii  libgtkspell0                           2.0.10-2build1     a spell-checking addon for GTK's TextView wi

```

---

### Post by cosmoshell on 2006-04-19
I installed all the ones i dident have and i stiil get 

./mupen64: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

---

### Post by localzuk on 2006-04-19
That file is included in libgtk2.0-0 according to packages.ubuntu.com.

I have just noticed one thing though: you appear to be running as root? If so, you don't need to run 'sudo' when installing applications...

Have you tried running the application as an unprivileged user? (Dunno how this would help).

---

### Post by cosmoshell on 2006-04-19
ive tried it both ways and it still doesent seem to run

---

### Post by cosmoshell on 2006-04-22
help!!!! PLEASE....

---

### Post by cosmoshell on 2006-04-23
god I hate them puple penguins

---

### Post by Sef on 2006-04-23
> help im starting to see purple penguins

The reason that you are seeing purple penguins is because Microsoft has patented the black and white tuxedo look, thus the penguins are violating the patent.  Since it is nigh impossible to squeeze money out of a penguin, they are being painted purple, so they don't violate the patent.

---

### Post by cosmoshell on 2006-04-23
[QUOTE=Sef]The reason that you are seeing purple penguins is because Microsoft has patented the black and white tuxedo look, thus the penguins are violating the patent.  Since it is nigh impossible to squeeze money out of a penguin, they are being painted purple, so they don't violate the patent.[/QUOTE]
DAMB microsoft LOOSERS!!!! if you ask me the army of the peinguins should rebel and DISTROY microsoft..





hmm... thing im going to make an opensource cartoon in flash about this.

---

