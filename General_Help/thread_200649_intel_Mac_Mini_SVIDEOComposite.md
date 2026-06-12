---
title: "intel Mac Mini SVIDEO/Composite"
date: 2006-06-20
forum: General Help
---

### Post by waPPe on 2006-06-20
Hi there,

I have a Mac Mini (Solo) with xubuntu running (dualboot osx/linux - bootcamp/refit/lilo).

Now i need to bring the mini to a TV set, no need for another display method. 

X is running, although the mouse is very slow i have no idea what is the reason for. But that is not important.
The more difficult problem is to bring the Mini to display X on a TV set.

Common solutions with TV-out do not work (in my opinion), because the Mini just has a DVI jack, plugged in a DVI to SVIDEO/Composite adapter (the original Mac one).

My question is now, what specifications (xorg settings) does this adatper need to display X correctly?
Can anyone give me a hint where i can further investigate. From my research i gues i am the only one who wants to do this *g*

Thanks for your help.
waPPe

---

### Post by waPPe on 2006-06-21
Well, i found a solution for my mouse problem. The reason for the strange behavoir was the usb port. the usb directly below the audio out does not work properly with my ubuntu.

now i use the other three and everything works just fine.


but i still do not have a idea how to make the SVIDEO/Composite to work. 

greetings 
waPPe

---

### Post by kiko-canonical on 2008-01-24
Best discussion on this topic I've seen so far is at [http://www.phoronix.com/forums/archive/index.php/t-5185.html](http://www.phoronix.com/forums/archive/index.php/t-5185.html) -- I am trying out different modelines and will tell you if I do find something that works.

---

