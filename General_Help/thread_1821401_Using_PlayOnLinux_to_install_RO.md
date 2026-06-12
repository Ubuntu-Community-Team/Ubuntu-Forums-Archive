---
title: "Using PlayOnLinux to install RO"
date: 2011-08-09
forum: General Help
---

### Post by felinoel on 2011-08-09
Ok so I followed the directions on their site and came up with having to write a script that told it what to do and run it through the program, based on what the site said I made this...

```
$HOME/.PlayOnLinux/wineprefix/
$HOME/Desktop/RO.msi
POL_SetupWindow_make_shortcut "RO" "/home/michael/Desktop/" "RO.msi" "" "RO"
```

But I keep getting permission denied no matter how much I alter it?

```
/home/michael/Desktop/RO: line 2: /home/michael/.PlayOnLinux/wineprefix/: is a directory
/home/michael/Desktop/RO: line 3: /home/michael/Desktop/RO.msi: **Permission denied**
/home/michael/Desktop/RO: line 4: POL_SetupWindow_make_shortcut: command not found
```

How do I get proper permissions?

---

### Post by dethorpe on 2011-08-09
I assume you are using wine to try and run this.
 
Can you post link to the instructions you are trying to follow, can see problems with script but don't know what it is trying to do, so can't offer full solution.
 
Some issues with the script are:
 
1) 1st line is just path to a directory, hence the error. Should it by changing to the directory with "cd" or running a script from the dir?
 
2) 2nd line is trying to run the file "RO.msi", can you do that with windows msi file? If so then need to give yourself read and execute permissions on it before running script:
 
```
 
chmod +rx $HOME/Desktop/RO.msi
 

```
 
3) on 3rd line shell can't find "POL_SetupWindow_make_shortcut" in your path, need to add it to $PATH or use full pathname in script.

---

### Post by felinoel on 2011-08-09
Oh... am I using wine? hmmm I just thought it was a wine substitute or addon even maybe 

[http://www.playonlinux.com/en/dev-documentation-5.html](http://www.playonlinux.com/en/dev-documentation-5.html)

---

### Post by Mark Phelps on 2011-08-09
The .msi file is a "Windows Installer" file -- which is used to install an application, not to run it.  You can't just run the app from the installer file, you have to actually install it first.

---

### Post by felinoel on 2011-08-09
> **Mark Phelps said:**
> The .msi file is a "Windows Installer" file -- which is used to install an application, not to run it.  You can't just run the app from the installer file, you have to actually install it first.

Oh hmm that makes sense <.<;

---

### Post by dethorpe on 2011-08-10
> **felinoel said:**
> Oh... am I using wine? hmmm I just thought it was a wine substitute or addon even maybe 
 
[http://www.playonlinux.com/en/dev-documentation-5.html](http://www.playonlinux.com/en/dev-documentation-5.html)
 
Play on Linux uses wine under the hood. I Know nothing about it though :-) so will defer to others to help with your installation problem, except for any specific scripting issues which i can help with. 
 
Good luck

---

