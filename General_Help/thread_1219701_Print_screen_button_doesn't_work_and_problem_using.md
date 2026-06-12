---
title: "Print screen button doesn't work and problem using screenshot"
date: 2009-07-22
forum: General Help
---

### Post by Avinash.Rao on 2009-07-22
hi,

I am using Xfce on Ubuntu Server 8.04 and the printscreen button doesn't work. 
Is there any settings to make this work? 
So, i added the Screenshot item on the panel. I want to take screenshots of adding customized items to the Panel, from the beginning for my office documentation.

I am not able to capture the " menu that appears after i right click on the panel ", after i right click, i have to click on the screenshot icon to capture, in which case the right clicked menu disappears.

How can i capture this? 

Avinash

---

### Post by kerry_s on 2009-07-22
you got to set the delay to capture menus.

you can add the screenshot program to your keyboard shortcuts.

i use mtpaint for my print, you can use xfce4-screenshooter

---

### Post by starcannon on 2009-07-22
Gimp takes a decent screen shot as well.

Run Gimp, then go to :

File>Aquire>Screenshot

Here is someone who found an answer on the dreamlinux forums; it's worth a look:[http://dreamlinuxforums.org/index.php?action=printpage%3Btopic=4015.0](http://dreamlinuxforums.org/index.php?action=printpage%3Btopic=4015.0)

As mentioned, you can set the Print Scrn. hotkey to any utility you like.

GL

---

### Post by gastly on 2009-07-22
> **Avinash.Rao said:**
> hi,

I am using Xfce on Ubuntu Server 8.04 and the printscreen button doesn't work. 
Is there any settings to make this work? 
So, i added the Screenshot item on the panel. I want to take screenshots of adding customized items to the Panel, from the beginning for my office documentation.

I am not able to capture the " menu that appears after i right click on the panel ", after i right click, i have to click on the screenshot icon to capture, in which case the right clicked menu disappears.

How can i capture this? 

Avinash
I use a tool called 'Shutter' to take screenshots. It's awesome! Try it and see if it works for you. You'll need to add it's ppa repo's to your sources.list file. Here are the instructions: [http://shutter-project.org/downloads/](http://shutter-project.org/downloads/)

---

### Post by Avinash.Rao on 2009-07-22
I dont have applications shortcut in keyboard option, coz i am using xfce.
Also, even if i can add, mtpaint is not installed.



> **kerry_s said:**
> you got to set the delay to capture menus.

you can add the screenshot program to your keyboard shortcuts.

i use mtpaint for my print, you can use xfce4-screenshooter

---

### Post by Avinash.Rao on 2009-07-22
I installed the Library, but how do i use it?? 

> **gastly said:**
> I use a tool called 'Shutter' to take screenshots. It's awesome! Try it and see if it works for you. You'll need to add it's ppa repo's to your sources.list file. Here are the instructions: [http://shutter-project.org/downloads/](http://shutter-project.org/downloads/)

---

### Post by Avinash.Rao on 2009-07-22
Xfce4-screenshooter-plugin is already installed on my machine, but how do i use xfce4-screenshooter... ??  I am not able to find xfce4-screenshooter file nor am able to install xce4-screenshooter?



> **kerry_s said:**
> you got to set the delay to capture menus.

you can add the screenshot program to your keyboard shortcuts.

i use mtpaint for my print, you can use xfce4-screenshooter

---

### Post by Avinash.Rao on 2009-07-22
I have been trying to install xfce4-screenshooter, i downloaded the package and i executed ./configure and here's wat i get.

checking for libxfce4panel-1.0 >= 4.4.0... not found
*** The required package libxfce4panel-1.0 was not found on your system.
*** Please install libxfce4panel-1.0 (atleast version 4.4.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

Where can i get Libxfce4panel-1.0 ?? 

Avinash

---

### Post by kerry_s on 2009-07-22
if you have Xfce4-screenshooter-plugin, than you have it already.
just use that command for your print key shortcut.

> I dont have applications shortcut in keyboard option, coz i am using xfce.

i am also using xfce4, see pic.

8.04 might be using a old version, you should consider using the latest version.

---

### Post by Avinash.Rao on 2009-07-22
What is the command??? 

I am using 8.04 server and there's no way i can upgrade as there are so many network services running and i found its stable on 8.04

> **kerry_s said:**
> if you have Xfce4-screenshooter-plugin, than you have it already.
just use that command for your print key shortcut.



i am also using xfce4, see pic.

8.04 might be using a old version, you should consider using the latest version.

---

### Post by kerry_s on 2009-07-22
> What is the command??? 

```
**xfce4-screenshooter**
```

try it in terminal, first see if it works.
you might want to read the man page to: **man xfce4-screenshooter**

have you figured out how to do the keyboard shortcut?
i think in the older xfce version, you click that "copy" which will make a new shortcut least which then you can edit.

---

### Post by Avinash.Rao on 2009-07-22
# xfce4-screenshooter
bash: xfce4-screenshooter: command not found

root@human:~# man xfce4-screenshooter
No manual entry for xfce4-screenshooter

I checked the keyboard shortcuts, its not letting me enter the shortcut keys..


> **kerry_s said:**
> ```
**xfce4-screenshooter**
```

try it in terminal, first see if it works.
you might want to read the man page to: **man xfce4-screenshooter**

have you figured out how to do the keyboard shortcut?
i think in the older xfce version, you click that "copy" which will make a new shortcut least which then you can edit.

---

### Post by Avinash.Rao on 2009-07-23
Guys, 

All am trying is to make the screenshot work  for menus. Is it so tough in Ubuntu? 
I am not able to install Xfce4-screenshooter, even after i installed xfce4-screenshooter-plugin, scrot doesn't serve my purpose, coz i have execute it manually from the terminal or shortcut and if i do that, the menu disappears.

I should atleast be able to map my PrtSc key to snapshot program..
:confused:

---

### Post by kerry_s on 2009-07-23
i told you you have to use a delay to capture menus, so for scrot-> 
**scrot -cd 5 %T.png**

for a 5sec delay & use the time for the file name. "man scrot" for more info.


> I should atleast be able to map my PrtSc key to snapshot program..

you just have to use the right command for the shortcut or key.

isn't there a menu item for the screen shooter?

i'm sorry, i just can't remember how the old setup was.

---

### Post by Avinash.Rao on 2009-07-24
The Scrot command worked! 

But, how do i add the shortcut, i have attached a image of my keyboard properties and even if i add a new theme, it doesn't give an option to add a shortcut, it just says no shortcut! 

Thanks


> **kerry_s said:**
> i told you you have to use a delay to capture menus, so for scrot-> 
**scrot -cd 5 %T.png**

for a 5sec delay & use the time for the file name. "man scrot" for more info.




you just have to use the right command for the shortcut or key.

isn't there a menu item for the screen shooter?

i'm sorry, i just can't remember how the old setup was.

---

### Post by kerry_s on 2009-07-24
click-> add
a window will pop up, put the name you want to use for that shortcut menu, example: mine
then click on the name of the shortcut menu you just added, it will be a exact copy of the default.
in there click-> "add" on the right side
the command window should pop up, put the command: scrot %T.png
click okay, the next window press the "print" key.
that should be it for that.
click the "add" again, this time put: scrot -d 5 %T.png
click okay, the next window press the "alt+print" key.
that will give a shortcut for the delayed screenshot.

on that you can remove the other shortcuts you don't need.
you can double click the command or the shortcut to change them for any command already made if you decide you want to use a different key/s or command.

---

### Post by Avinash.Rao on 2009-07-25
Thank you very much, it worked!
I just missed the part where you enter the key for the shortcut..

Cheers
Avinash


> **kerry_s said:**
> click-> add
a window will pop up, put the name you want to use for that shortcut menu, example: mine
then click on the name of the shortcut menu you just added, it will be a exact copy of the default.
in there click-> "add" on the right side
the command window should pop up, put the command: scrot %T.png
click okay, the next window press the "print" key.
that should be it for that.
click the "add" again, this time put: scrot -d 5 %T.png
click okay, the next window press the "alt+print" key.
that will give a shortcut for the delayed screenshot.

on that you can remove the other shortcuts you don't need.
you can double click the command or the shortcut to change them for any command already made if you decide you want to use a different key/s or command.

---

### Post by kerry_s on 2009-07-25
> **Avinash.Rao said:**
> Thank you very much, it worked!
I just missed the part where you enter the key for the shortcut..

Cheers
Avinash

no, thank you the pic helped a lot, otherwise i would not have remembered how it was.

the new 1 is so much easier now. i'm more of a mouse person so i don't use that many keyboard shortcuts.

---

### Post by Avinash.Rao on 2009-07-26
Yeah, u  mean u have the latest version of Xfce? I am using XUbuntu Desktop for LTSP and i am just a bit apprehensive on upgrading to the latest version of XUbuntu before testing them. 

I have not tried plain Xfce yet!

Cheers Mate :popcorn:
Avinash


> **kerry_s said:**
> no, thank you the pic helped a lot, otherwise i would not have remembered how it was.

the new 1 is so much easier now. i'm more of a mouse person so i don't use that many keyboard shortcuts.

---

