---
title: "Script at my session boot dont load after reboot"
date: 2010-11-18
forum: General Help
---

### Post by HungryMelon on 2010-11-18
Hi,

I've put a script in the "startup application preference". He load fine when i close and open my session, but he didn't load if i reboot or wake up before opening my session.

That's the command i've write in the "startup application preference" : sh /home/myname/intuos.sh

(The only thing my script do for now are reversing the button on the mouse of my Intuos4)

I don't think my script are badly write, since he work manually.

Why that's not working like i want, and how i can do ?

PS: Sorry for my english.

---

### Post by ajgreeny on 2010-11-18
Just make the script executable and point directly to it, ie, without the **sh /home/myname** in front.  Just **intuos.sh** will work as long as the file is executable and in the root of your home.

---

### Post by HungryMelon on 2010-11-18
That work the same way: nothing after a reboot.

I miss some thing somewhere i think...

---

### Post by HungryMelon on 2010-11-18
I did a simple test with a script who only start a terminal when i open my session. That work fine, even after a reboot.

So, i let you see the script i've write for my Intuos :

> #!/bin/bash

#Boutons tablette
#xsetwacom set "Wacom Intuos4 4x6 pad" button2 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button3 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button4 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" AbsWUp ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button1 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" AbsWDn ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button5 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button6 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button7 ""

#Boutons stylet
#xsetwacom set "Wacom Intuos4 4x6 stylus" button1 ""
#xsetwacom set "Wacom Intuos4 4x6 stylus" button2 ""
#xsetwacom set "Wacom Intuos4 4x6 stylus" button3 ""

#Boutons souris
xsetwacom set "Wacom Intuos4 4x6 cursor" button1 "3"
#xsetwacom set "Wacom Intuos4 4x6 cursor" button2 ""
xsetwacom set "Wacom Intuos4 4x6 cursor" button3 "1"

Load of comment, i just need to see what i want on these button...

So, this is the one who dont work after a reboot.

---

### Post by ajgreeny on 2010-11-19
I have no idea what is happening here and have never needed any similar scripts about a mouse and its buttons, however, I just wonder if it is acted upon too quickly in the x-session and needs a "sleep" option as the first line:-
```
#!/bin/bash

sleep 20 &
#Boutons tablette
#xsetwacom set "Wacom Intuos4 4x6 pad" button2 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button3 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button4 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" AbsWUp ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button1 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" AbsWDn ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button5 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button6 ""
#xsetwacom set "Wacom Intuos4 4x6 pad" button7 ""

#Boutons stylet
#xsetwacom set "Wacom Intuos4 4x6 stylus" button1 ""
#xsetwacom set "Wacom Intuos4 4x6 stylus" button2 ""
#xsetwacom set "Wacom Intuos4 4x6 stylus" button3 ""

#Boutons souris
xsetwacom set "Wacom Intuos4 4x6 cursor" button1 "3"
#xsetwacom set "Wacom Intuos4 4x6 cursor" button2 ""
xsetwacom set "Wacom Intuos4 4x6 cursor" button3 "1"                      
```I'm not sure whether it needs the & at the end of the line, so try with and without to see if either works.

PS:
Are you sure that the script file is executable?
I am assuming this script does not need sudo to run.  If it does add it to /etc/rc.local just above the "exit 0" line.

---

### Post by HungryMelon on 2010-11-19
Thanks, that's working with the "sleep 20" (without the &). After a while but that's working !

Thank you.

---

### Post by ajgreeny on 2010-11-19
Great!

The delay is probably the 20 seconds that the sleep tells it to use.  That sleep option can be very useful occasionally.

---

