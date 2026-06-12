---
title: "How to make screenshot with mouse cursor?"
date: 2006-05-04
forum: General Help
---

### Post by zeroconf on 2006-05-04
I am a teacher and would prepare course materials in OpenOffice.org. I use Edubuntu 5.10 currently. There are a lot of different mouse cursor behaviours, what I would like to teach. But which application to use for that? Gnome-screenshot is not able to do that, also I tried Gimp - not able. Usually I use Gimp fo making screenshots, because there I can also crop image if needed (usually is needed) and use blur function to hide some text if needed.
Under Windows is Irfan View - very comfortable program. There is special key for making screenshots and there is special place, where I can choose, would I see mouse cursor or not.
So - just one row into options:
(x) include mouse cursor....

---

### Post by Sef on 2006-05-04
Place the mouse on what you want to take a snapshot of and press 
Alt + Print Screen

---

### Post by b0rka7a on 2007-12-29
I'm using Ubuntu 7.10 and when I press Alt + Print Screen it takes a screenshot of the window I selected, and not showing the cursor. I want to take a screenshot with the mouse cursor visible.

---

### Post by b0rka7a on 2007-12-29
I'm still waiting... :|

---

### Post by zeroconf on 2008-01-01
currently the only opportunity, what I know, is to install some virtual machine program (Virtualbox, VM Ware, qemu, etc.) and under that virtual environment you have to install linux and not install guest additions. Guest additions may disturb you if you switch between host and guest operating system during the screenshot creation process because screenshot taking program is installed at host but you have to open the situation in guest operating system. Then if you move mouse cursor from some menu and you have guest additions installed, then it closes that menu from you want to do screenshot due to ability switch between host and guest smoothly. Therefore are guest additions not suggested if you want to do good screenshots. Otherwise you have to use automatic screenshot feature after some seconds but it is not very comfortable and takes more time if you have to wait some seconds in every screenshot and later crop that picture.
After installing virtual machine program and requested operating system as virtual machine, you can use any screenshoting program, e.g. I use Gimp, to get screenshots with mouse cursor. It's quite complicated and needs good hardware and therefore is perhaps not suitable for everyone. Virtual machine programs have usually some dependencies and therefore are not standalone programs, which will run in any system. E.g. I have some kind of old version of Diskstate from the year 1995 and that *.exe will work also in WinXP. But Linux is developed so fast (which is actually very good), that to keep so old libraries in system is not possible.

In KSnapshot under Kubuntu 7.10 and gnome-screenshot under Ubuntu/Edubuntu/Xubuntu 7.10 there is already opportunity to include or not window decorations. Hopefully will there come also opportunity to include mouse cursor:
[http://en.wikipedia.org/wiki/KSnapshot](http://en.wikipedia.org/wiki/KSnapshot)
[http://en.wikipedia.org/wiki/Gnome-screenshot](http://en.wikipedia.org/wiki/Gnome-screenshot)

More reading is located at
[http://en.wikipedia.org/wiki/Screenshot](http://en.wikipedia.org/wiki/Screenshot)
[http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux](http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux)

---

### Post by BL00dFox on 2008-01-01
I know an easy solution :popcorn:

Take a screenshot as normal, find a render of a cursor on the net, and place it where needed! :guitar:

---

### Post by angelsguitar on 2008-01-01
I don't know if this could work, as I have not tried it; only giving it as a suggestion:

Have you tried installing and running IrfanView under wine?

---

### Post by Gen2ly on 2008-02-08
I've tried everything listed here:

[http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux](http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux)

Plus xwd

```
xwd -root > myfile.dmp && convert myfile.dmp myfile.png
```

But still no luck.  Looks like for now we're OOL.

---

### Post by sagara on 2008-02-27
This is a 2 year old thread with no answer yet... anybody know how to acomplis this?

A screenshot with the mouse cursor included?

---

### Post by Gen2ly on 2008-02-28
bad bad.  I need to post this - import png.   The command import will do the job, just add the name.filetype.

---

### Post by sagara on 2008-02-28
I tried using this import command as import screenshot.jpg
The mouse cursor changed to a cross, I clicked on a window an a screenshot of that window was taken but no cursor in it...

Is this the expected behaviour of this command?

---

