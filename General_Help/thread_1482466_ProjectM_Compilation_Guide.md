---
title: "ProjectM Compilation Guide"
date: 2010-05-13
forum: General Help
---

### Post by AxelMan0 on 2010-05-13
About a year ago I started using Ubuntu as my primary operating system. I really missed the beautiful windows visualizer known as Milkdrop, and after a quick google search I found ProjectM. The precompiled files would not work on my machine, however, so I decided to try and compile it myself. I was too new at the Linux game to figure out how to do it--ProjectM can be a bit of a b*tch to compile for a newbie.
     So here I am, a year later, a year more experienced, and I recently decided to give ProjectM another shot. Well I have good news! I got it to work wonderfully, so I've decided to outline the steps of MY compilation so that other newbies can glean some insight into compiling programs for themselves, and hopefully get the most up to date version of ProjectM running on their Linux boxes!
     I myself am no pro at this, so anyone with more experience than me that wants to point out some conventions I may be ignoring is encouraged to say so!

Step 1: Make a folder to put the source code in
```

cd ~
mkdir src/projectm

```Step 2: Download from svn

I went to the projectM sourceforge page and found the proper svn url:

```

svn co [https://projectm.svn.sf.net/svnroot/projectm/trunk](https://projectm.svn.sf.net/svnroot/projectm/trunk)  projectm

```note: the website actually says 'projectM-Trunk' at the end instead of projectm, but caps and dashes are really annoying in folder names, so I replaced that with 'projectm'

Step 3: Dependencies

I found a list of the dependencies on the ProjectM wiki:
ftgl-dev >= 2.1.3-rc5 
 libglew1.5-dev 
 libsdl-dev 
 qt4-dev-tools

I then made sure that libglew1.5-dev was truely the most recent version available from apt-get, in case a newer version was out (note: this is an unnecessary step, and installing a different version than specified may actually prevent the program from compiling correctly if the particular package isn't backwards compatible).

```

zak@zak-laptop:~/src/projectm/src$ apt-cache search glew
glew-utils - The OpenGL Extension Wrangler - utilities
libglew1.5 - The OpenGL Extension Wrangler - runtime environment
libglew1.5-dev - The OpenGL Extension Wrangler - development environment
libglewmx1.5 - The OpenGL Extension Wrangler - runtime environment
libglewmx1.5-dev - The OpenGL Extension Wrangler - development environment
python-pyglew - GLEW bindings for Python

```indeed libglew1.5 is the most recent version

```

sudo apt-get install ftgl-dev libglew1.5-dev libsdl-dev qt4-dev-tools

```Step 4: Configure and produce the makefiles

ProjectM compiles using ccmake, and I wasn't sure if I had it installed, so i tried it.

```

cd ~/src/projectm/src
ccmake .

```at this point the terminal politely informed me that I did not have it installed, and gave me the name of the package to install, "cmake-curses-gui". Run ccmake as above, and you should be presented with a more or less blank screen, press 'c'. This provides a wonderful gui and i will be using ccmake from now on whenever possible. Below is a screenshot of MY configuration options (courtesy of a program called Shutter, and freeimagehosting.net) YOU may want different ones. If you're going to take the time to compile something yourself, you may as well get what YOU want out of it.
Decisions I made and why (this is part of a guide most people ignore, but the why is SO important!):

-The site recommends setting CMAKE_BUILD_TYPE to 'Release' for optimum performance
-Changed CMAKE_INSTALL_PREFIX from /usr/local to /usr because it is usually good practice to do so
-set EXECUTABLE_OUTPUT_PATH to /usr/bin/projectm. Usually this would simply be /usr/bin but because of my previous experiences trying to get this to work, I decided it would be nice to have all of the ProjectM executables (since I am compiling multiple versions) in one place for easy removal. 
-turned INCLUDE-PROJECTM-JACK on, if you don't use jack don't turn this on. I am trying to move to an all-jack audio setup, and I also thought it would be cool to play some live music into my computer and have ProjectM visualize it.
-turned INCLUDE-PROJECTM-LIBVISUAL-ALS (experimental) on. I figured what the hell, I'm compiling this, I might as well try and get every cool feature I can.
-set LIBRARY_OUTPUT_PATH to /usr/lib/projectm. Just like all executables should go in /usr/bin, all libraries should go in /usr/lib in their respective program folders.
-set USE_CG on. After all, I'm doing this to replace Milkdrop, I gotta have my pixel shaders!

[[IMG]http://www.freeimagehosting.net/uploads/6cb8da50e0.png[/IMG]]("http://www.freeimagehosting.net/")

Every once in awhile ccmake will update the options available, so when you're done go back up to the top and make sure there are no new ones. When all required options are set a new command should appear on the bottom of the screen accessible by the 'g' key. Press the 'g' key.

step 5: Compile!

Now for the moment of truth!
```

make

```Now, as expected (this almost never works the first time) I ran into a few problems. It tried to link something or other in /usr/bin/projectm and it said 'permission denied'. Sudo make didn't seem like the best idea to me, I didn't want to have to run ProjectM as root every time or something like that. Luckily I put all the ProjectM executables in one folder! Now all I needed to do to fix the problem was change ownership of that one folder from 'root' to (in my case) 'zak'.

I'm not too used to using chown, so a quick
```

man chown

```and I knew enough to type

```

zak@zak-laptop:~/src/projectm/src$ sudo chown -R zak /usr/bin/projectm

```'-R' makes it recursive, so that all the subfolders and files get their ownership changed as well.

I ran into a similar problem with the lib directory after trying to run 'make' a second time, so I did an identical chown command for /usr/lib/projectm.

Third time's the charm! I tried again and it worked all the way through.

Step 6: Install

```

sudo make install

```I test the program, which surprisingly picks up the last.fm acid jazz radio I have playing in Firefox right away. I now have my fully working and extremely pretty ProjectM, with extra versions for jack and an experimental stand-alone thing to play with. :P

And there you have it! My compilation experience with ProjectM. I hope it helps somebody out there :)

---

### Post by shantiq on 2010-12-20
hi there alex   first of all thanx for this

 got to step 4 and i get this



```
CMake Error at projectM-libvisual/CMakeLists.txt:41 (MESSAGE):
   libvisual 0.4 not found! Please visit http://libvisual.sf.net and download
   the module.
```


but i have libvisual 0.4 installed   it is in my synaptic


any idea anyone?

---

### Post by shantiq on 2010-12-21
ok really puzzling now    works in qmmp and audacious and works well    but never did make or sudo make install :KS



ok maybe i had it already installed with [this]("http://ubuntuforums.org/showpost.php?p=3903253&postcount=1")


not sure but good anyway

---

