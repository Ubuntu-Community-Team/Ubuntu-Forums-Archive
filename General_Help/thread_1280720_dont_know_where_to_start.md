---
title: "???? dont know where to start ????"
date: 2009-10-02
forum: General Help
---

### Post by MAXENRELAXEN on 2009-10-02
im new to this forum today so if im posting in the wrong place , please forgive. 
iv just installed xubuntu on my ps3 and iv never used it before. i set up an external hard drive with some files that i want to accuss but every time i click on the icon for it, it acts like its going to open up, but then it just closes. how do i open or get to those files? 
 
its a 300 gb hard drive , and the xubuntu ver is 8.10
im trying to get in to a folder called games and run am emulater in there that i have so i can play some old super nes games
 
but id be happy to just get in 
 
can someone help with this

---

### Post by scragar on 2009-10-02
Can your right click the files to see what they will open with?

You might also want to open a terminal(easiest way is alt+f2 ```
xterm
```), right click the file to get the path, then type:
```
gnome-open **pathHere**/**filename**
```
To see what error messages are occuring.

---

### Post by MAXENRELAXEN on 2009-10-02
this is the error i get. error stating file'/home/maxenrelaxen/path':no such file or directory
 
 
 
the only way i can even get to the external hard drive is to right clik on the bottom task bar, and add places, click on the places icon and my external hd shows up there as SWIFNIFE2 , (cuz when i used swiss knife to for mat it to a fat 32 file system, it named it that, )

---

### Post by MAXENRELAXEN on 2009-10-02
i cant ever right click on any file and see what comand is used. it never shows me anything like that

---

### Post by scragar on 2009-10-02
> **MAXENRELAXEN said:**
> this is the error i get. error stating file'/home/maxenrelaxen/path':no such file or directory
 
 
 
the only way i can even get to the external hard drive is to right clik on the bottom task bar, and add places, click on the places icon and my external hd shows up there as SWIFNIFE2 , (cuz when i used swiss knife to for mat it to a fat 32 file system, it named it that, )

OK, let's try this:
```
cd /media
ls
```That will list currently mounted devices, most likely your external HD will be included.
```
cd **BLAH**
```Where blah is the directory name, repeat the **ls** and **cd** commands until you find what you want(please practice using [tab] to complete file names while you are at it, you'll find it saves a lot of time if you ever have to use the terminal again).

Once you've found a file try to open it using gnome-open like I said:
```
gnome-open **filename**
```

I apologise for not making the whole path part clear earlier, I just assumed you'd be able to find it correctly, doesn't matter that you couldn't, it took me ages before I even realised basic things about my system(like tab complete, or highlight-middle click being a shortcut for copy/paste, or alt+f1 being a quick way to open the main menu).


EDIT: can you tell me the file name actually? I could probably name the application that would open it, would probably be quicker.

---

### Post by MAXENRELAXEN on 2009-10-02
the eazyest way for me to explain it to u is like this:
 
on my home pc which is running xp i would go to my computer and double click on the the external hard drive , then i would double ckick on the folder called "games", then i would double click on the folder called "supper nes n all  games", now, inside this folder are all the game files and titles, as well as the emulator , its called " zsnesw " , and then all i have to do is pick out a game file, drag it over to the emulater icon and drop it on top of the i con , and it opens the game

---

### Post by scragar on 2009-10-02
snes roms?
[http://packages.ubuntu.com/search?keywords=snes&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=snes&searchon=names&suite=jaunty&section=all)

There are 3 emulators there, including zsnes, pick one, install it and try to open the files again.

PS1: install files using synaptic package manager under system, add/remove applications under applications, from the command line:```
sudo apt-get install **application name**
``` Or by clicking an apt link like this one: [install zsnes](apt:zsnes)

PS2: don't go dragging files onto other files, it doesn't do anything, your problem is that linux doesn't use windows executables, it uses it's own, unless you install wine, in which case drag and drop onto exe's still doesn't work, because that's not how things are done on linux.

---

### Post by MAXENRELAXEN on 2009-10-02
yea, im compleatly lost. iv never used this type of os before and it shows lol. 
now its not letting me see the icons on the desktop, and when i go to settings, settings manager, select desktop, and try to put a checkmark in the " let xfce manage desktop " box, the desktop icons come back, but only untill i move the mouse to click on something, then the i cons go away again, and the check box becomes unchecked again.

---

