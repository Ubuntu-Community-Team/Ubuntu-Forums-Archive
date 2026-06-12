---
title: "File has 2 names!  How?"
date: 2009-12-02
forum: General Help
---

### Post by bit mad on 2009-12-02
There's a file that was created by *Startup Applications* ( Mint 8 ) that I copied elsewhere and back again, and the name changed to the Name specified when I created the task. So the name appears as ***loginscr*** in Nautilus, but in a terminal it is ***login-script.sh.desktop***

[IMG]http://i48.tinypic.com/rc1u1v.jpg[/IMG]

Can any of you Linux experts explain how/why etc... please?!
Thanks :D

---

### Post by ed-koala on 2009-12-02
This is two separate files, from the look of things. One file is in /mint/.config/autostart and is called loginscr. The other file is in /mint and is called login-script.sh.

---

### Post by raktarok on 2009-12-02
They both represent the same file. Open the file in a text editor and you will understand. Or from the terminal, do this: 
```
cat /mint/.config/login-script.sh.desktop
```
There should be a field called name there, with 'loginscr' as the entry.
Nautilus (and other file managers too) shows that name when handling files ending in.desktop, but the real file name is always login-script.sh.desktop.

Here is the contents of a sample examples.desktop file, seen as Examples in file manager.
```
[Desktop Entry]
Version=1.0
Type=Link
Name=Examples
Comment=Example content for Ubuntu
URL=file:///usr/share/example-content/
X-Ubuntu-Gettext-Domain=example-content
```
 

A classic example of the use of such files would be the directory /usr/share/applications. The files there all end in .desktop too, but you see the 'Name' when viewed in nautilus. Files ending in .desktop serve as launchers when clicked from file managers like nautilus.

Hope this cleared the confusion!

---

### Post by bit mad on 2009-12-02
Excellent, many thanks for explaining that.
It had puzzled me as I solved my keyboard setting problem here [http://forums.linuxmint.com/viewtopic.php?f=60&t=36842](http://forums.linuxmint.com/viewtopic.php?f=60&t=36842)

Cheers!

---

### Post by dcstar on 2009-12-02
> **bit mad said:**
> There's a file that was created by *Startup Applications* ( Mint 8 ) that I copied elsewhere and back again, and the name changed to the Name specified when I created the task. So the name appears as ***loginscr*** in Nautilus, but in a terminal it is ***login-script.sh.desktop***

Can any of you Linux experts explain how/why etc... please?!
Thanks :D

In my system the file names in that folder are exactly the same.

---

