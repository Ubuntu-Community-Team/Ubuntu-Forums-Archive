---
title: "Recovering data of Vista hard drive"
date: 2010-04-25
forum: General Help
---

### Post by XR171 on 2010-04-25
Hello all.  I've found a lot of helpfull information here before and I'm hoping my call will be answered.

I am trying to transfer files from a SATA hard drive with Windows Vista (Home Premium) installed on it.  Some files I can easily copy over, others just say Access Denied.  

I'm sure permissions is part of the issue, unofrtunately Windows is unable to boot at all (surpise surprise) so I can't adjust anything from within in.  I know with XP drives I can easily copy and paste onto my Ubuntu machine.  I'm using a SATA to USB converter that let's me plug it in and my desktop reads it like an external hard drive.

I've gone into the properties and under permissions it shows my account as having access to Create and delete files under folder access amd "---" under File access.  My group and others show None and --- for Folder and File access.  I can post a link to a screenshot tomorrow.  I've tried to also select Read and Write for File access but it goes back to the dashes before I can apply it.

I am running 64 bit Ubuntu 9.10 and do not have the sharing aspect installed.  Any questions please feel free to ask me.

Thank you and I appreciate any and all assistance.

---

### Post by SnickerSnack on 2010-04-25
Use the command line terminal (Applications>Accessories>Terminal) to move items and precede every command with "sudo", as in

```
$ sudo cp * /home/me/vistaRecover
```

Obviously, you need to create the folder vistaRecover first, or you can put the files wherever you need them.

The command line is very powerful/useful and you would do well to use it most of the time rather than the graphical user interface.  Sometimes (and at first, often) it's a bit slower than the gui, but with experience, it is much faster and more flexible.

I have a terminal launcher on my panel and also linked to a hardware button.

If you need more help with doing things in the terminal, google for 'linux command line' and 'terminal commands' first.  It shouldn't be hard to find any commands you need.

---

### Post by XR171 on 2010-04-25
I'm fairly used to using it with Windows, still trying to get comfortable with Linux commands.  Which brings me to a noob question since my desktop is still busy scannong the drive for viruses.  Its found three already.

Do I need to type the $ and *?  Thank you again.

---

### Post by ks07 on 2010-04-25
> **XR171 said:**
> I'm fairly used to using it with Windows, still trying to get comfortable with Linux commands.  Which brings me to a noob question since my desktop is still busy scannong the drive for viruses.  Its found three already.

Do I need to type the $ and *?  Thank you again.
Don't type the $ - it (or a similar character if you've changed it) will be there already. Replace the * with the path to your file, e.g. /media/windows/some_file.file .

EDIT: Easier way would be to use root nautilus, then you can copy/paste till your hearts content. Type the following into a terminal or press Alt-F2 and enter it there.
```
gksudo nautilus
```

---

### Post by rjcroy on 2010-04-25
You can also use the graphical file browser with root privileges by typing 
```
$ gksudo nautilus 
```
in a terminal. But be careful with this! You could trash your system with a unfortunate drag and click of the mouse!

One reason why this is a good excuse to get to know how to manipulate files at the command line. The command shells in Linux are really useful and powerful. Recommended!

---

### Post by SnickerSnack on 2010-04-25
> **XR171 said:**
> I'm fairly used to using it with Windows, still trying to get comfortable with Linux commands.  Which brings me to a noob question since my desktop is still busy scannong the drive for viruses.  Its found three already.

Do I need to type the $ and *?  Thank you again.

As above, don't type the $, but yes, do type the * (it's a dummy variable symbol).  Below are some directions that give exactly the commands to type and avoid the use of *.

It's true that you can use nautilus, but you're going to have to learn the command line eventually, so it's better to start now.  More detailed directions:

1) open a terminal
2) type "mkdir windowsRecover", enter.  This makes a place for the copied files.
3) type ls ```
-R /media | grep [someWord]
```, picking some word that you know will appear in the windows filesystem, maybe "desktop.ini", enter.  This will help pinpoint the location of the windows files you wish to copy.  The command "grep" sorts lines of text and looks for key words, and "|" sends the output of one command to another, so "ls | grep the" lists the files/folders in the current working directory, but only the ones with "the" in the name.
4) Suppose step three show that desktop.ini is in /media/windows/Users, type ```
ls /media/windows/Users
```, enter, and pick the username you were using out of the list.  We'll call it XR171 for now.
5) type ```
sudo cp -rf /media/windows/Users/XR171 /home/me/windowsRecover
```, enter.  This will copy the entire user directory you had in windows to a folder in your linux user directory.
6) If you instead want *everything* in the windows partition to be copied, then do ```
sudo cp -rf /media/windows/Users/XR171 /home/me/windowsRecover
```

---

### Post by XR171 on 2010-04-25
Thank you everyone!  I've played around with the various methods and each worked greatly.  I was able to recover a lot of important folders.

Thank you again!

---

