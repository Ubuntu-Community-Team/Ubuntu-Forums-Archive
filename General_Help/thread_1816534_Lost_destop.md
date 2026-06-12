---
title: "Lost destop"
date: 2011-08-02
forum: General Help
---

### Post by aussie.ian on 2011-08-02
I downloaded the nvidia package so I could customize my graphics card and monitors. Followed the instructions  ```
nvidia-xconfig
``` restarted X and now for some reason am stuck with [http://www.box.net/shared/0buvgc6smpl1ps4bcbq0]("http://www.box.net/shared/0buvgc6smpl1ps4bcbq0") I now have only one monitor working and what seems to be the libra office destop.. I would like the original Gnome destop back.
I tried logging out to select an alternate destop manager to log in to but there are no options available.

---

### Post by Jouke S on 2011-08-02
Can you open a terminal? Try searching in nautilus if you can't access it normally 
now type 'gnome-panel'.
Do the panels appear?

---

### Post by aussie.ian on 2011-08-02
> Can you open a terminal? Try searching in nautilus if you can't access it normally
now type 'gnome-panel'.
Do the panels appear? 

This is what I get
[http://www.box.net/shared/ft9lbzd3f6btiohl15b0]("http://www.box.net/shared/ft9lbzd3f6btiohl15b0")  It is saying it can't connect to the session manager. Although the Gnome-panel does come up (along with the other) as soon as I close the terminal it disappears

I believe what I have here (from reading an article in linux magazine) is something called the untiy destop. Sorry don't like it and want traditional Gnome back..

---

### Post by aussie.ian on 2011-08-02
> **aussie.ian said:**
> This is what I get
[http://www.box.net/shared/ft9lbzd3f6btiohl15b0]("http://www.box.net/shared/ft9lbzd3f6btiohl15b0")  It is saying it can't connect to the session manager. Although the Gnome-panel does come up (along with the other) as soon as I close the terminal it disappears

I believe what I have here (from reading an article in linux magazine) is something called the untiy destop. Sorry don't like it and want traditional Gnome back..
Sorry to have to bump this but I really need help getting my desktop working. How do I get A stable shell working.. Right now i have the Unity thing spread across 2 monitors but neither is responsive as it is just a mess.
Half of monitor 1 is on monitor 0, the unity bar (on the left of screen) is actually in the middle of monitor 0. I click drag monitor 1 and a red square appears in the left of monitor 0.
I hope that makes sense to someone, I can't do a screen shot as nothing works..

---

### Post by JC Cheloven on 2011-08-02
If I understand correctly, what happened is:
- first you hadn't the nvidia driver, so the system boots in "classic" mode.
- then you installed the drivers, the system realized unity was possible and started it.

To go back to classic, reboot and do this: 
- click in your username, but don't enter your psswd (yet)
- at the bottom, some session options do appear.
- choose "classic" from the drop menu
- proceed to type in your password 

That should be it ;)

---

### Post by aussie.ian on 2011-08-02
Thanks JC, you pretty much got what's happening.. Problem is, I have auto login active (logs in with no password). I need to stop the auto login process and somehow get to the login. Once the system boots both monitors are unresponsive. The only way I can restart is by hard reboot.
Booting to safe mode is possible and usable (with Gnome shell) but I have been unable to change any settings in the normal user boot.

---

### Post by aussie.ian on 2011-08-03
> **aussie.ian said:**
> Thanks JC, you pretty much got what's happening.. Problem is, I have auto login active (logs in with no password). I need to stop the auto login process and somehow get to the login. Once the system boots both monitors are unresponsive. The only way I can restart is by hard reboot.
Booting to safe mode is possible and usable (with Gnome shell) but I have been unable to change any settings in the normal user boot.
I've done a little investigating. I managed to login and switch to "Ubuntu Classic (no extras)", everything works fine. If I login with just "Ubuntu Classic" it tries to start "Unity" and the problem arises. It seems Unity can't handle dual monitors and just messes the whole thing up. If I disable my 2nd monitor and start "Ubuntu Classic" Unity comes up and works as it should (I presume, never used it)

---

### Post by JC Cheloven on 2011-08-04
> **aussie.ian said:**
> I've done a little investigating. I managed to login and switch to "Ubuntu Classic (no extras)", everything works fine. If I login with just "Ubuntu Classic" it tries to start "Unity" and the problem arises. It seems Unity can't handle dual monitors and just messes the whole thing up. If I disable my 2nd monitor and start "Ubuntu Classic" Unity comes up and works as it should (I presume, never used it)
So you basically have now a way of getting some work done, congrats :)

Only, choosing "Ubuntu Classic" shouldn't try to start unity. This leads to think that the problem is more with compiz than otherwise. I'm not using unity myself ATM (in fact I'm on lxde: no gnome, no compiz...), so I'm afraid I can't dig deeper into the problem. Will come back if a clever idea arises though.

---

