---
title: "Ubuntu, Launchpad, Bzr help?"
date: 2009-07-01
forum: General Help
---

### Post by idk1333 on 2009-07-01
Can someone give me a quick brief about Launchpad and Bazzar?

I'm using Ubuntu 9.04, and i'm trying to animate my desktop background with .gif images.
[http://ubuntuforums.org/showthread.php?t=926519&highlight=how+do+i+use+moving+background](http://ubuntuforums.org/showthread.php?t=926519&highlight=how+do+i+use+moving+background)

I've already executed 
sudo apt-get install bzr build-essential gifsicle
And have already registered on launchpad, and entered my SSH Keys. 

On [http://ubuntuforums.org/showthread.php?t=926519&highlight=how+do+i+use+moving+background](http://ubuntuforums.org/showthread.php?t=926519&highlight=how+do+i+use+moving+background)
What does he meant by:- 

Now let's grab the code:
Code:

bzr branch lp:xwinwrap

Whenever i run " bzr branch lp:xwinwrap " in terminal, it says

idkk111@idkk111-laptop:~$ bzr branch lp:xwinwrap
bzr: ERROR: Target directory "xwinwrap" already exists.

---

### Post by .Maleficus. on 2009-07-01
Did you try the next command ("cd xwinwrap")?  When you run "bzr branch lp:xwinwrap" it checks out a copy of xwinwrap from Launchpad.  If you already have the directory "xwinwrap" it's already checked out the code and put it in a directory.

---

### Post by idk1333 on 2009-07-01
Well, i did, and here's the result:-

> idkk111@idkk111-laptop:~$ cd xwinwrap
idkk111@idkk111-laptop:~/xwinwrap$ make> gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
xwinwrap.c:45:22: error: X11/Xlib.h: No such file or directory
xwinwrap.c:46:23: error: X11/Xutil.h: No such file or directory
xwinwrap.c:47:23: error: X11/Xatom.h: No such file or directory
xwinwrap.c:48:24: error: X11/Xproto.h: No such file or directory
xwinwrap.c:50:34: error: X11/extensions/shape.h: No such file or directory
xwinwrap.c:51:36: error: X11/extensions/Xrender.h: No such file or directory
xwinwrap.c:110: error: expected ‘)’ before ‘*’ token
xwinwrap.c:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
xwinwrap.c:192: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘find_desktop_window’
xwinwrap.c: In function ‘main’:
xwinwrap.c:234: error: ‘Display’ undeclared (first use in this function)
xwinwrap.c:234: error: (Each undeclared identifier is reported only once
xwinwrap.c:234: error: for each function it appears in.)
xwinwrap.c:234: error: ‘dpy’ undeclared (first use in this function)
xwinwrap.c:235: error: ‘Window’ undeclared (first use in this function)
xwinwrap.c:235: error: expected ‘;’ before ‘win’
xwinwrap.c:236: error: expected ‘;’ before ‘root’
xwinwrap.c:237: error: expected ‘;’ before ‘p_desktop’
xwinwrap.c:239: error: ‘XSizeHints’ undeclared (first use in this function)
xwinwrap.c:239: error: expected ‘;’ before ‘xsh’
xwinwrap.c:240: error: ‘XWMHints’ undeclared (first use in this function)
xwinwrap.c:240: error: expected ‘;’ before ‘xwmh’
xwinwrap.c:255: error: ‘Atom’ undeclared (first use in this function)
xwinwrap.c:255: error: expected ‘;’ before ‘state’
xwinwrap.c:259: error: ‘Pixmap’ undeclared (first use in this function)
xwinwrap.c:259: error: expected ‘;’ before ‘mask’
xwinwrap.c:260: error: ‘GC’ undeclared (first use in this function)
xwinwrap.c:260: error: expected ‘;’ before ‘mask_gc’
xwinwrap.c:261: error: ‘XGCValues’ undeclared (first use in this function)
xwinwrap.c:261: error: expected ‘;’ before ‘xgcv’
xwinwrap.c:263: warning: implicit declaration of function ‘XOpenDisplay’
xwinwrap.c:270: warning: implicit declaration of function ‘DefaultScreen’
xwinwrap.c:271: error: ‘root’ undeclared (first use in this function)
xwinwrap.c:271: warning: implicit declaration of function ‘RootWindow’
xwinwrap.c:279: warning: implicit declaration of function ‘XParseGeometry’
xwinwrap.c:296: error: ‘state’ undeclared (first use in this function)
xwinwrap.c:296: warning: implicit declaration of function ‘XInternAtom’
xwinwrap.c:382: error: ‘xsh’ undeclared (first use in this function)
xwinwrap.c:382: error: ‘PSize’ undeclared (first use in this function)
xwinwrap.c:382: error: ‘PPosition’ undeclared (first use in this function)
xwinwrap.c:383: warning: implicit declaration of function ‘DisplayWidth’
xwinwrap.c:384: warning: implicit declaration of function ‘DisplayHeight’
xwinwrap.c:393: error: ‘xwmh’ undeclared (first use in this function)
xwinwrap.c:393: error: ‘InputHint’ undeclared (first use in this function)
xwinwrap.c:398: error: ‘XSetWindowAttributes’ undeclared (first use in this function)
xwinwrap.c:398: error: expected ‘;’ before ‘attr’
xwinwrap.c:399: error: ‘Visual’ undeclared (first use in this function)
xwinwrap.c:399: error: ‘visual’ undeclared (first use in this function)
xwinwrap.c:401: warning: implicit declaration of function ‘findArgbVisual’
xwinwrap.c:408: error: ‘attr’ undeclared (first use in this function)
xwinwrap.c:410: warning: implicit declaration of function ‘XCreateColormap’
xwinwrap.c:410: error: ‘AllocNone’ undeclared (first use in this function)
xwinwrap.c:412: error: ‘win’ undeclared (first use in this function)
xwinwrap.c:412: warning: implicit declaration of function ‘XCreateWindow’
xwinwrap.c:413: error: ‘InputOutput’ undeclared (first use in this function)
xwinwrap.c:414: error: ‘CWBackPixel’ undeclared (first use in this function)
xwinwrap.c:414: error: ‘CWBorderPixel’ undeclared (first use in this function)
xwinwrap.c:414: error: ‘CWColormap’ undeclared (first use in this function)
xwinwrap.c:418: error: expected ‘;’ before ‘attr’
xwinwrap.c:421: warning: implicit declaration of function ‘find_desktop_window’
xwinwrap.c:421: error: ‘p_desktop’ undeclared (first use in this function)
xwinwrap.c:424: error: ‘CopyFromParent’ undeclared (first use in this function)
xwinwrap.c:425: error: ‘CWOverrideRedirect’ undeclared (first use in this function)
xwinwrap.c:435: warning: implicit declaration of function ‘XSetWMProperties’
xwinwrap.c:438: warning: implicit declaration of function ‘setWindowOpacity’
xwinwrap.c:442: error: ‘Region’ undeclared (first use in this function)
xwinwrap.c:442: error: expected ‘;’ before ‘region’
xwinwrap.c:444: error: ‘region’ undeclared (first use in this function)
xwinwrap.c:444: warning: implicit declaration of function ‘XCreateRegion’
xwinwrap.c:447: warning: implicit declaration of function ‘XShapeCombineRegion’
xwinwrap.c:447: error: ‘ShapeInput’ undeclared (first use in this function)
xwinwrap.c:447: error: ‘ShapeSet’ undeclared (first use in this function)
xwinwrap.c:448: warning: implicit declaration of function ‘XDestroyRegion’
xwinwrap.c:453: warning: implicit declaration of function ‘XChangeProperty’
xwinwrap.c:454: error: ‘XA_ATOM’ undeclared (first use in this function)
xwinwrap.c:454: error: ‘PropModeReplace’ undeclared (first use in this function)
xwinwrap.c:459: error: ‘mask’ undeclared (first use in this function)
xwinwrap.c:459: warning: implicit declaration of function ‘XCreatePixmap’
xwinwrap.c:460: error: ‘mask_gc’ undeclared (first use in this function)
xwinwrap.c:460: warning: implicit declaration of function ‘XCreateGC’
xwinwrap.c:460: error: ‘xgcv’ undeclared (first use in this function)
xwinwrap.c:467: warning: implicit declaration of function ‘XSetForeground’
xwinwrap.c:468: warning: implicit declaration of function ‘XFillRectangle’
xwinwrap.c:471: warning: implicit declaration of function ‘XFillArc’
xwinwrap.c:476: error: ‘XPoint’ undeclared (first use in this function)
xwinwrap.c:476: error: expected ‘;’ before ‘points’
xwinwrap.c:484: warning: implicit declaration of function ‘XFillPolygon’
xwinwrap.c:484: error: ‘points’ undeclared (first use in this function)
xwinwrap.c:484: error: ‘Complex’ undeclared (first use in this function)
xwinwrap.c:484: error: ‘CoordModeOrigin’ undeclared (first use in this function)
xwinwrap.c:494: warning: implicit declaration of function ‘XShapeCombineMask’
xwinwrap.c:494: error: ‘ShapeBounding’ undeclared (first use in this function)
xwinwrap.c:497: warning: implicit declaration of function ‘XMapWindow’
xwinwrap.c:501: warning: implicit declaration of function ‘XLowerWindow’
xwinwrap.c:504: warning: implicit declaration of function ‘XSync’
xwinwrap.c:538: warning: implicit declaration of function ‘XDestroyWindow’
xwinwrap.c:539: warning: implicit declaration of function ‘XCloseDisplay’
make: *** [all64] Error 1> idkk111@idkk111-laptop:~/xwinwrap$ sudo make install
make: *** No rule to make target `install'.  Stop.
idkk111@idkk111-laptop:~/xwinwrap$ 

---

### Post by .Maleficus. on 2009-07-01
You need the development headers for Xorg.
```
sudo apt-get install xorg-dev
```

---

### Post by idk1333 on 2009-07-01
Still receiving errors,

> 
idkk111@idkk111-laptop:~$ cd xwinwrap
idkk111@idkk111-laptop:~/xwinwrap$ make
gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
mkdir x86_64
mkdir: cannot create directory `x86_64': File exists
make: [all64] Error 1 (ignored)
mv ./xwinwrap ./x86_64
gcc -m32 -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
mkdir i386
mkdir: cannot create directory `i386': File exists
make: [all32] Error 1 (ignored)
mv ./xwinwrap ./i386
idkk111@idkk111-laptop:~/xwinwrap$ 

 how do i fix it?

---

### Post by .Maleficus. on 2009-07-01
Both errors appeared to have been ignored so try "sudo make install" now.  Post back the outcome of that.

---

### Post by idk1333 on 2009-07-01
Well after executing "cd xwinwrap" and "make", 
Two new folder has been created under xwinwrap directory.
(1) i386 & (2) x86_64

But i'm still unable to execute sudo make install. =/

> idkk111@idkk111-laptop:~$ cd xwinwrap
idkk111@idkk111-laptop:~/xwinwrap$ make
gcc -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
mkdir x86_64
mkdir: cannot create directory `x86_64': File exists
make: [all64] Error 1 (ignored)
mv ./xwinwrap ./x86_64
gcc -m32 -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls -lX11 -lXext -lXrender xwinwrap.c -o xwinwrap
mkdir i386
mkdir: cannot create directory `i386': File exists
make: [all32] Error 1 (ignored)
mv ./xwinwrap ./i386
idkk111@idkk111-laptop:~/xwinwrap$ sudo make install
make: *** No rule to make target `install'.  Stop.

---

