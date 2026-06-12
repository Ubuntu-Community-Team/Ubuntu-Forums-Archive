---
title: "password rejected after ScreenLock !!"
date: 2006-05-04
forum: General Help
---

### Post by mooha on 2006-05-04
Hi all,

When My screen get locked, I try to unlock it, it reject my password, Any help please.


Thanks

---

### Post by deadgobby on 2006-05-04
[QUOTE=mooha]Hi all,

When My screen get locked, I try to unlock it, it reject my password, Any help please.


Thanks[/QUOTE]

Can you please go into futher detail on the screen getting locked up? Was it the log in screen? Did Ubie lock up and ask you for a pass word? Did Ubie boot all the way into the log in screen and you tried to type in your user name and pass word over and over agian? Some info would be helpful. 
Thanks
Gobby

---

### Post by Mustard on 2006-05-04
I think he is talking about the screenlock that you can set manually, or have activated by the screensaver settings, which blanks the screen when you walk away.

The only thing I can think of is that you might be entering the wrong password.

---

### Post by deadgobby on 2006-05-04
I did not think of that.

---

### Post by mooha on 2006-05-04
Thanks for the reply,

I am talking about the normal Screensaver Lock option, everything works normal, except when you wanna resum working ( try to go back to desktop ) ofcorse it will Ask you for Password, when I type it it will hangs for a second and then I see DENNIED big in red, NO I didnt typed the wrong password !! I am sure of that.

Please any help is appreciated

Many thanks

---

### Post by elamericano on 2006-05-04
To be really sure of that, you can click "Switch User" and type it into the login box there, in order to see it. That should expose if there is a keyboard problem.

Unfortunately, if you logon there it wants to create a new session. If you say resume, it will bounce you back to the lock screen.

Give it a try and report your results.

---

### Post by mooha on 2006-05-04
My problem is why the screenlock dennied my password? 

So the only way I can resume my work in this machine is to reboot the PC.

I can do Crtl+Alt+F6 and log on with the same password that was refused by Screensaver, and reboot.

Please help

---

### Post by elamericano on 2006-05-04
I'm sorry, I couldn't tell if you tried my switch user suggestion. I understand that you are typing your password correctly, but I wanted to see what letters you're getting. Maybe your keyboard map is wrong at that moment.

A terminal session might not be the same situation.

---

### Post by nanotube on 2006-05-04
hey
well, i am not exactly sure why your password is denied. maybe you have more than one keymap assigned? for example, i have us dvorak and us qwerty, and use dvorak myself - but sometimes in the login screen it starts denying my password, and i say aha, maybe it switched to qwerty accidentally - and swictch it back (default key combo is to press two alt's at the same time), and then it works.

but another thing - when you go ctl-alt-f6, and switch to another terminal and log in - instead of rebooting, try finding and killing the xscreensaver process. that should unlock your screen, i would think. save yourself a reboot. :)

---

### Post by Engnome on 2006-05-04
No one mentioned caps lock so I though i might aswell... probably not that though as its pretty obviously states if you got caps on. (In dapper it does, not sure about breezy)

---

### Post by elamericano on 2006-05-04
Exactly my point. If you type it into a field that echos the characters, you can see what's going on.

As for Alt-Alt, that switched to my 'Esp' keyboard setting, but doing it again has no effect. Do you know the keys to switch keymaps in the other direction?

---

### Post by elamericano on 2006-05-04
Ooh, looks like a bug (my first bug). When I enable shift-shift or ctrl-ctrl as the switching combination it switches back and forth, but with alt-alt, which is the one enabled by default, it goes to the Esp setting and stays there.

---

### Post by mooha on 2006-05-04
I have appsolutly no other Keyboard other than the QWERTY US keyboard installed on my system, I checked that too and confirmed about the CAPS, but any way I changed the user password to a very simple password easy one with only one latter that repeats many times, it didn't work too, if I click on Switch User I can access to another Login but I dont go back to the Locked one (  I Mean couldn't Unlock it ).

---

### Post by Mustard on 2006-05-04
I have some feint recollection of this problem occuring in another thread a long time ago.  You might try doing a search and see if you can find anyone else who had the same problem.

-edit-

I'm doing some searches myself atm.  I've found this thread which is at least showing that you are not alone...
[http://www.ubuntuforums.org/showthread.php?t=144148](http://www.ubuntuforums.org/showthread.php?t=144148)

Can I ask what method you are using to set the password btw?  Are you using the graphical user interface in System>Administration>Users and Groups or are you using the command line with a sudo passwd command?

---

### Post by mooha on 2006-05-06
I thank Everyone for helping me on this problem,

What I did is  sudo passwd , changed password by terminal, and I also uninstalled the  Kuser. and it worked fine.

once again I appreciate everyone's help

Thank you

---

