---
title: "Help..Terminal On Startup"
date: 2010-01-17
forum: General Help
---

### Post by soryu on 2010-01-17
I Unistalled  Thunderbird And Evolution.  Now When I Startup Karmic . I Get
 Startup Screen,Grub Menu,Splash Screen  And Instead Of Going To the  DEsktop Screen i get A Terminal Command Screen.
What command do i use to get my pc to start up normally?

---

### Post by ubudog on 2010-01-17
> **soryu said:**
> I Unistalled  Thunderbird And Evolution.  Now When I Startup Karmic . I Get
 Startup Screen,Grub Menu,Splash Screen  And Instead Of Going To the  DEsktop Screen i get A Terminal Command Screen.
What command do i use to get my pc to start up normally?

At the terminal type ```
startx
```, then once you have logged in, open a terminal, Applications>Accessories>Terminal, and type```
gksu gedit /etc/rc.local
```, enter your password, then at the end of all that stuff, just above the "exit 0" add a line that says "/usr/bin/startx/" without the quotes. Then reboot and all should be good.  Hope that helps. ;)

---

### Post by soryu on 2010-01-17
i got :user not authorized to run xserver. aborting??
 
 i tried sudo startx and got server is already active.

---

### Post by soryu on 2010-01-17
i added the line above exit 0. same problem [EMAIL="linux@linux-desktop:$"]linux@linux-desktop:$[/EMAIL] on start up.

---

### Post by ubudog on 2010-01-17
If the server is already active, then try hitting CTL ALT F7

---

### Post by soryu on 2010-01-17
nothing happens?
 
the command screen is on the upper left part of the desktop when i move the cursor out of the screen  the pointer changes from arrow to loading? (spinning circle)

---

### Post by ubudog on 2010-01-17
Press ALT F2 and type killall gnome-terminal

---

### Post by soryu on 2010-01-17
no process found

---

### Post by ubudog on 2010-01-17
Ok, so this is what is happening: You are able to login and see your desktop, but there is a terminal window at the top of the screen?

---

### Post by soryu on 2010-01-17
right except, i can't see my desktop  the screen is all black except for the terminal. if i type exit in the terminal window it sends me to the login screen. i log in and  the terminal  pops out it's not the regular terminal window. you know applications>terminal.
this one looks like a boot screen.

---

### Post by ubudog on 2010-01-17
> **soryu said:**
> right except, i can't see my desktop  the screen is all black except for the terminal. if i type exit in the terminal window it sends me to the login screen. i log in and  the terminal  pops out it's not the regular terminal window. you know applications>terminal.
this one looks like a boot screen.

Ah, I see.  I don't know of anything to do except reinstall.  Sorry. :(

---

### Post by soryu on 2010-01-17
is there anyway i can save some of the data in the pc?. pics,music.

---

### Post by ubudog on 2010-01-17
> **soryu said:**
> is there anyway i can save some of the data in the pc?. pics,music.

Yeah sure.  If you have a flash drive or other removable media, plug it in, and then copy all the stuff you want, like home directory, etc. with cp /file/ /media/device/  Then unmount it with umount /media/device/.  Reinstall Ubuntu, and all should work.  Then you can just use the file manager to copy all your stuff back over.  If you need any help, just PM me.

---

### Post by john newbuntu on 2010-01-17
When you login, hit Ctrl+Alt+F2.  You should get a virtual terminal.  Login and run:
sudo service gdm stop

Then run:
sudo apt-get install ubuntu-desktop

---

