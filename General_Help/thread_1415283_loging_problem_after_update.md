---
title: "loging problem after update"
date: 2010-02-24
forum: General Help
---

### Post by caslor on 2010-02-24
Hi
i install xubuntu 9.10  and after i finish it i start the update manager..
I had to update/install  183 packages.. and so i let it  do it....
after finishing all this packages  the tool bar  to the top  vanished !!

i decide to continue with the installation of 3-4 programs i wanted.
so i run  synaptic package manager  and install  openoffice,vlc,moovida,amsn,gedit

and when all finished and installed i restart my system.

Notice that i had choose not asking me for password at the begging  and all restartings until know where ok.


The system now starts... shows xubuntu splash  screen...  open and close 1-2 times.. and then closes again .. and now open a screen  thas asks me with what user want to login and give password
i type password and after while  again the same screen  asking me to choose user and place password..

what happend??? grrrrrrrrr
any solutions?

---

### Post by BrandonBan6 on 2010-02-24
I had a similar episode... when you boot up your computer, you will see the BIOS splash screen and then before the xubuntu splash screen you will see "grub loading", hit escape, go into to a root shell

type:
```
passwd username
```
type a new password at the prompt
then type: shutdown -r now

Will it let you log on now?

---

### Post by caslor on 2010-02-24
ok i will try it and will tell you the results.. thanks my friend :)

---

### Post by Wlo on 2010-02-24
Same thing just happened to me.  I'm not on Xubuntu though, just standard Gnome.

I can still log in via SSH, so I've done so and changed my password, which was fine, but back on my desktop when I try to login the same thing happens - it goes away for a second, refreshes, and then presents the same screen to me again.

This is the second time in a couple of weeks that I've installed an updated which has broken my system.  I'm not knocking the usually excellent work which Canonical and the Debian developers do, but let's face it, it's a massive frustration (to put it politely) that I now can't use my system.  For all it's faults this never happened with Windows.

Can anyone help?

---

### Post by caslor on 2010-02-24
ok i try it but was difficult to go  into to a root shell
BUt if i hit all the time ''esc''  i can go directly to main window :P :P  and i am login ..

i saw tha the tool bar still missing from the desktop :(

i restart it and again have the same problem with login  (but now i know how to avoid this.. hit esc all the time)

can i write these command lines you said   from a shell as i am login ?

 about missing tool bar anyone?


(if we knew what package messing that.. it will be interesting in order to avoid it next time we want to update )

---

### Post by caslor on 2010-02-25
Ok today i isntalled xubuntu 8.04 but because i didnt like it.. i install again!! xubuntu 9.10

I find out what was wrong with the boot when asked me for user and password even i had select not to do that..

This system is in my car.. convertible beetle  with celeron as cpu   and   7'' touchscreen...
monitor was the problem... the xubuntu had as default 800x600 resolution and when i change today (i have done that and last time)  to 640x480   after  restart i had the same problem..  :P :P


the solution was to change again the resolution of the monitor to the default  800x600

---

### Post by azertyh on 2010-02-25
hi,
this bug is already on launchpad. there are many threads about it on the forum.
the solutions are :
  	 	 	 	 	 	  [http://ubuntuforums.org/showthread.php?t=1340208](http://ubuntuforums.org/showthread.php?t=1340208)
 or open a terminal on gdm screen and type    	 	 	 	 	 	  *sudo mv /usr/bin/xsplash /usr/bin/xsplash.disabled *

---

### Post by caslor on 2010-02-25
thanks my friend ;)

i find out that when restart...if you press a lot of times the  esc   while it tries to connect then for some reason pass alla the splash screens  and after while you are in desktop ;)

thats how i manage to change the resolution to the default

---

