---
title: "apt-get install question"
date: 2011-09-18
forum: General Help
---

### Post by lanzd on 2011-09-18
after using the 

```
sudo apt-get install ...
```command where does the package go? lol.  I somehow have gotten around not knowing this for the past month or so but I recently installed mangler and don't know where it went.  And after using 

```
sudo apt-get install ...
```what is/are the files I need to use the program.  And how to I run them?

would it just be to type in the terminal 

```
mangler
``` with out any other command preceding it? Or something of the like for w/e program It is?

Thank you, I'm still very new to ubuntu.  Oh and I'm using 10.04 ubuntu, if that would change anything.

---

### Post by TeoBigusGeekus on 2011-09-18
```
whereis mangler
```

---

### Post by MG&amp;TL on 2011-09-18
```
sudo apt-get install <package> 
``` installs the package to the computer. 

then running the command in terminal will run it. It may also show up in Unity launcher/ Gnome taskbar.

If you want to see the source of the package, use ```
apt-get source <package>
```

---

### Post by dniMretsaM on 2011-09-18
Program executables are installed in /usr/bin. You can run the program by typing the name of the program's executable file or, if it's a graphical program, it will be in the application menu.

---

### Post by lanzd on 2011-09-18
Okay, thank you for all your help.  I can see all the programs I have currently installed in the /usr/bin folder.

---

### Post by oldos2er on 2011-09-18
**dpkg -L mangler** will show you where each file in the package 'mangler' is installed. The actual package will be stored in /var/cache/apt/archives.

You can see the same info in Synaptic Package Manager; right-click on an installed package, Properties, Installed Files.

---

