---
title: "2 Ubuntu 11.04 narly narwhal(or w/e it is) problems"
date: 2011-06-21
forum: General Help
---

### Post by CorkedA on 2011-06-21
One problem is that whenever i try to install software from a deb file or try to find software in the ubuntu software center, installing from a seperate file just opens up U.S.C and when i try to find software from the software center it just sits there and searches.

My other problem is that when i try to edit files in my etc or just in my main file system im only aloud to read, not edit, and i cant change the file permissions, but im the only user, and i have admin rights, why cant i edit files? Please help!

---

### Post by nickleboyblue on 2011-06-21
To edit files on your system, you need root access.  In Ubuntu, the root user is disabled by default.  You shouldn't enable it because Ubuntu gives you sudo, the command you precede every command you need to execute as root.  For example, opening a file in the /etc directory for editing:

```
sudo gedit <filename>
```

That will give you access to it. When installing .deb files, Ubuntu tries to do this through software center.  It used to be different, but now that's how it's done.  So, if you download and try to install a .deb file, U.S.C. will come up.  It will look like it's just starting for several seconds, so be patient!  After a while, it will bring up your .deb file and give you the option to install it.

If you start navigating around inside of U.S.C. after opening it by trying to install a .deb package, it will most likely not work as expected.  U.S.C., when opened this way, will look like you simply opened it to begin with.  Again, it takes a couple of seconds before it loads the .deb file.

Welcome to the belly of the whale!

---

### Post by nickleboyblue on 2011-06-21
One more thing: since you are new, you should probably brush up on the command line just a tad.  To begin with, the command "cd <path_to_directory>" will change the terminal directory to the given location.  If you want to do this graphically without any hassle, just type:

```
sudo nautilus
```

This will open a file browser from which you can literally edit anything on your computer.  Be VERY careful when you edit stuff, especially inside of /etc.  Those files can sometimes make your system do (or not do) funky things.  Just make sure you know what you're up to.

---

### Post by CorkedA on 2011-06-21
Ok, the gedit worked, but i tryed to install a deb file again and wait this time but it just sat at the starting menu of the software center, and software center still just does searching whenever i click a catergory or search for something, help!

---

### Post by satyanash on 2011-06-21
Hmm. assuming that the file is in your Downloads directory, and you are not afraid of the command line, you could do the following:
```

cd Downloads
sudo dpkg -i your_deb_file.deb

```
The first command changes your directory to the Downloads one, and the second one installs the deb file, this is a hassle free way to install through .deb files without going/waiting through the Software Center or synaptic.
However do not close the terminal until you are dropped back to the prompt, this is typically when the previous command has stopped spewing output, and you can type back in commands normally.
Satyajeet

---

### Post by satyanash on 2011-06-21
.

---

### Post by dFlyer on 2011-06-21
Here is a few ref material for reading:

man gedit
man dpkg
man sudo
man apt-get
man bash
man gksudo

Reviewing the above will help ya in the future. It's always good to learn some command line.

---

