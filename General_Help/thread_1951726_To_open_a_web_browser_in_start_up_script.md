---
title: "To open a web browser in start up script"
date: 2012-04-03
forum: General Help
---

### Post by ajaypadvi on 2012-04-03
Hello all;
I want to open a web browser in start up script while booting an ubuntu machine up.
I have tried googling over it but didnt found any useful solutions with some of which says to change System->preferences->start up apps properties,But my requirement is to open it via start up script.
Please help me out if its there any possible outcome as solution for above one.

Thanks 
Ajay

---

### Post by hwttdz on 2012-04-03
You can make your script the start up application and then just have the script call the browser (though this is just adding an unnecessary layer).  

If you're using gnome (which I assume), you can read some more about it here: [http://www.yolinux.com/TUTORIALS/GNOME.html#INITIALIZATION](http://www.yolinux.com/TUTORIALS/GNOME.html#INITIALIZATION)
The start up applications is just providing a means of interacting with the /usr/share/gnome/default.session file (which looks a little annoying).

---

