---
title: "Cannot start Ubuntu after trying to upgrade gnucash"
date: 2009-08-30
forum: General Help
---

### Post by nestor_stura on 2009-08-30
I have probably made a big mistake, but don't know where...

It was the first time I tried to install a .tar.bz2 program.

I downloaded the newest release of gnucash (2.3.4) and followed the instructions for installation (extract, ./configure, make and make install)
While in the configure step, it stopped saying that it needed a newer version of Glib (2.6) I downloaded and installed also fron a .tar.bz2 file.

Next I tried to install gnucash again and now it said that I have glib installed, but an older version too and to remove that version (thing that I don't know how).

The real problem came afterwards. I give up trying to install gnucash, until I get more info and turned mi PC off. Later, when I turned it on, I could not enter. The screen asking for user and password changed for a simpler black and white screen and after entering my user and passw. it appears to go to the Terminal: nestor@nestor-desktop:$ 
The only command I remembered was reboot, so after rebooting her I am, using Win... to get to this forum and ask if someone knows how to solve this issue.
By the way I am using Ubuntu 9.04(32) and I have already tried to start in recovery mode with the same result.
Thanks in advance.

---

### Post by Liolikas on 2009-08-30
...newer version of Glib (2.6) I downloaded and installed also fron a .tar.bz2 file.
And that was very bad idea because half of your system need older glib.
Now try simple fix:
sudo apt-get install glib

Next time install programs over Synaptic or apt-get.

---

### Post by nestor_stura on 2009-08-30
> **Liolikas said:**
> ...newer version of Glib (2.6) I downloaded and installed also fron a .tar.bz2 file.
And that was very bad idea because half of your system need older glib.
Now try simple fix:
sudo apt-get install glib

Next time install programs over Synaptic or apt-get.

Liolikas, thanks for your prompt reply.
My problem now is that I cannot start Ubuntu.

I tried your suggestion from the root shell prompt but it says "glib file not found"

Néstor

---

### Post by Metallinut on 2009-11-21
I had Gnucash running just fine. Then I upgraded to 9.10. Now Gnucash can't start, saying that it can't parse the URL of my data file.

Fortunately I have this running in a virtualbox machine, so I could roll back a version, but what gives?!?

Anyone else have Gnucash stop working after an upgrade?

---

