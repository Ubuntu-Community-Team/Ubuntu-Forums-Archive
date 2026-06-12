---
title: "Problem with compiling Gimp Painter"
date: 2009-12-25
forum: General Help
---

### Post by chris_0076 on 2009-12-25
EDIT EDIT

Problem solved.

For future reference to install Gimp Painter for Ubuntu 9.10:

How to Build:
1. Download the Gimp Source Code and Gimp Painter patch
[ftp://ftp.gimp.org/pub/gimp/v2.6/gimp-2.6.6.tar.bz2](ftp://ftp.gimp.org/pub/gimp/v2.6/gimp-2.6.6.tar.bz2)
[http://sourceforge.jp/projects/gimp-painter/downloads/41325/gimp-painter--20090715.diff/](http://sourceforge.jp/projects/gimp-painter/downloads/41325/gimp-painter--20090715.diff/)

2. Extract the Gimp Source Code to the Desktop (/home/USERNAME/Desktop)

3. Move the gimp-painter--20090715.diff file to the desktop (do not place it in the Gimp Source Code folder)

4. Open a terminal (Applications -> Accessories -> Terminal)

5. Type "sudo apt-get build-dep gimp" into the terminal without the quotes.

6. Type your password into the terminal when prompted.

7. Type "cd /home/USERNAME/Desktop/gimp-2.6.6" into the terminal without the quotes. This should move you into the folder with the gimp source code.

8. Type "patch -p1 < ../gimp-painter--20090715.diff" into the terminal without the quotes. This should patch the gimp source code so that Gimp Painter will work.

9. Type "./configure" into the terminal without the quotes. This will configure for the build.

10. Type "sudo make" into the terminal without the quotes. This will build the source code to allow you to use Gimp Painter.
 
11. Type "sudo make install" into the terminal without the quotes. This will install Gimp Painter.
  

After Install:
After that if you had gimp already installed go to Applications -> Graphics - Gimp 
If you did not have gimp installed then type "gimp" into the terminal to run it.

If something pops up up and says something like this:

```
"Libgimp version mismatch!

The GIMP binary cannot run with a libgimp version
other than its own. This is GIMP 2.6.6, but the
libgimp version is 2.6.7.

Maybe you have GIMP versions in both /usr and /usr/local ?"
```Then you need to go System -> Administration -> Synaptic Package Manager
Once it opens search for "libgimp".
Once you find it right click on it and set it to be removed. Then apply those settings and restart.

Now you can go to Applications -> Graphics -> Gimp and it should work just fine.

Hope this helps someone in the future.







I just tried to compile the Gimp painter patch to gimp and now it has just finished. Where can I go to find the file that I can use to run gimp? I also noticed that in compiling gimp it has used up about 600Mb. How can I get rid of all of this excess junk. I know for a fact that it is not that big because I had the exact same thing installed on my windows machine and it was less than 100Mb. I know several things that had to be installed for it to compile. 

I have used sudo apt-get clean, sudo apt-get autoclean, and the computer janitor and there is still a lot left.


So I guess I have two options that you can help me with:
1. Where is the file to run gimp at?
and if that how do I delete the extra files?


2. How do I remove all the files that are associated with the gimp so that I can just run a normal install of gimp?

Sorry if I am making no sense I am running on next to no sleep because I am trying to get this to work.


EDIT
New problem

When I run gimp it says:
"Libgimp version mismatch!

The GIMP binary cannot run with a libgimp version
other than its own. This is GIMP 2.6.6, but the
libgimp version is 2.6.7.

Maybe you have GIMP versions in both /usr and /usr/local ?"

I checked /usr and /usr/local and there are no gimp folders there.

---

### Post by Sc10 on 2010-01-15
Thanks a a lot chris! I too have been wanting gimp-painter on my new machine (despite having a lousy Aiptech tablet that disables the mouse from the canvas) and your steps worked flawlessly! Time for [GPS]("http://code.google.com/p/gps-gimp-paint-studio/")...

Next I'll be looking into getting a PPA.

Cheers and happy painting!

:KS

---

