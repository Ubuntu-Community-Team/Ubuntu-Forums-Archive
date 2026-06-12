---
title: "Gimp wont load. please help."
date: 2009-10-03
forum: General Help
---

### Post by cesal on 2009-10-03
Im using ubuntu 9.04. and im pretty new to ubuntu. But i've been using the gimp program for a while. but recently it has been horrible for me. when i try to run gimp. i get the splash screen image. and on it it says Searching for brush presets. It will stay that way for about 1 minute. then the whole program will just disapeer. and sometimes it crashes my system.. i've tried uninstalling and reinstalling through aps manager, terminal, and synaptic package manager. but it still does the same thing.. this is very frustrating because i use gimp almost everyday and now i cant. if anybody knows how to fix this i would greatly appreciate it.

thanks

im also using the acer netbook laptop with ubuntu "Release 9.04 (jaunty)"

---

### Post by physic.dude on 2009-10-03
Did you try to reinstall GIMP?

---

### Post by ad_267 on 2009-10-03
Try running gimp from a terminal to see what error messages are given. Go to applications - accessories - terminal and type "gimp" then press enter.

---

### Post by Spaceman9 on 2009-10-03
My first thought is this could be a problem with running Ubuntu Desktop 9.04 on a netbook. Have you tried the Ubuntu 9.04 netbook remix? [http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

---

### Post by cesal on 2009-10-04
I have tried eebuntu and netbbok remix but 9.04 works better so far.

i got this error message when i typed Gimp into the terminal.

monte@monte-laptop:~$ gimp
/home/monte/.themes/Aurora Mini/gtk-2.0/gtkrc:505: error: unexpected keyword `class', expected character `}'
GIMP-Error: Failed to load data:

Image file '/home/monte/Documents/2009-09-19 7 mile' contains no data

GIMP-Error: Failed to load data:

Image file '/home/monte/Documents/Blue Harvest MP4' contains no data

gimp: terminated: Terminated
monte@monte-laptop:~$ 

It looks like gimp is trying to find the files in my documents folder. but they arent there.  so it bugs and crashes. when i goto my system moniter it also takes up 2-45% cpu... is there any way to fix gimp to make it run like it used too?

Thanks

---

### Post by banago on 2011-02-17
I got the same problem - were you able to fix it? Thanks!

---

### Post by WorMzy on 2011-02-17
Try this:

[LIST=1]
[*]Make sure that gimp isn't running (check with "ps -ef | grep gimp", or use the system monitor)
[*]Back up any custom brushes and whatever you want to keep from ~/.gimp-2.6
[*]Delete the .gimp-2.6 folder from your home folder.
[*]Start gimp
[/LIST]

---

### Post by banago on 2011-02-17
You made my day - THANK YOU SOOOOOO MUCH!

---

