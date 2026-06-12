---
title: "&quot;new login&quot; help/question"
date: 2006-06-28
forum: General Help
---

### Post by Polygon on 2006-06-28
*update*, see later posts

Hello,

one of the things i liked about windows xp was that you could switch users without closing all of your programs, which was helpful if my brother or dad needed to use my computer for example.

I thought this feature wasnt in ubuntu until recently, just trying out some random things in "system tools" led me to the "new login" feature which basically lets me switch users and let my programs keep running. yay!

but... there is one problem with it and i would like to know if there is a way to solve it. After i double click" new login" it goes back to the login screen and says "already logged in" under my name, so far so good. But after a long period of time, like when the screensaver comes on, after i come out of it, it requires MY password to access the computer again and to login as someone else.

so... is there anyway to diable that extra password check after i use "new login" and bring the computer out of screensaver mode?

thanks!

---

### Post by aysiu on 2006-06-28
It should ask you for your password only after the new person has logged out.

This behavior with the "already logged in" and the screensaver isn't normal.

---

### Post by scxtt on 2006-06-28
also check that "Lock screen when screensaver is active" isn't checked ...

System --> Preferences --> Screensaver

---

### Post by Polygon on 2006-06-28
no scxtt, that button is not checked.

here, let me explain this a little better

*i click "new login" to log out without all of my programs being closed
*Ubuntu returns to the login screen with "already logged in" under my username
*i go to bed
*the next morning, i turn on the monitor, and i see a blank screen
*when i move the mouse, this window pops up that says "mark@ubuntu" or something and it asks for my password
*if i press "cancel", the window dissapears and then when i move the mouse it reappears and asks for my password again
*when i do enter my password, it comes out of that black screen thing and returns to the login window

now my question is, why is it requiring my (mark's) password to unlock the screen after i use newlogin and the computer is idle? and if this is not normal, how do i fix it? thanks

---

### Post by Polygon on 2006-06-28
bump

---

### Post by MacMan on 2006-06-29
[QUOTE=Polygon]*if i press "cancel", the window dissapears and then when i move the mouse it reappears and asks for my password again
*when i do enter my password, it comes out of that black screen thing and returns to the login window
[/QUOTE]

Polygon, 
I'm not sure if this can be helpful. Anyway if I understand correctly, when you use the "new login" function a new X session is created. You can switch between those sessions using the CTRL + ALT + <F-key> combo. For example you open the first X session with CTRL + ALT + F7, the second with CTRL + ALT + F8 and so on.

So maybe to see the login prompt you just need to switch between sessions until you find the one with the login app on.

Can't try it myself now so I can't be 100% sure this applies to you. Anyway I hope this helps.

Ciao.
-- 
MacMan

---

### Post by honda on 2006-06-29
I have no solution, I just like to describe my similar problems with switching users. I have created separate accounts for my children (age (almost)3..8, btw the 3 years old girl totally love tuxpaint..) They have no problem using the 'quit' button and 'log out' to switch user, but since they are used to (from XP) leaving their programs running and just 'switching' every know and then they like to do that in ubuntu as well. But now it gets confusing for the smaller ones, when they press 'quit' and 'switch user' buttons they return to the login window with face browser, then they click on the 'face' and enter their password. Then up pops a window (in english, not localized) with buttons asking for a new login or return to current. Of course they want to return to current but the default choise is 'new login'. And when they press that 'middle' button (return to previous) up pops another window asking for the password AGAIN, also with english speaking button for swithing user, and there they have to press a button named 'Unlock' after entering the password the second time.  And strangely it doesn't always ask for the password two times, but it seems unrelated to the screensaver timeout which is much longer. This is not very easy to understand for a kid and I am simply amazed that they manage to do it, but is there any way to get rid of that 'Unlock' thing which asks for the password again? (yes the 
lock screen' feature of the screensaver is not checked). Also the default should be 'return to previous' and not 'new login'.

---

### Post by Polygon on 2006-07-01
that does it, when i do "new login" if i press "ctrl+alt+f8" it takes me to the black screen that i described before, and if i press ctrl+alt+f7, it takes me back to the face browser. thanks again

---

### Post by Polygon on 2006-07-01
actually this does NOT work.

my above post was just me testing clicking "new login" and then doing it and it seemed to work

but after my computer is idle and the screensaver comes on, for some reason it locks the screen and if i try to switch sessions, it either wont let me or will just take me to a text based terminal.

any other suggestions?

---

### Post by rollps on 2006-07-08
hi,

not going to help with your problem here, sorry :$

but this is related to the "new login" feature...

well, basicaly, I don't have it anymore with Xubuntu 6.06 !
is it like a Gnome only feature ??

if so, what is the name of the package so I can put it on Xubuntu

Thanks for any help

---

