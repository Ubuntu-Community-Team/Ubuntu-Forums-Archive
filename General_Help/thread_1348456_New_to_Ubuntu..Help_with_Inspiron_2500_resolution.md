---
title: "New to Ubuntu..Help with Inspiron 2500 resolution"
date: 2009-12-07
forum: General Help
---

### Post by orfjmc on 2009-12-07
[FONT=Arial][SIZE=3]I am very new to the Ubuntu/Linux world and could use some help. I am using a Dell Inspiron 2500 which I have 9.04 on. My problem is I cannot get my resolution to go above 800x600. I have tried to edit xorg as documented in the following thread, ( [/SIZE][/FONT][_[COLOR=#0000ff][COLOR=#0000ff][FONT=Arial][SIZE=3]http://ubuntuforums.org/showthread.php?t=750372[/SIZE][/FONT][/COLOR][/COLOR]_]("http://ubuntuforums.org/showthread.php?t=750372")[FONT=Arial][SIZE=3] ) but when I do this, I keep getting a message that Ubuntu is running in low graphics mode. Here is the process I used to update xorg, which might be the problem.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]1. Created a copy of xorg and pasted into my home folder. [/SIZE][/FONT]
[FONT=Arial][SIZE=3]2. Opened copy of xorg and replaced contents with text from above link.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]3. Pressed Ctrl-Alt-F2 and typed [/SIZE][/FONT][FONT=Arial][SIZE=3]sudo /etc/init.d/gdm stop[/SIZE][/FONT]
[FONT=Arial][SIZE=3]4. sudo cp xorg.conf /etc/X11/xorg.conf[/SIZE][/FONT]
[FONT=Arial][SIZE=3]5. sudo /etc/init.d/gdm start[/SIZE][/FONT]
[FONT=Arial][SIZE=3]At this point I get the low graphics mode errors. I was able to select troubleshoot from the menu and then edit configutaion to verify the new version had been copied over. [/SIZE][/FONT]
[FONT=Arial][SIZE=3]What is missing or what am I doing wrong?[/SIZE][/FONT]

---

### Post by jordanae on 2009-12-07
Sounds like you haven't gotten your graphics card driver yet. Just go to System> Administration> Hardware Drivers or somehting like that.

But then it should search for drivers (as long as you're connected to the internet). Install it and use the reccommended version. You should then be able to change it to a higher resolution.

---

### Post by orfjmc on 2009-12-07
There is nothing listed and after it finishes searching  I get a message that there are no propietary devices on my system.

---

### Post by orfjmc on 2009-12-10
quick question regarding editing xconf.org: is it as simple as opening the file up in a terminal and deleting the existing text, and replacing it with the recommended info?  
 
CAn anyone explain how the drivers work in Ubuntu vs. say a Windows environment?  Why do I not have any hardware drivers listed and is can they be installed in the same manner that Windwos drivers are?

---

