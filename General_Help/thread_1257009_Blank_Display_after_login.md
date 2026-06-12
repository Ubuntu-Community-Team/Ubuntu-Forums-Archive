---
title: "Blank Display after login"
date: 2009-09-03
forum: General Help
---

### Post by DrRaven on 2009-09-03
Hi everyone,

I am fairly new to Linux..so please be gentle :)..

Ive  installed ubuntu 9.04 on my Toshiba A100 laptop with 1GB RAM. The installation seemed to go smoothly...I started the computer and received the login screen. However, after I type the username and the password, the screen go blank. I am able to move the mouse courser, but nothing else appear on the screen.

Im guessing it has something to do the the video driver....but being fairly inexperienced with Linux...Im not so sure what to do. 

Ideas?? Help?? :confused:

TIA...

Raven

---

### Post by P4man on 2009-09-03
if you can see and move the mousepointer, then it seems your screen is initialized, and therefore Im not so sure its a driver thing (you woulnd't need one anyway to get a desktop).

can you press control+alt+F1 to get to a terminal screen?

---

### Post by DrRaven on 2009-09-03
Hi,

> **P4man said:**
> can you press control+alt+F1 to get to a terminal screen?

Yes. I can get to all the other terminal screens as well...Just not sure how to correct the problem.

Raven

---

### Post by P4man on 2009-09-03
well, me neither :)

This was the first boot after the installation right?
If a terminal doesn't scare you too much (and considering you are aware there are several, Im guessing you're not entirely new to linux ;) ), try this:

```
sudo /etc/init.d/gdm stop
```

to stop X

Then start it again and see if you get any meaningful output or errors:

```
startx
```

---

### Post by DrRaven on 2009-09-03
This isnt the first boot after installation because I have been playing around a bit to try and get it to work...no luck thou.

I might try a reinstall and see what happens...though I am sure the problem will likely reoccur. Im a little directionless in terms of what to do....I used to installing Windows....but really want to give Linux a go.

Raven

---

### Post by P4man on 2009-09-03
dont start reinstalling so quickly.
lets try something else. Boot in to recovery mode (in grub menu), select a root shell. Then do

```
mv /home/user /home/user.bak
mkdir /home/user
chown user:user /home/user

```

replace user with your username. This will rename your homefolder, and make a fresh one, thereby resetting most user related settings. You can later recover anything you'd need from the user.bak folder.

---

### Post by Valino on 2009-09-03
I have encountered similar problem. I used this command:

```
sudo dpkg --force all --configure -a
```

---

### Post by davetrainer on 2009-09-03
I was just about to start my own thread when I saw this. I'm having the same exact problem on the Dell Vostro A9 with NBR. It started when the NBR desktop started misbehaving so I switched to the regular Ubuntu desktop. I restarted and suddenly there it was with no window manager and no panel.

Here is how I get back to normal whenever I start up. Right click the desktop, and click Create Launcher. Name it whatever, and in the Command field type gnome-terminal. Click ok and now double click the launcher to open a Terminal window, and enter

```
gnome-wm & gnome-panel &
```

This restores the normal Ubuntu desktop, at least for me. My questions now are, why, and how do I get this working properly again?

A sidebar question: After using Ctrl-Alt-F1 to switch to a terminal, how do I return to my GNOME desktop?

In the meantime I am going to try the package reconfig that someone suggested earlier.

---

### Post by Jazzy_Jeff on 2009-09-03
> **P4man said:**
> well, me neither :)

This was the first boot after the installation right?
If a terminal doesn't scare you too much (and considering you are aware there are several, Im guessing you're not entirely new to linux ;) ), try this:

```
sudo /etc/init.d/gdm stop
```

to stop X

Then start it again and see if you get any meaningful output or errors:

```
startx
```

I am also having the same problem. When I follow this I get a message  xauth: timeout in locking authority file /home/jeff/.Xauthority

---

### Post by P4man on 2009-09-03
> A sidebar question: After using Ctrl-Alt-F1 to switch to a terminal, how do I return to my GNOME desktop?


control alt F7 gives you X again.
F1 to F6 are all different terminals 

as for your actual problem.. try this:

```
sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session
```

---

### Post by DrRaven on 2009-09-03
OK.....Well its bedtime here in Australia....

Im going to do a fresh install tomorrow...and then try these suggestions...I'll report on the progress....

In the meantime...more suggestions would be awesome :)

Raven :D

---

### Post by P4man on 2009-09-03
> **Jazzy_Jeff said:**
> I am also having the same problem. When I follow this I get a message  xauth: timeout in locking authority file /home/jeff/.Xauthority

try this:
```
sudo chmod 600 /home/jeff/.Xauthority
```

---

### Post by davetrainer on 2009-09-03
> **P4man said:**
> control alt F7 gives you X again.

Cool, thanks.

> **P4man said:**
> as for your actual problem.. try this:

Tried it and restarted; no dice.

---

### Post by Jazzy_Jeff on 2009-09-03
Do you know if your home directory is encrypted? And have you changed your password lately? 

I was having the same problem as you. I changed my main password the other day and just rebooted this morning and could not get back in. I found that my home directory was encrypted and needed my original password. So at the command line I typed passwd and changed my password back to my original password and everything works fine now.

---

