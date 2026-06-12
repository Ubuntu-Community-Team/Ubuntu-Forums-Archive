---
title: "Noob mistake, need assistance"
date: 2010-08-06
forum: General Help
---

### Post by kingme23 on 2010-08-06
I was ignorant enough to try and install google earth on my laptop (Ubuntu 10.04), of course I realize after the fact that trying to install it the easy way doesn't work on 64 bit. I X'ed out of the terminal thinking it was just a glitch but now it's caused some issues, it removed my flash plugins and I can't get to synaptic package manager. It says something along the lines of "can't unlock synaptic, this usually means another package manager is in use", my guess is the process is somehow still running? Any help would be appreciated.

---

### Post by worksofcraft on 2010-08-06
By aborting the installation you may have left a lock file.

Simply delete /var/lib/dpkg/lock and then it should work again
You will probably need root permission to do this:

sudo rm /var/lib/dpkg/lock

p.s. I downloaded GoogleEarthLinux.bin for 64 bit from a web site somewhere and running that installed no problem :)

---

### Post by kingme23 on 2010-08-06
Ok I've made some progress lol..when I try to install flash plugin it says it will remove googleearth but this is the message I keep getting:

"E: I wasn't able to locate a file for the googleearth package. This might mean you need to manually fix this package. (due to missing arch)"

I never fully installed it, so that is probably why it can't locate a file. I stumbled across this [http://www.newt.com/debian/blog.html#interrupting-aptitude](http://www.newt.com/debian/blog.html#interrupting-aptitude) if it worked for that it should work for google earth as well right? What would I type into the terminal? Thanks for any answers I truly am a linux n00b.

---

