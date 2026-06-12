---
title: "Terminal troubles"
date: 2011-03-09
forum: General Help
---

### Post by pseudosmart on 2011-03-09
I was having trouble extracting some files because the system said I didn't have sufficient permissions, so I started fooling around with my permissions in Users and Groups. But now, when I open a terminal, there's no $, and my username isn't there, it's just a blinking insertion point. And I can't even type anything into the terminal. Does anyone know how I can just reset my default user account permissions? Without using the terminal, since I can't seem to type anything into it? Thanks in advance for your help, I'm very new at using Linux.

---

### Post by watupgroupie on 2011-03-09
This may seem a little dumb, but just try a reboot and see what happens.

---

### Post by Habitual on 2011-03-10
type
```
reset
``` in faith at "blinking insertion point" (it's just 6 keystrokes and it MAY work)

You could always install another terminal...
Let's see if xterm is installed first. Alt+F2 and type in xterm and hit the run button. 

IF xterm does not run, Find the Ubuntu Software Center from the Menu and search for xterm, install it. Then run it with Alt+F2 > xterm > run button.

in xterm, type
```
sudo cp /etc/skel/.bashrc ~/

```
then
```
whoami 
```(note your username)
then
```
sudo chown whoami:whoami ~/.bashrc
```
Changing whoami:whoami for your username:username

Then, barring any further errors, run gnome-terminal using Alt+F2 > gnome-terminal > run button.

Does it look ok now?

Please let us know...

---

### Post by pseudosmart on 2011-03-10
Well, rebooting was the first thing I tried, but no dice. And I'll try typing 'reset' at the blinking insertion point this evening and I'll post whether it works or not. Unfortunately, I don't have access to the command line using CTRL + ALT + F1-F6. I'm not sure why the command line won't display, but I think it may have something to do with some work I had to do to make my display work correctly. I had to remove the nouveau driver to successfully install and use the driver for my nvidia GeForce 330M card. And everything with the display has worked fine now, except for being able to see the command line. Which I didn't really mind (until now of course). In any case, I'll back up all my files and try this reset thing tonight and I'll post what happens. Just out of curiosity, beyond typing reset into the empty terminal (which I'm really hoping works), do I have many other options beyond just backing up my files to my external HD and reinstalling the OS and my nvidia driver all over again? It's not the worst thing the world to have to do, but I'd rather avoid it if I can. Thanks again for your help.

---

### Post by AlphaLexman on 2011-03-10
Also, try typing <**ctrl-c**> at the blinking cursor, you may have an unfinished builtin looking for a closing statement.

---

### Post by pseudosmart on 2011-03-10
Thanks, I'll try CTRL+C as well. I really hope one of these methods works..haha..I'd rather not spend tonight reinstalling everything.

---

### Post by bodhi.zazen on 2011-03-10
You probably need to reinstall as that is often faster then trying to restore ownership and permissions of system files.

You should NOT change ownership or permissions of system files (anything outside of your home directory).

What was your original problem and what made you think changing ownership and permissions of system files would solve anything ?

---

### Post by pseudosmart on 2011-03-10
Yeah, I definitely won't mess with the permissions again, I think I learned that lesson. haha. Like I said, I'm really new at using  Linux, and I was trying to extract some files I downloaded to my desktop, and I kept getting the message that I didn't have the permission to extract to that location. Which confused and frustrated me, so I thought I would just give myself the highest permissions possible, and see if that would work. Made sense to me at the time, but never again.

---

### Post by bodhi.zazen on 2011-03-10
> **pseudosmart said:**
> Yeah, I definitely won't mess with the permissions again, I think I learned that lesson. haha. Like I said, I'm really new at using  Linux, and I was trying to extract some files I downloaded to my desktop, and I kept getting the message that I didn't have the permission to extract to that location. Which confused and frustrated me, so I thought I would just give myself the highest permissions possible, and see if that would work. Made sense to me at the time, but never again.

Since you are new to Linux I highly suggest you learn to manage Linux permissions and how to use (on Ubuntu) sudo.

He who play  with root eventually kill tree

using the root account to circumvent learning permissions is the "root cause" of your problem.

---

### Post by pseudosmart on 2011-03-10
Yeah, at first I thought I had at least a basic grasp on the whole permissions thing, but I obviously didn't. I have used the sudo command a few times, to install stuff with the terminal, like 'sudo apt-get install...', but I can't say I totally understand it other that it gives you temporary permission as a super user, is that right? In any case, I went ahead and backed up all my files during lunch, and I'm just going to do a fresh install this evening to make sure all the permissions are back to what they should be. And maybe this time I'll try blacklisting nouveau this time instead of removing it all together, and maybe that way I won't have problems when I update the system. But thanks for all the suggestions, I really appreciate everybody's help.

---

### Post by bodhi.zazen on 2011-03-10
> **pseudosmart said:**
> Yeah, at first I thought I had at least a basic grasp on the whole permissions thing, but I obviously didn't. I have used the sudo command a few times, to install stuff with the terminal, like 'sudo apt-get install...', but I can't say I totally understand it other that it gives you temporary permission as a super user, is that right? In any case, I went ahead and backed up all my files during lunch, and I'm just going to do a fresh install this evening to make sure all the permissions are back to what they should be. And maybe this time I'll try blacklisting nouveau this time instead of removing it all together, and maybe that way I won't have problems when I update the system. But thanks for all the suggestions, I really appreciate everybody's help.

If you run into a problem, ask for assistance, that is what we are here for.

For sudo see:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

