---
title: "Ubuntu Minecraft Issues"
date: 2012-01-15
forum: General Help
---

### Post by colelw on 2012-01-15
Im aware there are many posts on this already, none seem to have the same issue, or have a working fix for me.
 Black screen issue after login.
I am running ubuntu 11.1 on an HP desktop. Stock ati/amd graphics card. I have updated the LWJGL, my graphic card driver is up to date and active. Minecraft worked fine on this system while running windows, now with ubuntu i get the black screen after login. any thoughts or ideas?

---

### Post by whatthefunk on 2012-01-15
Im guessing its a Java problem.  What java program do you have installed?  Try opening minecraft from a terminal to see if you get any error messages related to Java.

---

### Post by HavoK360 on 2012-01-15
Okay there is a few problems. One it is the openGL you have on the computer. On ubuntu, you can't modify it. The alternative way to run it is with openAL. I can't name it off of the top of my head but there is a .bat file that you can create to force mine craft to run it with openAL. There is no difference between the two. The other problem is that you may not even have java in the first place! Go to the ubuntu web software center and get everything that says openJDK. It's all java stuff. Even get the iced tea web start. You'll need it. If you have downloaded a tar.gz file from java.com, that does not install on ubuntu. Neither does the zip files for Linux. You need to get it from the web center. Hope it helps!
(oh yeah, and 1.1 is out if you didn't know...just because you may of not played it in awhile)

---

