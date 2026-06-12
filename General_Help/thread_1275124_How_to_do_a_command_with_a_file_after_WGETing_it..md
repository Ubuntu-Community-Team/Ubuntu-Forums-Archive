---
title: "How to do a command with a file after WGETing it."
date: 2009-09-25
forum: General Help
---

### Post by rob86 on 2009-09-25
I want to make a simple script to download an image with wget, and then open it in gthumb. I know how to use wget, and I know how to open an image (I'm using gthumb), but I don't know how to make the "gthumb TheImage" wait for the file to be done downloading. Is this possible with a bash script?

---

### Post by XCan on 2009-09-25
Now I'm green when it comes to bash scripting, but what happens if you do ```
 wget link.here && gthumb TheImage 
``` If I get the whole thing correctly, && would put gthumb on hold until wget runs succesfully.

---

### Post by StuartN on 2009-09-25
> **rob86 said:**
> I know how to use wget, and I know how to open an image (I'm using gthumb), but I don't know how to make the "gthumb TheImage" wait for the file

If you **wget [http://www.google.com/images/nav_logo7.png](http://www.google.com/images/nav_logo7.png) ; gthumb nav_logo7.png**, then the second command does not begin until the first has completed. And you could gthumb *.png if you were as lazy as me.

---

