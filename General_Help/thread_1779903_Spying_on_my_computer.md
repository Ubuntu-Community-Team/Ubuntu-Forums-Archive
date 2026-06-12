---
title: "Spying on my computer"
date: 2011-06-11
forum: General Help
---

### Post by John Rogers on 2011-06-11
I have Audacity installed.
I have installed the help files in /usr/share/audacity/help/manual
BUT when I click on the "Index" option under the Help menu I get a message that I have not installed the Help files....
How do I find out where my computer is looking for those help files, please?

---

### Post by knutschr on 2011-06-11
Try
>  whereis audacity


---

### Post by John Rogers on 2011-06-11
Thanks for that suggestion.

dell@dell-desktop:~$ whereis audacity
audacity: /usr/bin/audacity /usr/share/audacity /usr/share/man/man1/audacity.1.gz

I can understand the /usr/bin/audacity is the binary program file
And  /usr/share/audacity  is where I tried installing the help files without getting the right response.
So does that mean I should try putting them in  /usr/share/man/man1/  ??
If so, will audacaity be looking for man, manual, help..... or what ?

Thanks again.

---

### Post by John Rogers on 2011-06-11
O.K. so I've worked out that the /usr/share/man/man1/audacity.1.gz is where the computer finds its response to 
dell@dell-desktop:~$ man audacity

...and this documentation says that the first place audacity looks for help files is in /usr/share/audacity which is where I currently have the help files. I can only presume it is looking at a different level or for a different label...

That is why I wondered if there is a technique for tracking where and what it is consulting.  ;-)

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **John Rogers said:**
> O.K. so I've worked out that the /usr/share/man/man1/audacity.1.gz is where the computer finds its response to 
dell@dell-desktop:~$ man audacity

...and this documentation says that the first place audacity looks for help files is in /usr/share/audacity which is where I currently have the help files. I can only presume it is looking at a different level or for a different label...

That is why I wondered if there is a technique for tracking where and what it is consulting.  ;-)

Make sure you consult Synaptic Package Manager first and do a search for whatever application you are looking for help and documentation..  Usually you need to manually install those through Synaptic Package Manager if needed. They do so as to save space.

---

