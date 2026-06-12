---
title: "Error Message!!!Please Help"
date: 2006-04-23
forum: General Help
---

### Post by morbid_bean on 2006-04-23
Im trying to add some code to the file   "/etc/rc.d/rc.local file." and when i try to save it i get the error   "Could not save the file "/etc/rc.d/rc.local"".....i need to do this to get my modem to work through my usb port.PLEASE HELP!

---

### Post by dermotti on 2006-04-23
You need to open that file as root thats why
[B]

sudo vi /etc/rc.d/rc.local[/B]

or

**gksudo gedit /etc/rc.d/rc.local**

---

### Post by morbid_bean on 2006-04-23
im quite sure i did....i typed   "sudo gedit /etc/rc.d/rc.local file"..........that is how i do it right?

---

### Post by dermotti on 2006-04-23
im pretty sure its "rc.local" not "rc.local file"

---

### Post by morbid_bean on 2006-04-23
oh yea your right ...gettin mixed up (reading a thingi on how do do something and i seen file so....)

---

### Post by morbid_bean on 2006-04-23
how do i save the file in the terminal...what do i type/press?

---

### Post by sinkxdie on 2006-04-23
I think you just copy it, paste it into another file, and replace the one in your /rc.d with it.

If not, I have no idea what I'm talking about. Lol

---

### Post by morbid_bean on 2006-04-23
ahhhh? ok wut you mean by that?

---

### Post by sinkxdie on 2006-04-23
Lol just copy the whole text in the terminal, and then create a new blank file on your desktop, paste the text into teh blank file, rename the blank file rc.local, and then replace the rc.local in your /rc.d/ directory with the new one. Sounds like it'll work. :D

---

### Post by dermotti on 2006-04-23
or else just use nano


sudo nano /etc/rc.d/rc.local

---

### Post by sinkxdie on 2006-04-23
I like my way better.
The name nano reminds me of iPod nano.
iPod's are made by Apple.
Apple is Microsoft's enemy.
I hate microsoft. So anything that makes me think of Microsoft i dont like.
So nano isn't an option for me.
:D

---

### Post by morbid_bean on 2006-04-23
hmmm the rc.d folder dosnt exist on my computer...so im guesing the refrence im using is a diffrent distribution. Ill hunt for another tutorial.:neutral:

---

### Post by sinkxdie on 2006-04-23
Wait, if there was no rc.d folder, how were you accessing an rc.local file anyway?

---

### Post by sinkxdie on 2006-04-23
[QUOTE=sinkxdie]Wait, if there was no rc.d folder, how were you accessing an rc.local file anyway?[/QUOTE]

EDIT: Just to let you know, there are other folders like rc0.d in the /etc dir.

---

### Post by morbid_bean on 2006-04-23
it looked to me as if it basicly started a new rc.local file because there was no code at all in there

---

### Post by morbid_bean on 2006-04-23
matter in fact i did a search on my computer for the file "rc.local" and didnt find nothin

---

### Post by sinkxdie on 2006-04-23
Yeah, no rc.local file in Ubuntu. :D

---

### Post by sinkxdie on 2006-04-23
Hah, I searched too. Nothing came up either. Try adding Ubuntu when you search next time for a tutorial.

---

### Post by morbid_bean on 2006-04-23
yep...ill have to find someone else who had same modem as me that got it to work in the usb and tell me how they did it.....this modem isnt that common....its only availibal in only a few places in the u.s.   ([www.ricochet.com](www.ricochet.com))

---

### Post by sinkxdie on 2006-04-23
Riochet looks new, so it probably isn't supported. Also, how are you online now?

---

### Post by morbid_bean on 2006-04-23
im on the ricochet now on the linux...it works in the serial port but not usb port......the reason i want it in the usb port it goes like 5 times faster than serial port so.....

---

### Post by sinkxdie on 2006-04-23
oh haha, let me do a little searching for you.

---

### Post by sinkxdie on 2006-04-23
Sorry, I can't find anything. :(
Im tired anyway, Im gonna go to bed :D

---

### Post by morbid_bean on 2006-04-23
This is the website i was refering to in this forum..............[http://linuxgazette.net/issue63/nielsen3.html#ricochet](http://linuxgazette.net/issue63/nielsen3.html#ricochet)

---

