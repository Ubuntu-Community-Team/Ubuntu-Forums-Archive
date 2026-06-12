---
title: "&quot;You do not have the permissions ...&quot;"
date: 2012-01-21
forum: General Help
---

### Post by Airycat on 2012-01-21
I tried to save a picture into the desktop backgrounds folder and got this message:
> You do not have the permissions necessary to save the file.

I remember doing something last week where I got a similar message. Why do I not have permission to do certain things on my computer? Can I get permission? Where/how?

Not sure if this might affect anything, but right now I still have Ubuntu in Windows. Once I get all my programs either set up and working well with wine or whatever, or replaced with something adequate, I'll install it as the only OS.

---

### Post by dcstar on 2012-01-21
> **Airycat said:**
> 
I remember doing something last week where I got a similar message. Why do I not have permission to do certain things on my computer? Can I get permission? Where/how?


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mutley89 on 2012-01-21
Linux (and other unix) has a system of ownership and permissions.  Each File has an owner and an owning group, and each file can be readable, writeable, and executable by it's owner, group and everyone else.  More info here:
[http://en.wikipedia.org/wiki/Filesystem_permissions#Traditional_Unix_permissions](http://en.wikipedia.org/wiki/Filesystem_permissions#Traditional_Unix_permissions)
[http://tldp.org/LDP/intro-linux/html/sect_03_04.html](http://tldp.org/LDP/intro-linux/html/sect_03_04.html)
Most system-wide files and diectories will be owned and only writeable by the superuser, called "root", whereas most of your files within your home directory are owned by you.  To change file permissions you use the chmod command, or the properties window of the file manager.  For files not owned or writeable by you, for example to install software, you need to become root to change them.  For this use sudo(or gksu for graphical programs):
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

However where are you trying to save to? For changing the desktop background you should be able to save the image within your home directory then change it from there.

---

### Post by Airycat on 2012-01-21
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)Does this mean that anything in "File System" is something I can't/shouldn't bother with (at least until I know what I'm doing)? And did this grab whatever is in Windows? -- I see a folder of something I removed from my computer, but the folders and some files remained. This was before I installed Ubuntu.

> **mutley89 said:**
> However where are you trying to save to? For changing the desktop background you should be able to save the image within your home directory then change it from there.

 /usr/share/backgrounds. This is the folder that opens (but not as a folder) when you right click on the desktop and select "Change the Desktop Background," or click on System Settings in the upper right hand corner of the desktop and choose "Appearance." I wanted to put some of my backgrounds there so I didn't have to go looking for them any time I want to change the background on my desktop. (I can copy out of this folder, just not into it.)

Not a big deal at this point. Although I don't see why this should be a root folder requiring permission (what can having more background pictures possibly hurt?), I'm not keen on using the root or sudo now, since I don't understand enough, yet.

---

### Post by stoneage on 2012-01-21
I sometimes wonder why wallpapers are in the root file system. I guess it is for convenience and security.

Anyway, from the directory the wallpaper is in, enter > sudo cp filename.jpg /usr/share/backgrounds 

This will copy the image file to the backgrounds folder.

You can also easily add and remove images from the gui. Right click on the Desktop and choose Change Desktop Background, then add anything you want.
[[img]http://s12.postimage.org/4op6n46qx/Screenshot_6.jpg[/img]](http://postimage.org/image/4op6n46qx/)

I should add, in case things have changed since, that I still use 11.04

---

### Post by Airycat on 2012-01-27
Thank you!

> **stoneage said:**
> Anyway, from the directory the wallpaper is in, enter 
> sudo cp filename.jpg /usr/share/backgrounds
This will copy the image file to the backgrounds folder.

OK, I'm a total newb to Ubuntu... enter where? 

> You can also easily add and remove images from the gui. Right click on the Desktop and choose Change Desktop Background, then add anything you want.
[[img]http://s12.postimage.org/4op6n46qx/Screenshot_6.jpg[/img]](http://postimage.org/image/4op6n46qx/)
I knew this, but I have lots of photos I like to use and I wanted to keep them all together, rather than have to go looking for them all the time. I change my background frequently. I thought if I put it all in the original directory, then it's right there to click on for a change.

---

### Post by stinkeye on 2012-01-27
Install **Wallch** from the Ubuntu Software Centre.
Allows you to add directories and schedule wallpaper changing.

---

### Post by Airycat on 2012-01-28
> **stinkeye said:**
> Install **Wallch** from the Ubuntu Software Centre.
Allows you to add directories and schedule wallpaper changing.

Oh! Thank you!!! That's exactly what I was looking for!!

---

### Post by stoneage on 2012-01-29
> **Airycat said:**
> Thank you!
OK, I'm a total newb to Ubuntu... enter where? 
Hello, sorry I'm late back here. Enter it in the Terminal.



> **Airycat said:**
> 
I knew this, but I have lots of photos I like to use and I wanted to keep them all together, rather than have to go looking for them all the time. I change my background frequently. I thought if I put it all in the original directory, then it's right there to click on for a change.
Once you 'Add' them to the list, they stay in the list, you don't have to go looking for them again. Unless you move them frequently too........ :D

---

