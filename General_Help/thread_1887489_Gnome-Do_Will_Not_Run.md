---
title: "Gnome-Do Will Not Run"
date: 2011-11-27
forum: General Help
---

### Post by RobMagus on 2011-11-27
I have just upgraded my netbook from 11.04 to 11.10, and find that gnome-do will not run.

I have purged gnome-do & gnome-do-plugins and reinstalled, and this issue still occurs:

If I attempt to start it in the terminal by typing gnome-do, nothing happens. It appears to just hang - the terminal does not give another prompt; it's as if the program is running but giving no indication that it's doing anything. I have to exit with ctrl+C. Leaving that running and then trying to invoke gnome-do (with my normal key-combination before reinstall) didn't start it up, and it should come up on its own on first run after a fresh install.

Gnome-do --debug does nothing as well, the same hang occurs.

When I start it using the launcher (and again nothing happens), I can open up a terminal and run top: I find a process called cli that is eating 90+ of my CPU. It appears to be something started by mono (based on reading the man page for cli). Killing it works fine, but then I'm back where I started.

Please help! I need my gnome-do shortcuts!

- r

---

### Post by BC59 on 2011-11-27
Did you run 

```
sudo dpkg --configure -a
sudo apt-get -f install
```

To ensure all necessary packages are completely installed and configured?

---

### Post by RobMagus on 2011-11-27
I purged it again, changed my repositories to the official ubuntu archive, updated, and reinstalled gnome-do (which installed a punch of mono libraries along with it).

I've just ran sudo dpkg --configure -a, and sudo apt-get -f install, as you suggested. EDIT: Neither of them gave any output other than to say nothing was broken & nothing was fixed.

Alas, the same issue occurs. I try to run gnome-do and get nothing but a cli process from mono that eats 99% of my cpu.

:(

---

### Post by BC59 on 2011-11-27
Well then try through Synaptic to see if you can install the gnome-do dependencies manually.

Open synaptic and finding Gnome-do, right click and go to properties to see the dependencies. Check one by one if it's installed.

Mine looks like this:

---

### Post by BC59 on 2011-11-27
Well googling I found that for gnome-do to work, sometimes is needed to open another application before.

So try to install Epiphany web browser.

Another solution I found here:
[http://anonir.wordpress.com/2010/02/05/gnome-do-startup-problem/](http://anonir.wordpress.com/2010/02/05/gnome-do-startup-problem/)

---

### Post by RobMagus on 2011-11-27
Reinstalled each dependency manually.

Same thing - nothing happens, and I get a process called cli that just uses up cpu.

Does gnome-do not run in unity? Am I missing something that simple?

EDIT: Installed epiphany, tried running gnome-do, same thing. Why would isntalling epiphany in particular help?

Created and ran the shell script, same issue.

*tears out hair*

---

### Post by BC59 on 2011-11-27
You have right, under Unity needs special installation:

[http://www.techrepublic.com/blog/opensource/install-and-configure-gnome-do-in-ubuntu-unity/2535](http://www.techrepublic.com/blog/opensource/install-and-configure-gnome-do-in-ubuntu-unity/2535)

---

### Post by RobMagus on 2011-11-27
The instructions in that link are for binding gnome-do to a different launcher key combo, using its configuration menu once you've managed to run the program and its gui appears.

My issue is that I can't even get the program to open - no gui appears and thus I can't configure anything.

---

### Post by BC59 on 2011-11-27
Well I searched to the existing bugs and I found this

gnome-do don't start with username > 9 characters

[https://bugs.launchpad.net/do/+bug/439949](https://bugs.launchpad.net/do/+bug/439949)

I don't know if someone of the members knows something more, I'm out of ideas.

---

### Post by BC59 on 2011-11-27
Actually here looks they found a solution:

[http://flax.ie/gnome-do-ubuntu-10-04-crashes-on-login/](http://flax.ie/gnome-do-ubuntu-10-04-crashes-on-login/)

---

