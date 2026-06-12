---
title: "knemo wont start in tray"
date: 2012-04-30
forum: General Help
---

### Post by Unguidedone on 2012-04-30
I installed knemo yesterday to handle a network issue and was configuring the program to start in my system tray.  I went to change the icon in the config window and it disappeared from the system tray.  If i run top in the terminal i see knemo is running but wont display a gui.

I found this for kde :
[http://www.kubuntuforums.net/showthread.php?6647-KNemo-in-tray-won-t-appear](http://www.kubuntuforums.net/showthread.php?6647-KNemo-in-tray-won-t-appear)

But I am running gnome so what command line would i use?
I also tryed uninstalling and reinstalling the program from the command line and gui and that did not work.


Some programs might be unintalled but could leave the config behind how do i uninstall the program completely so a reinstall could fix it?

---

### Post by kushdilip on 2012-07-03
It may be little late to reply but I encountered with exactly same problem today. But after lots of frustration finally solved it. I posting here the solution for people who may face this same problem again.

Solution:

[LIST]
[*]First go to synaptic manager and completely remove the ***knemo***.
[*]Now go to the directory */home/[Desktop_name]/.kde/share/config*, and delete the file *knemorc* . You can also use following command. ```
cd ~/.kde/share/config; rm knemorc
```
[*]Now reinstall the knemo from **Synaptic** or ***Software center***.
[/LIST]
Knemo will work fine as before.
And remember don't again change the theme, its a bug I think. :p

---

### Post by iMARUF on 2013-02-28
> **kushdilip said:**
> 
[LIST]
[*]First go to synaptic manager and completely remove the ***knemo***.
[*]Now go to the directory */home/[Desktop_name]/.kde/share/config*, and delete the file *knemorc* . You can also use following command. ```
cd ~/.kde/share/config; rm knemorc
```
[*]Now reinstall the knemo from **Synaptic** or ***Software center***.
[/LIST]
Thanks :)That helped :)

---

