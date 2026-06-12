---
title: "Cursor cant be changed in ubuntu 10.4 in gnom"
date: 2010-05-27
forum: General Help
---

### Post by demontranoth on 2010-05-27
The tittle pretty much says it all, In Ubuntu 10.4 64 bit which i have installed on a partition next to windows 7, I can not change the cursor. when I click a different cursor nothing happens. I don't think its very hard to fix but i lack the expertize so thank you!

---

### Post by jerrrys on 2010-05-27
try 'crystalcursor' its in synaptic package manager

[ATTACH]158461[/ATTACH]

---

### Post by demontranoth on 2010-05-28
Thanks, Il try that! but do you think it will let me use the other cursors as well (glass red and all of those)?

---

### Post by cottfcfan on 2010-05-28
If your running compiz, theres a bug where only the default cursor shows.
Turn off visual affects and see if you cursor changes then.

---

### Post by demontranoth on 2010-05-28
cotttfcfan, that apears to be the problem but now i can no longer use DMZ white as my mouse with the effects on :(. Is there a way to fix this problem? thanks at the moment the cursor is stuck being crystal blue.

---

### Post by dino99 on 2010-05-28
you might have some errors or/and warning logged: system admin log viewer, and into .xsession-errors (/home, unhide it with menu)

---

### Post by demontranoth on 2010-05-28
I got to the log viewer but dont understand what to do next could you maybe explain further?

---

### Post by auxiliary.chipmunk on 2010-06-13
> **cottfcfan said:**
> If your running compiz, theres a bug where only the default cursor shows.
Turn off visual affects and see if you cursor changes then.
hey thanks this fixed it for me, i turned the effects back on and the mouse cursor is still set to crystal.

It seems to be once you have turned the effects off you can just turn them back on and you will have the cursor of choice and th effect as well 

many thanks

:)

---

### Post by jocam on 2010-09-12
[SIZE=2]Hi there Love my Ubuntu but I do miss my Large Red Glass Cursor as I am sight impared and the red glass cursor helps tremendously ~ I do get the red glass cursor in some applications but not all

Somebody suggested to turn off compiz ~ I am hesitant to do this as I don't know what I will lose ~ we spent a long time getting Ubuntu set up to suit me ~ can someone please tell me what will happen if I do that ~ what will I lose? ~ or ~ will compiz settings be easily restored if I don't like what I see?

Every time I update I look for my Red glass cursor which worked Soo well in previous version

Regards
jocam 
P.S. ~ My Red glass cursor is working on this site
[/SIZE]

---

### Post by smittycity on 2010-12-02
> **jocam said:**
> [SIZE=2]Hi there Love my Ubuntu but I do miss my Large Red Glass Cursor as I am sight impared and the red glass cursor helps tremendously ~ I do get the red glass cursor in some applications but not all

Somebody suggested to turn off compiz ~ I am hesitant to do this as I don't know what I will lose ~ we spent a long time getting Ubuntu set up to suit me ~ can someone please tell me what will happen if I do that ~ what will I lose? ~ or ~ will compiz settings be easily restored if I don't like what I see?

Every time I update I look for my Red glass cursor which worked Soo well in previous version

Regards
jocam 
P.S. ~ My Red glass cursor is working on this site
[/SIZE]


My mother is having the exact same problem, she is also visually impaired. The compiz + redglass theme has worked well for quite a while, now all the sudden it doesn't. It is a known bug, and I am disappointed that it has not yet been fixed.

I tried this:
[http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html](http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html)

However, this only causes them theme to be conserved, the size of the pointer still changes depending on what application you are in.

Most visually impaired people will want to use the compiz magnifier and a big mouse pointer, so this is a bit of a problem any visually impaired person trying to use Ubuntu.

Also, disabling compiz did not work, once you reenable it the cursor problem persists.

---

### Post by cottfcfan on 2010-12-03
If you want your cursor to work there is an easy fix.
1st and obvious make sure the cursor you want is chosen in theme/customize/pointer. Then you need to edit a file:
From a terminal:

sudo gedit /usr/share/icons/default/index.theme

Then change the line Inherits=.... To the name of your cursor theme.
eg mine is Inherits=Azenis-Orange
Make sure the name is exact and it is case sensitive.
After that save the file, close, log out and back in and your cursor theme should stick.

---

### Post by smittycity on 2010-12-03
I have already tried this. My index.theme is Inherits=redglass

Like I said, this makes it so that the redglass theme is used everywhere, when it was not before, however, the size of the pointer is not the same everywhere. For example it is small on the desktop and large in a browser window. 

Is there an option I could append to the theme? Something like Inherits=redglass.large ?

---

### Post by cottfcfan on 2010-12-03
What you need to do is install more cursors.
In synaptic there is a "big-cursor" App.
Install that and see which cursor suits, then follow the above.

---

### Post by smittycity on 2010-12-07
Is the big-cursor app supposed to come with a set of themes or is it supposed to modify existing themes?

I installed it and nothing seemed to change. My index.theme was already inheriting the proper theme.

I apt-get removed all of the x cursor themes after installing big-cursor and upon restarting X there was a big black cursor and only the default cursor theme.

I then reinstalled redglass, checked the index.theme, restart X. Now the redglass cursor is always small.

So rite now I have chosen the go with what was working before, the big black default cursor. 

This in inelegant and not optimal so I would still like to find a better solution.

---

