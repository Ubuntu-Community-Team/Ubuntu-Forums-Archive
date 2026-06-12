---
title: "How to compile Gaim Beta2...?"
date: 2006-02-15
forum: General Help
---

### Post by MellonCollie on 2006-02-15
[COLOR="SeaGreen"]**Edit: I found a .deb for beta2 so this isn't urgent.**[/COLOR]


Hi!

I followed the instructions for compiling Gaim on [this](https://wiki.ubuntu.com/CompileGaim) page, but something's going wrong and I can't work out what the problem is.

Everything *seems* to go ok during the './configure' and 'make' stages, but everything goes wonky after 'checkinstall -D make install'.


> 
========================= Installation results ===========================

Copying documentation directory...
Making install in doc
make[1]: Entering directory `/home/jmc777/Programs/gaim-2.0.0beta2/doc'
make[2]: Entering directory `/home/jmc777/Programs/gaim-2.0.0beta2/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: cannot create directory `/usr/local/man': File exists
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/jmc777/Programs/gaim-2.0.0beta2/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/jmc777/Programs/gaim-2.0.0beta2/doc'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.



Is there a kind soul out there who has the patience to take my hand and show me how to go about getting Beta2 installed?

---

### Post by beartard on 2006-02-15
Out of curiosity, did you sudo before checkinstall?

---

### Post by MellonCollie on 2006-02-15
I did beartard, yes. :confused: 


Here's the full output from the terminal window for anyone that's interested: [gaim.txt]("http://jmc7.pwp.blueyonder.co.uk/Files/gaim.txt")

---

### Post by beartard on 2006-02-16
ok.  it looks like everything in "make" was successful.  So something is not right between "make" and "make install."  Did you tell checkinstall to make the doc part?  Seems like that's where it's failing.  Could be a matter of switching n/y at that prompt.

I noticed, too, that when I compiled Gaim beta2, I had to be really specific in the "configure" step in order to keep the new install from overwriting my "stable" Gaim installed through synaptic.  It couldn't hurt to check the configuration options as to where things get installed and make sure checkinstall isn't getting cockblocked by apt-get at the "make install" step.

---

