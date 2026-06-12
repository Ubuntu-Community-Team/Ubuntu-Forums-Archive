---
title: "How do I install Quanta?"
date: 2011-10-26
forum: General Help
---

### Post by oldtimer7777 on 2011-10-26
I had a really quick question. Quanta doesn't seem to be available in the Ubuntu repositories anymore. It was in 11.04, but isn't available anymore in 11.10.  :confused:

How do install Quanta step by step in Ubuntu 11.10 from the command line?

Quanta is great for Web-based HTML development. Hopefully I can get this back on here again. All help is very much appreciated.

---

### Post by Nubnut on 2011-10-26
If you did an upgraed from 1104 to 1110 then it should still be installed, try going to the command line and typing "quanta" return

---

### Post by oldtimer7777 on 2011-10-26
> **Nubnut said:**
> If you did an upgraed from 1104 to 1110 then it should still be installed, try going to the command line and typing "quanta" return

I always do fresh installations of Ubuntu whenever there is a new release, it just makes it go that much easier for me, but I still need to do a reinstall of Quanta for my work at this point. Any suggestions? Or should I downgrade back to 11.04?

---

### Post by Nubnut on 2011-10-26
Its available from the software centre too

---

### Post by Nubnut on 2011-10-26
If you cant get it through the Software Centre, then try typing this form the command line

sudo apt-get install quanta

---

### Post by oldtimer7777 on 2011-10-26
> **Nubnut said:**
> If you cant get it through the Software Centre, then try typing this form the command line

sudo apt-get install quanta

When I attempt to install Quanta from the command line this is what I get:

sudo apt-get install quanta
[sudo] password: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package quanta

I have both partner and independent repositories enabled in synaptic package manager running on my Ubuntu 11.10 fresh installation.  Any other suggestions?

---

### Post by oldtimer7777 on 2011-10-26
Bump

---

### Post by lykwydchykyn on 2011-10-27
Looks like quanta was removed from oneiric because it depends on KDE 3 libraries that are no longer maintained.

Probably you can add a natty repository and download it from there.  It shouldn't affect any other packages you have installed, since APT will always try to install the newest versions of things.

---

### Post by oldtimer7777 on 2011-10-27
> **lykwydchykyn said:**
> Looks like quanta was removed from oneiric because it depends on KDE 3 libraries that are no longer maintained.

Probably you can add a natty repository and download it from there.  It shouldn't affect any other packages you have installed, since APT will always try to install the newest versions of things.

That was the confirmation I was looking for. Thank you. :) 

Closing thread.

---

### Post by de Bacon on 2011-11-20
> **lykwydchykyn said:**
> Looks like quanta was removed from oneiric because it depends on KDE 3 libraries that are no longer maintained.

Probably you can add a natty repository and download it from there.  It shouldn't affect any other packages you have installed, since APT will always try to install the newest versions of things.

How does one do this?  I am not an idiot, just sort of computer illiterate.  For me it takes near a step by step to get through an issue like this.

I do sort of depend on quanta for web-page work.  I just upgraded (fresh reload) from Kubuntu 11.04 to Ubuntu 11.10 last night.  I think I have finished pulling the rest of my hair out now!

---

### Post by larrypg on 2011-11-20
Hello,

I am sure you already know this but it seems that Quanta is not a free program but Quanta Plus is.

---

