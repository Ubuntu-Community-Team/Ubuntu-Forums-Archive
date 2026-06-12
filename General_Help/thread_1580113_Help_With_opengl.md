---
title: "Help With opengl"
date: 2010-09-22
forum: General Help
---

### Post by portsniper on 2010-09-22
ok so i installed ubuntu onto my laptop last night, just started playing with it this morning and i tried to install warcraft III, i was using iso, i mounted the images, installed both fine, and when i tried to run the installer it ran perfectly, and then i recieved this error

> err:ole:CoCreateInstance apartment not initialised
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:advapi:SetSecurityInfo stub
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  179 ()
  Serial number of failed request:  701
  Current serial number in output stream:  702
yes i am running wine i've updated my system and it's still not working

i'm running an Acer Aspire 5315. Any help would be appreciated

---

### Post by andrewthomas on 2010-09-22
post the output of 

```
glxinfo | grep OpenGL
```and 
```
lspci |grep VGA
``` or```
 sudo lshw -short |grep display
```

---

### Post by Serpher on 2010-09-22
Although there may be a solution to your problem, WINE does not work with everything. It's getting better and better, but it's not completely there yet. It's extremely difficult to make WINE, and it's amazing they've come this far. To help you further I'd also have to see the output of the commands andrew told you to punch into terminal.

---

