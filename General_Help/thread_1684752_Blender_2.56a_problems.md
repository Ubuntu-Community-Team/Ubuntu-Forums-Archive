---
title: "Blender 2.56a problems"
date: 2011-02-09
forum: General Help
---

### Post by pages on 2011-02-09
Hi all ,
For a project i was doing on 64 bit Ubuntu i needed Blender so i downloaded the file extracted it and simply double clicked the application to run it
Now im operating from a laptop 32bit Ubuntu and tried the same process ( obviously selected the 32bit download) and nothing happens when i double click it
I tried it from the command line 
```

shane@ubuntu:~/blender-2.56a-beta-linux-glibc27-i686$ blender
The program 'blender' is currently not installed.  You can install it by typing:
sudo apt-get install blender
shane@ubuntu:~/blender-2.56a-beta-linux-glibc27-i686$ sudo apt-get install blender

```

just to note i never had to do this on the 64 bit OS but after it downloaded and installed what it required i then tried running the program

```
 
shane@ubuntu:~/blender-2.56a-beta-linux-glibc27-i686$ blender
Compiled with Python version 2.6.6.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x9
  Serial number of failed request:  21
  Current serial number in output stream:  22

```

If anyone has any ideas on how to get this application up and running i'd be extremely grateful as i am already really far behind on my final year project :)

Thanks for your time,
Pages

---

### Post by Bucic on 2011-02-20
I had problems with Blender 2.4x GUI on my buntu 10.10 x64 so I've downloaded 2.56 beta and it's all running fine, so it appears.


EDIT:
I rushed it. It doesn't work for me either after all. Ubuntu was launching the 2.49 I had installed! Now I uninstalled it and I'm trying to run 2.56 only. I did as per readme.html file in the tar.bz2 archive but doubleclicking the blender executable does nothing!



[COLOR="Silver"]I've downloaded the archive (tar.bz2) from here [http://www.blender.org/download/get-256-beta/](http://www.blender.org/download/get-256-beta/) extracted it, navigated to the directory in the Terminal and simply typed **blender**. Try if this works for you. Doubleclicking didn't work for me.


BTW, the recommended installation procedure for 2.56 from PPA gave me an error
```
:~$ sudo add-apt-repository ppa:cheleb/blender-svn
Error reading https://launchpad.net/api/1.0/~cheleb/+archive/blender-svn: <urlopen error [Errno 113] No route to host>

```

All in all I'm satisfied that it at least works now. Could anyone tell me how to create a launcher/shortcut to blender in my scenario?[/COLOR]

---

