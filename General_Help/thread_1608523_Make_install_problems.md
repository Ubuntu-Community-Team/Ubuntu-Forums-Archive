---
title: "Make install problems"
date: 2010-10-29
forum: General Help
---

### Post by mooserider2 on 2010-10-29
I am trying to install a program called airfart and when I run make after cd'ing to the appropriate file i get this

```
g++ -g `pkg-config gtk+-2.0 --cflags` -o src/main.o -c src/main.cpp
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
In file included from src/main.cpp:20:
src/main.h:25: fatal error: glib.h: No such file or directory
compilation terminated.
make: *** [src/main.o] Error 1
```

I'm not entirely sure on what to do with this...

---

### Post by 3Miro on 2010-10-29
Try going to Synaptic Package Manager (System -> Admin -> Synaptic) and search for gtk+-2.0 (you probably need the regular as well as the -dev package). Install them and try again.

---

### Post by mooserider2 on 2010-10-29
I just did apt-get install gtk+-2.0 and tryed it again but i get the same message

---

### Post by 3Miro on 2010-10-29
What do you get when you type:
```
 pkg-config gtk+-2.0 --cflags 
```
maybe you are missing pkg-config.

---

### Post by mooserider2 on 2010-10-29
I get 

```
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
```

it says I should add the directory containing `gtk+-2.0.pc' what would i do to do that?

---

### Post by 3Miro on 2010-10-29
When you go to Synaptic, is there a gtk+-2.0 development package (it will contain something like -dev in the name). I think the regular package lets  you run programs, however, the dev package lets you make new programs.

---

### Post by mooserider2 on 2010-10-30
I do not have a gtk+-2.0 -dev or any package the closest thing i have is gtk+-2.0-examples how do i add the dicrectory containing 
gtk+-2.0.pc? What is the exact name of the package that im trying to install is it a library?

---

### Post by mooserider2 on 2010-10-30
Ok shocking news i downloaded some gtk lib and tryed it again and i got something else. I get a lot of errors in a file called vendor.cpp. Stuff like 
```
‘strtok’ was not declared in this scope
```
What does this meen?

---

### Post by 3Miro on 2010-10-30
This usually means that some .h file did not get properly included. 

I just googled the airfart. This project has been abandoned since 2003, it was probably build for an older version of GTK. The problem is probably with the source-code itself and this is not easy to fix. You basically have to learn C/C++ as well as GTK, then study the program and figure out what is wrong with it. If I were you, I would look for a more modern alternatives to the program.

---

### Post by 3Miro on 2010-10-30
On the other hand, this looks exactly like what nm-applet does when you have to pick a wireless network. Just click on the network icon and you will get a list of nearby networks and their strength.

---

### Post by mooserider2 on 2010-10-30
I thought that age might be a problem, but I'm looking for something that will give me real time signal strength data from multiple wireless routers, do you know anything that fits that discription?

---

