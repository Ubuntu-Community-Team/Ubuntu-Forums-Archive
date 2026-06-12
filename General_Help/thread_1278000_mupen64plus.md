---
title: "mupen64plus"
date: 2009-09-29
forum: General Help
---

### Post by minasmorath on 2009-09-29
Hi all,

I am having some troubles using mupen64plus (The N64 Emulator), mainly I get a small, uncloseable popup that states simply "ERROR: Cannot set display mode", and now more recently "The core thread recieved a SIGSEGV signal".

To clarify some technical points, I am running Debian Testing, and for those that don't know it's what Ubuntu is based upon, and is basically the same thing as whatever new version comes around. My pc specs are as follows:

intel core 2 duo 2.2 ghz (32 bit)
1 gb RAM
nvidia geForce 8400M GS
1280x800 24-bit LCD display

Graphics drivers are the latest from nVidia, 185 i believe. I had the thing working, I was playing F-Zero X, closed it, and tried to open Ocarina of Time, and these errors started. No config changes, no hardware swaps, no nothing.

If anyone has more expertise in this area than me, please feel more than welcome to help me out. Thanks ahead of time!

Mitch

---

### Post by sedawk on 2009-09-29
Hello!

If you changed nothing else you might be suffering from
broken configuration files.

You can try to create a new user (with fresh desktop)
and check if it still happens for that new user.

If not you can try to cleanup your configuration files
for the application. Is there any directory like
```

ls -d ~/.mup*

```
?

---

### Post by minasmorath on 2009-09-29
ah, thanks for the reply

There is a ~/.mupen64plus directory... I'll delete it and see how the program responds, although i attempted purging the program and all dependencies and reinstalling it, and that didn't change the issue.

Also, now every couple boots GDM refuses to start, but i can still login at tty1 and issue 'startx' and my xfce-session comes up just fine... side effect of purging?

thanks again,

Mitch

---

### Post by argor on 2009-10-26
TRY to download from this site [http://code.google.com/p/mupen64plus/downloads/list](http://code.google.com/p/mupen64plus/downloads/list) the deb file can be more unstable  than the binary package 
then just unzip and run the program

---

