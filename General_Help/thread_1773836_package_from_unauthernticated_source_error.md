---
title: "package from unauthernticated source error"
date: 2011-06-02
forum: General Help
---

### Post by qwertyjjj on 2011-06-02
I am trying to install an iso reader but no matter which package I choose they all return this error:

**The action would require the installation of packages from unauthenticated sources.**

These are all packages in the Ubuntu Software centre so am not sure what the problem is.

---

### Post by qwertyjjj on 2011-06-03
> **qwertyjjj said:**
> I am trying to install an iso reader but no matter which package I choose they all return this error:

**The action would require the installation of packages from unauthenticated sources.**

These are all packages in the Ubuntu Software centre so am not sure what the problem is.

any ideas?

---

### Post by jerrrys on 2011-06-03
**unauthenticated sources **usually means your missing a key (authentication) in your software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources&sa=Search&cof=FORID:9#851](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources&sa=Search&cof=FORID:9#851)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources+authentication&sa=Search&cof=FORID:9#836](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources+authentication&sa=Search&cof=FORID:9#836)

---

### Post by qwertyjjj on 2011-06-03
> **jerrrys said:**
> **unauthenticated sources **usually means your missing a key (authentication) in your software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources&sa=Search&cof=FORID:9#851](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources&sa=Search&cof=FORID:9#851)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources+authentication&sa=Search&cof=FORID:9#836](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+sources+authentication&sa=Search&cof=FORID:9#836)

how do I find the one that's missing the key though and remove it?
I think it might be WinFF

The solution here worked but I'm not sure if it was a good thing to do:
[http://ubuntuforums.org/showthread.php?t=1327907](http://ubuntuforums.org/showthread.php?t=1327907)
[I]Posting to help others:
I just received the same error message. I used apt-get on the command line to install what i needed, but I didnt want to have to revert to that all the time. I like browsing the software manager for games and stuff. So after installing 2 packages on the command line, I went searching for the issue.
My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever. Hope it helps somebody browsing, since at this moment, this is google's #1 result for the error message.[/I]

---

### Post by linuxinstalledfromhdd on 2011-06-03
Enable your ind and partner repositories

and then run

sudo apt-get install winff 

from terminal

---

### Post by qwertyjjj on 2011-06-04
> **linuxinstalledfromhdd said:**
> Enable your ind and partner repositories

and then run

sudo apt-get install winff 

from terminal

ind?
independent? it was already enabled and winff is already installed.

---

