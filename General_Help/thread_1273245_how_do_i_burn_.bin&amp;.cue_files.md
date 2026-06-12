---
title: "how do i burn .bin&amp;.cue files?"
date: 2009-09-23
forum: General Help
---

### Post by kooley on 2009-09-23
i downloaded a file that contains .bin and .cue files and i hear u can burn them like and .iso and iv also heard hey need to be converted to .iso and i was wondering can i burn them without converting how do i go about doing it like do i need any special program to burn .bin&.cue files?Iif i need to convert them how do i got about doing that, like what program do i need and wut procedure? 

thnx in advance for help

---

### Post by scragar on 2009-09-23
[http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html](http://www.ubuntugeek.com/how-to-convert-bincue-files-to-iso-in-ubuntu.html)

Unfortunately the easiest way is to convert it to an iso and burn the iso.

EDIT: ignore me, I didn't realise that K3B supported .bin-.cue files now, it didn't last time I tried which is why I believed there was only this alternative.

---

### Post by etnlIcarus on 2009-09-23
[This should be of help](http://ubuntuforums.org/showthread.php?t=209547).

Edit: you shouldn't need to convert them before burning.

---

### Post by kooley on 2009-09-23
kk well i gota burn it on a windows computer so can i still burn a .bin on windows or do i have to convert?

---

### Post by etnlIcarus on 2009-09-23
From the tutorial:

> 1. You will need K3B (a great CD burning tool). To get this all you need to do is move you mouse up to SYSTEM in the drop down menu select ADMINISTRATION and then click on SYNAPTIC PACKAGE MANAGER (this contains lots of free software). A box will open asking for your root password enter this now. In the SYNAPTIC PACKAGE MANAGER WINDOW select search and write K3B in the search box then push return. You should get a few results but what is important is that K3B will be in the list. Select this and right click. Now select mark for installation (in the menu that appeared when you right clicked on K3B). Now push apply. The software should install (it is downloaded from the package server then installed onto your computer).

2. Now confirm that K3B has been installed by checking in applications (top left of screen in drop down menus, just point and click). Its there? If not got to Add/Remove... and use the window that opens to find and install K3B (If you figured out Package manager you will find this easy, search, point click, apply).

3. Open the K3B CD burner. You should get in program window (graphics and all). Now select BURN CD IMAGE. In the new window Click on the little blue folder in the top left. This opens another window that allows you to find your .bin/.cue file. Assuming you know were it is, select it and push ok. Now it is important to mention that you will only see a .cue file only in the open file window don't worry this is ok just click on the .cue file and it will automaticly load the .bin as well.

4. Now your ready, CD in drive push start and wrrrrrr.... You now have a CD with your .bin files on. Now use them for whatever purpose you had for them. Wasn't That was simple. Well done and Enjoy. 

Obviously use Adept instead of Synaptic, if you're using Kubuntu.

Have you tried doing this?

---

### Post by kooley on 2009-09-24
ok thanx,

but as i posted above I'm burning the files on a windows o.s not Linux as my Linux comp doesn't have a working burner atm.

by all means i am grateful for the guide though and thanks ill be sure to use it when i get a working burner on Linux

---

