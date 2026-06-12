---
title: "Individual key switch again ...."
date: 2009-10-25
forum: General Help
---

### Post by meinvateristnein on 2009-10-25
ok well in my previous post i found a way to switch individual keys in my case y and z which was the code 
xmodmap -e 'keycode 52 = z'
xmodmap -e 'keycode 29 = y' 

but ... when i restart the comp the code reverts back to the original so any code to keep the settings?? 

Any help would be great... 



PROPS to Johnny B for the code!

---

### Post by mgmiller on 2009-10-25
You could try making a script that runs at startup.

Open a terminal:
Applications > Accessories > Terminal

Create a folder in you home directory called bin (or whatever you want, but I use this in my system):
```
mkdir ~/bin
```Next, use gedit to create a file called keyswitch:
```
gedit ~/bin/keyswitch
```Next, copy the following into the file:
```
#! /bin/bash
xmodmap -e 'keycode 52 = z'
xmodmap -e 'keycode 29 = y' 
```Click save in gedit.

You can now close gedit, but keep the terminal open.

Next, make it executable:
```
chmod 777 ~/bin/keyswitch
```
You can now close the terminal.

Finally go to System > Preferences > Startup Applications and in the Startup Applications tab, click on "Add"
Give it whatever description you want and then click on the "Browse" button and navigate to the keyswitch file you just created in your home/bin directory. 
Once you have that, click the "Add" button and it should appear in the list.

That should do it.  It should run your script on every startup.

---

### Post by meinvateristnein on 2009-10-25
Thank you again and i am just saying i can not believe how helpful ubuntuforums is. it is like no other community, i can get an answer to my questions in less than 10 mins

---

### Post by mgmiller on 2009-10-25
You're welcome.

Stick with the forums and you will find one day that you'll read a question that you can answer.  The more you help, the more you learn yourself.

It's fun and gratifying and the pay is great, (ok, so the pay is purely fictional), but it still feels terrific to help others all over the world.

:popcorn:

---

