---
title: "Ubuntu freezes after login.(pink screen)"
date: 2010-03-06
forum: General Help
---

### Post by -spy on 2010-03-06
So it was running fine until I decide to change a theme (GTK 2.) and it freezes, I wait a while and nothing happens, so I did a hard shutdown. Now after I boot up and login, it just sits at the pink screen, I can see the mouse pointer and move it but thats all, eventually a white square will appear in the right corner, my computer also gets really hot during this. This happens in recovery mode also.

I searched online and did this 'soultion' but it didn't work ( [http://benaiah41.wordpress.com/2008/11/01/ubuntu-810-freezes-after-login-screen/](http://benaiah41.wordpress.com/2008/11/01/ubuntu-810-freezes-after-login-screen/) )

I'm a ubuntu noob so I dont know too much yet.

Unfortunately my windows os also just died today, so I'm stuck using the libraries mac.

---

### Post by flippo on 2010-03-06
Can you log in though a tty terminal?

If you don't know try this:
turn on PC, at login screen
push ctrl+alt+f1
log in
if it works, then you can
push ctrl+alt+f7 to get back to graphical login screen

---

### Post by -spy on 2010-03-06
> **flippo said:**
> Can you log in though a tty terminal?

If you don't know try this:
turn on PC, at login screen
push ctrl+alt+f1
log in
if it works, then you can
push ctrl+alt+f7 to get back to graphical login screen

What do I do when I log into the terminal?

---

### Post by flippo on 2010-03-06
It will prompt you for your username and password, type them in.  If it logs you in successfully (you can do a command, like "ls") then you can log in though tty1, otherwise you cant.

---

### Post by -spy on 2010-03-06
> **flippo said:**
> Can you log in though a tty terminal?

If you don't know try this:
turn on PC, at login screen
push ctrl+alt+f1
log in
if it works, then you can
push ctrl+alt+f7 to get back to graphical login screen

Ok, I did this, pressed control alt F1 at the login, but then the screen messes up, I cant see anything. 

Any other options?

---

### Post by flippo on 2010-03-06
Ugh, I think that means the default framebuffer for the terminal is not compatible with your card...

You need to have your system boot using a software framebuffer (uvesafb <I think>) that is compatible with pretty much every set of hardware.  Then you can get to tty1 and have it work.  You can specify this with a kernel parameter at boot time (you have to edit grub).  I sadly am not experienced enough with this to walk you though it remotely.  Hopefully someone else can give some advice on that.

Alternatively you can try logging in on recovery mode, see if things work in that.

---

### Post by -spy on 2010-03-06
> **flippo said:**
> Ugh, I think that means the default framebuffer for the terminal is not compatible with your card...

You need to have your system boot using a software framebuffer (uvesafb <I think>) that is compatible with pretty much every set of hardware.  Then you can get to tty1 and have it work.  You can specify this with a kernel parameter at boot time (you have to edit grub).  I sadly am not experienced enough with this to walk you though it remotely.  Hopefully someone else can give some advice on that.

**Alternatively you can try logging in on recovery mode, see if things work in that.**

I tried recovery mode, where I did all the stps from the link in my op, that didn't work. I really have no idea what I'm doing though..

---

### Post by flippo on 2010-03-06
ahhh, well if we can get to a shell we are still in business.  If you dont mind loosing all your custom gui settings (keyboard shortcuts, wallpapers, set themes, etc) you can just delete (or even better rename) all of those folders, and for 9/10 ppl that will solve the issue.

```
mv /home/<username>/<folder> /home/<username>/<folder>_backup
```

replace <username> with your username and <folder> with the following folders (each one individually):

.gconf .gconfd .gnome .gnome2 .gnome2_prvate .compiz .emerald .icons .nautilus .themes 

NOTE: you most likely don't have to move all of these, and you may even not have all of these, but they are the folders where your user configuration is stored, and its most likely messed up somewhere, causing this problem.  If you get rid of the configuration gnome will just restore a default and your back in business.

A check to be sure this method will work before you log in is the following:

Make a new user (from recovery terminal)```
sudo useradd <newusername>
sudo passwd <newusername>
```

reboot and try to log in as your new user, if it works fine then this fix *should* work for you.

If you really care about your gnome customization and really don't want to go though all the work of getting it back we can work on that too, but it will be a huge headache.

---

### Post by -spy on 2010-03-06
> **flippo said:**
> ahhh, well if we can get to a shell we are still in business.  If you dont mind loosing all your custom gui settings (keyboard shortcuts, wallpapers, set themes, etc) you can just delete (or even better rename) all of those folders, and for 9/10 ppl that will solve the issue.

```
mv /home/<username>/<folder> /home/<username>/<folder>_backup
```

replace <username> with your username and <folder> with the following folders (each one individually):

.gconf .gconfd .gnome .gnome2 .gnome2_prvate .compiz .emerald .icons .nautilus .themes 

NOTE: you most likely don't have to move all of these, and you may even not have all of these, but they are the folders where your user configuration is stored, and its most likely messed up somewhere, causing this problem.  If you get rid of the configuration gnome will just restore a default and your back in business.

A check to be sure this method will work before you log in is the following:

Make a new user (from recovery terminal)```
sudo useradd <newusername>
sudo passwd <newusername>
```

reboot and try to log in as your new user, if it works fine then this fix *should* work for you.

If you really care about your gnome customization and really don't want to go though all the work of getting it back we can work on that too, but it will be a huge headache.

ok so i do all this from the recovery mode screen (black and white screen)?

---

### Post by flippo on 2010-03-06
Yep, unless you want to verify the method will work before you try it, in which case the part I say "reboot and log in as your new user" should be done from the graphical one

---

### Post by -spy on 2010-03-06
Thanks, that worked great, everything is back to default as far as the gui.

---

### Post by flippo on 2010-03-06
Great, glad to hear your running again.

Please mark the thread as solved.

---

### Post by Shamlou on 2010-05-03
Hi.
I've been searching up and down for a solution to my problem, and I think this was the closest I got to finding a solution... but alas, they didn't work for me :(

My problem is this:
I had ubuntu running perfectly fine, until I decided to install the mac4lin theme. I got to the part in the mac4lin installation instructions ([http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)). At the point where it instructs you to logout and login again to get the Global Menu Applet to show up on your top panel, I can't logout, it does something, but it doesn't log me out ... I tried a few times, but to no avail. Then I tried rebooting.

It did reboot, but when it's time for it to show splash screen, I only see black. Nothing I press on the keyboard does anything. The mouse works. I CAN get into the tty1, etc... but I don't know where to go from there.

I did the things suggested earlier in this post, but nothing different happens.

Please help!

---

