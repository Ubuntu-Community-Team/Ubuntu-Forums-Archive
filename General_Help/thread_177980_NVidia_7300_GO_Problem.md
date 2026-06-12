---
title: "NVidia 7300 GO Problem"
date: 2006-05-17
forum: General Help
---

### Post by ilektriksky on 2006-05-17
Hi,

Was curious if anyone had run into this error when attempting to install nvidia drivers for their NVidia 7300 GO.  I followed the link on how to install the drivers and as far as I can tell they are install correctly.

After installing and resetting the xserver:

________________________________________

(EE) NVIDIA(0): Failed to allocate rankine object

Fatal server error:
AddScreen/ScreenInit failed for driver 0
________________________________________

If anyone knows of a solution or has any ideas please let me know.

Thanks

---

### Post by ilektriksky on 2006-05-19
Also,

I've tried manually compiling the latest versions of nvidia drivers, but no luck still.

I think I will probably have to just wait a few weeks till the newest nvidia drivers are supported.


Ilektrik

---

### Post by firetux on 2006-06-05
What does ```
glxinfo
``` give?

---

### Post by anton_most_muscular on 2006-07-21
hey I'm having the same problem! I have nvidia 7300 LE
I've tried *EVERYTHING!* no solution. dosnt work in fedora or kubuntu either.

One thread I've read reckons you need to uninstall EVERYTHING relating to NVidia (its in the forums somewhere) and reinstall thru synaptec -however i dont think it will work (will try tomorrow).

This is driving me insane so I would love to find a solution

ant

---

