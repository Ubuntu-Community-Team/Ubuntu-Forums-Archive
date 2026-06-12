---
title: "wine blocks programs"
date: 2010-11-05
forum: General Help
---

### Post by steveredshaw on 2010-11-05
I have just started using ubuntu 10.10 and have installed wine, however when I try to run windows programs located in the program file folder of my windows partition they get blocked

I have tried changing the permissions to allow then to run as executables but the check box in the permissions tab won't stay checked

how do I get around this - thanks

---

### Post by 3rdalbum on 2010-11-05
> **steveredshaw said:**
> I have just started using ubuntu 10.10 and have installed wine, however when I try to run windows programs located in the program file folder of my windows partition they get blocked

I have tried changing the permissions to allow then to run as executables but the check box in the permissions tab won't stay checked

how do I get around this - thanks

Firstly, most programs need to be installed into Wine, and won't work properly if you just try to run them from another Windows installation. You can try it, though - some programs do work, most don't.

Secondly, you can't change permissions of files on a filesystem that doesn't support those permissions - Windows has no concept of an execute permission. That's why the checkbox doesn't stay checked.

Thirdly, you don't need to change the execute permission. Go to a terminal and type 'wine' and then a space. Drag the program's icon to the terminal. Press Enter. This will run the program in Wine.

---

### Post by mc4man on 2010-11-05
You can also do a simple one time set up to switch the opening of .exe's from 'Wine Windows Program Loader' to just 'wine' 
(the former runs thru the 'cautious-launcher' which has a security bit restriction, the latter doesn't.

Right click on any .exe -> 'Open With -> Other Application' -> Use a custom command. For command just use 
wine
Then just click on Open

This will open the .exe thru wine, create a new Open With entry, 'wine' and make 'wine' the default for .exe's, so in the future just d. left click on any .exe.

(atm in nautilus any file or folder, when opened from the 'other application' and or custom command menu, will have the default set to the application chosen when the 'remember this ...' option is enabled -  which it is by default. It shouldn't be default enabled, but atm it is...

---

### Post by steveredshaw on 2010-11-05
thanks for that, problem solved

this behaviour took me by surprise as I have been running Mandriva for a while and had no problem running the few windows programs I needed - is ubuntu applying a tighter security check? I don't quite get why the windows programs on my own computer won't run under wine - a program that is designed to run windows programs

presumably the wine windows loader is another layer on top of the wine software(?)

---

