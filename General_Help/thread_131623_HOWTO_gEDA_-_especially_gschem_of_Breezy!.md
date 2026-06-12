---
title: "HOWTO: gEDA - especially gschem of Breezy!"
date: 2006-02-16
forum: General Help
---

### Post by daller on 2006-02-16
Hi There,

This is a CRAPPY way to make gschem (and a lot of other electronical apps working) - but it DOES work!

Here we go:

-----

To install: geda, pcb, ngspice, gnucap, gerbv, gtkwave, wcalc

Download and burn this ISO:
	[http://geda.seul.org/dist/suite/20060124/geda-install-20060124.iso](http://geda.seul.org/dist/suite/20060124/geda-install-20060124.iso)

Copy the content of the cd to a folder on the harddrive! (At least I didn't have any luck running it of the cd!)

Install these packages: (I think that's all you'll need)

	build-essential
	libreadline5-dev
	guile-1.6
	libwxgtk2.6-dev
	libgtkmm-2.4-dev
	libxaw7-dev
	gperf

Go to the directory you copied the files to, and run:

	sudo sh installer

...The rest is GUI - should be self-explanatory!

After installation, the binaries can be found here:

/home/<USER>/geda-install/bin (Would it be safe to select "/usr/bin" as installation directory?)

...Enjoy!!!

---

### Post by daller on 2006-02-16
Or the easy way...

Try to download the gschem binary from my computer:

[http://dumazz.dk/gschem](http://dumazz.dk/gschem)

...and put it in your /usr/bin

(It worked on my girlfriends laptop!)

Tell me about your experience!

---

### Post by egghead3 on 2006-02-17
I attempted to build from source as you described in your first post and am having an error, perhaps permissions related? I know very little about building from source...

Here is the error from the log file....

```
make open
make: *** No rule to make target `open'.  Stop.



==============  Error!  ======================
Failure executing command "make open", ReturnCode = 2
```

---

### Post by daller on 2006-02-18
[QUOTE=egghead3]I attempted to build from source as you described in your first post and am having an error, perhaps permissions related? I know very little about building from source...

Here is the error from the log file....

```
make open
make: *** No rule to make target `open'.  Stop.



==============  Error!  ======================
Failure executing command "make open", ReturnCode = 2
```[/QUOTE]

Where in the process does this happen? (While running "sudo sh installer"???)

---

### Post by egghead3 on 2006-02-18
Yes, it happens while running the installer script immediately after giving me the message that I should go take a long coffee break (so apparently right when it tries to start the actual compilation). The file copying at the very beginning, where it sets up the geda-install and geda-source directories appears to work fine (no errors).

edit: I just noticed this thread was in the KDE forum (I found it on a global search for geda). I am running gnome. Could this be part of the problem? Should I install KDE libraries or could you try to do this in a gnome envoronment?

Thanks for the help

---

### Post by bebop_tango on 2006-11-23
I installed gEDA Suite from the ISO - you don't have to copy the whole thing to your hard drive, but to mount it in another folder:

mount -o exec -t iso9660 /dev/cdrom /mnt/cdrom

Aside from the packages daller mentioned, in order to compile the whole thing I think you'll also need:

bison
m4
flex
libstroke0 
libstroke0-dev
libpango1.0-dev
tcl8.4
tcl8.4-dev

I think both g++ and g77 should be pre-installed, but I'm not sure if they're required.

The installer program asks you if it should install some required packages, such as guile and wxGTK, but I strongly recommend you to install those via apt-get or synaptic - you could have some conflicts going on latter, I couldn't start wxMaxima after the gEDA installation, so I had to install the wxGTK package from the repositories in order to get it working again.

Anyway, we should keep a list of the known required packages to install gEDA from the CD. It's the best way to do it, albeit a bit labourous.

---

