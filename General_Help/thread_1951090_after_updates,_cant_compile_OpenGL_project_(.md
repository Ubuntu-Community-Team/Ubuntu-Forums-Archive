---
title: "after updates, cant compile OpenGL project :("
date: 2012-04-01
forum: General Help
---

### Post by xmorg on 2012-04-01
I just copied my current code to my laptop, overwriting the previous code, which had a binary that i compiled previous (pre updates)

Now with the new code, i type make, and basically get undefined reference to..... every glFucntion I call in my program.  The errors do not indicate that libGL.so.1 is not found.  However, I do notice that its in a VERY WIERD place  /usr/lib/i386-linux-gnu/mesa???

And libGLU.so.1 is in /usr/lib/i386-linux-gnu

I was pretty certain that these libs were in /usr/lib previously

What gives?
```

gcc -Wall  -o spearfall -lGL -lGLU -lm `sdl-config --cflags --libs` Main.c drawprims.c textures.c maps.c wfobj.c datafile.c drawing.c movement.c
Main.c: In function &#8216;main&#8217;:
Main.c:52:17: warning: unused variable &#8216;obj_tree&#8217; [-Wunused-variable]
Main.c:51:30: warning: variable &#8216;rightMouseB&#8217; set but not used [-Wunused-but-set-variable]
drawprims.c: In function &#8216;drawHgrid&#8217;:
drawprims.c:71:7: warning: variable &#8216;sl&#8217; set but not used [-Wunused-but-set-variable]
drawprims.c: In function &#8216;drawplayerIcon&#8217;:
drawprims.c:90:7: warning: variable &#8216;pos&#8217; set but not used [-Wunused-but-set-variable]
datafile.c: In function &#8216;LoadSettings&#8217;:
datafile.c:16:8: warning: variable &#8216;lSize&#8217; set but not used [-Wunused-but-set-variable]
datafile.c:12:7: warning: variable &#8216;i&#8217; set but not used [-Wunused-but-set-variable]
datafile.c: In function &#8216;getMap&#8217;:
datafile.c:134:8: warning: unused variable &#8216;str&#8217; [-Wunused-variable]
datafile.c: In function &#8216;getMap2&#8217;:
datafile.c:123:8: warning: &#8216;y&#8217; may be used uninitialized in this function [-Wuninitialized]
movement.c: In function &#8216;wallCheck&#8217;:
movement.c:15:13: warning: &#8216;loc&#8217; may be used uninitialized in this function [-Wuninitialized]
/tmp/cc70jVhr.o: In function `main':
Main.c:(.text+0x112): undefined reference to `SDL_Init'
Main.c:(.text+0x11b): undefined reference to `SDL_GetError'
Main.c:(.text+0x147): undefined reference to `SDL_GetVideoInfo'
Main.c:(.text+0x157): undefined reference to `SDL_GetError'
Main.c:(.text+0x1d6): undefined reference to `SDL_GL_SetAttribute'
Main.c:(.text+0x200): undefined reference to `SDL_SetVideoMode'
Main.c:(.text+0x213): undefined reference to `SDL_GetError'
Main.c:(.text+0x24e): undefined reference to `SDL_EnableKeyRepeat'
Main.c:(.text+0x257): undefined reference to `SDL_GetError'
Main.c:(.text+0x3ad): undefined reference to `SDL_SetVideoMode'
Main.c:(.text+0x3c0): undefined reference to `SDL_GetError'
Main.c:(.text+0x491): undefined reference to `SDL_PollEvent'
/tmp/cc70jVhr.o: In function `handleKeyPress':
Main.c:(.text+0x5c9): undefined reference to `SDL_WM_ToggleFullScreen'
Main.c:(.text+0x634): undefined reference to `sin'
Main.c:(.text+0x68e): undefined reference to `cos'
Main.c:(.text+0x71d): undefined reference to `sin'
Main.c:(.text+0x754): undefined reference to `sin'
Main.c:(.text+0x7ae): undefined reference to `cos'
Main.c:(.text+0x834): undefined reference to `sin'
/tmp/cc70jVhr.o: In function `Quit':
Main.c:(.text+0x89b): undefined reference to `SDL_Quit'
/tmp/cc70jVhr.o: In function `resizeWindow':
Main.c:(.text+0x8e6): undefined reference to `glViewport'
Main.c:(.text+0x8f2): undefined reference to `glMatrixMode'
Main.c:(.text+0x8f7): undefined reference to `glLoadIdentity'
Main.c:(.text+0x920): undefined reference to `gluPerspective'
Main.c:(.text+0x92c): undefined reference to `glMatrixMode'
Main.c:(.text+0x931): undefined reference to `glLoadIdentity'
/tmp/ccZv0XXO.o: In function `drawHFace':
drawprims.c:(.text+0x1a): undefined reference to `glBegin'
drawprims.c:(.text+0x39): undefined reference to `glNormal3f'
drawprims.c:(.text+0x4f): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x70): undefined reference to `glVertex3f'
drawprims.c:(.text+0x86): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xac): undefined reference to `glVertex3f'
drawprims.c:(.text+0xc2): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xed): undefined reference to `glVertex3f'
drawprims.c:(.text+0x103): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x129): undefined reference to `glVertex3f'
drawprims.c:(.text+0x12e): undefined reference to `glEnd'
/tmp/ccZv0XXO.o: In function `drawCubeBlock':
drawprims.c:(.text+0x161): undefined reference to `glBegin'
drawprims.c:(.text+0x177): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x198): undefined reference to `glVertex3f'
drawprims.c:(.text+0x1ae): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x1d2): undefined reference to `glVertex3f'
drawprims.c:(.text+0x1e8): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x20f): undefined reference to `glVertex3f'
drawprims.c:(.text+0x225): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x249): undefined reference to `glVertex3f'
drawprims.c:(.text+0x25f): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x280): undefined reference to `glVertex3f'
drawprims.c:(.text+0x296): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x2ba): undefined reference to `glVertex3f'
drawprims.c:(.text+0x2d0): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x2f7): undefined reference to `glVertex3f'
drawprims.c:(.text+0x30d): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x331): undefined reference to `glVertex3f'
drawprims.c:(.text+0x347): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x36b): undefined reference to `glVertex3f'
drawprims.c:(.text+0x381): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x3a8): undefined reference to `glVertex3f'
drawprims.c:(.text+0x3be): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x3e8): undefined reference to `glVertex3f'
drawprims.c:(.text+0x3fe): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x425): undefined reference to `glVertex3f'
drawprims.c:(.text+0x43b): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x45f): undefined reference to `glVertex3f'
drawprims.c:(.text+0x475): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x49c): undefined reference to `glVertex3f'
drawprims.c:(.text+0x4b2): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x4dc): undefined reference to `glVertex3f'
drawprims.c:(.text+0x4f2): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x519): undefined reference to `glVertex3f'
drawprims.c:(.text+0x51e): undefined reference to `glEnd'
/tmp/ccZv0XXO.o: In function `drawHgrid':
drawprims.c:(.text+0x5bc): undefined reference to `glBegin'
drawprims.c:(.text+0x5ff): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x618): undefined reference to `glVertex3f'
drawprims.c:(.text+0x62e): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x64b): undefined reference to `glVertex3f'
drawprims.c:(.text+0x661): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x684): undefined reference to `glVertex3f'
drawprims.c:(.text+0x69a): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x6b7): undefined reference to `glVertex3f'
drawprims.c:(.text+0x6ca): undefined reference to `glEnd'
/tmp/ccZv0XXO.o: In function `drawplayerIcon':
drawprims.c:(.text+0x706): undefined reference to `glColor3f'
drawprims.c:(.text+0x712): undefined reference to `glBegin'
drawprims.c:(.text+0x728): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x747): undefined reference to `glVertex3f'
drawprims.c:(.text+0x75d): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x77c): undefined reference to `glVertex3f'
drawprims.c:(.text+0x792): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x7b1): undefined reference to `glVertex3f'
drawprims.c:(.text+0x7c7): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0x7e6): undefined reference to `glVertex3f'
drawprims.c:(.text+0x7eb): undefined reference to `glEnd'
/tmp/ccZv0XXO.o: In function `glBlitOnScreen':
drawprims.c:(.text+0x7ff): undefined reference to `glMatrixMode'
drawprims.c:(.text+0x804): undefined reference to `glPushMatrix'
drawprims.c:(.text+0x809): undefined reference to `glLoadIdentity'
drawprims.c:(.text+0x815): undefined reference to `glMatrixMode'
drawprims.c:(.text+0x81a): undefined reference to `glPushMatrix'
drawprims.c:(.text+0x81f): undefined reference to `glLoadIdentity'
drawprims.c:(.text+0x832): undefined reference to `glBindTexture'
drawprims.c:(.text+0x851): undefined reference to `glColor3f'
drawprims.c:(.text+0x85d): undefined reference to `glBegin'
drawprims.c:(.text+0x871): undefined reference to `glTexCoord2i'
drawprims.c:(.text+0x890): undefined reference to `glVertex3f'
drawprims.c:(.text+0x8a4): undefined reference to `glTexCoord2i'
drawprims.c:(.text+0x8c3): undefined reference to `glVertex3f'
drawprims.c:(.text+0x8d7): undefined reference to `glTexCoord2i'
drawprims.c:(.text+0x8f6): undefined reference to `glVertex3f'
drawprims.c:(.text+0x90a): undefined reference to `glTexCoord2i'
drawprims.c:(.text+0x929): undefined reference to `glVertex3f'
drawprims.c:(.text+0x92e): undefined reference to `glEnd'
drawprims.c:(.text+0x933): undefined reference to `glPopMatrix'
drawprims.c:(.text+0x93f): undefined reference to `glMatrixMode'
drawprims.c:(.text+0x944): undefined reference to `glPopMatrix'
drawprims.c:(.text+0x950): undefined reference to `glMatrixMode'
/tmp/ccZv0XXO.o: In function `drawUprightProp':
drawprims.c:(.text+0xa0c): undefined reference to `glBegin'
drawprims.c:(.text+0xa22): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xa58): undefined reference to `glVertex3f'
drawprims.c:(.text+0xa6e): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xaa7): undefined reference to `glVertex3f'
drawprims.c:(.text+0xabd): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xaf9): undefined reference to `glVertex3f'
drawprims.c:(.text+0xb0f): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xb48): undefined reference to `glVertex3f'
drawprims.c:(.text+0xb4d): undefined reference to `glEnd'
/tmp/ccZv0XXO.o: In function `drawSimpleTree':
drawprims.c:(.text+0xb83): undefined reference to `glBegin'
drawprims.c:(.text+0xb99): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xbba): undefined reference to `glVertex3f'
drawprims.c:(.text+0xbd0): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xbf4): undefined reference to `glVertex3f'
drawprims.c:(.text+0xc0a): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xc31): undefined reference to `glVertex3f'
drawprims.c:(.text+0xc47): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xc6b): undefined reference to `glVertex3f'
drawprims.c:(.text+0xc81): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xca2): undefined reference to `glVertex3f'
drawprims.c:(.text+0xcb8): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xcdc): undefined reference to `glVertex3f'
drawprims.c:(.text+0xcf2): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xd19): undefined reference to `glVertex3f'
drawprims.c:(.text+0xd2f): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xd53): undefined reference to `glVertex3f'
drawprims.c:(.text+0xd69): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xd8d): undefined reference to `glVertex3f'
drawprims.c:(.text+0xda3): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xdca): undefined reference to `glVertex3f'
drawprims.c:(.text+0xde0): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xe0a): undefined reference to `glVertex3f'
drawprims.c:(.text+0xe20): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xe47): undefined reference to `glVertex3f'
drawprims.c:(.text+0xe5d): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xe81): undefined reference to `glVertex3f'
drawprims.c:(.text+0xe97): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xebe): undefined reference to `glVertex3f'
drawprims.c:(.text+0xed4): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xefe): undefined reference to `glVertex3f'
drawprims.c:(.text+0xf14): undefined reference to `glTexCoord2f'
drawprims.c:(.text+0xf3b): undefined reference to `glVertex3f'
drawprims.c:(.text+0xf40): undefined reference to `glEnd'
/tmp/ccVoYwed.o: In function `LoadGLTextures':
textures.c:(.text+0x19d): undefined reference to `glGenTextures'
textures.c:(.text+0x217): undefined reference to `SDL_RWFromFile'
textures.c:(.text+0x227): undefined reference to `SDL_LoadBMP_RW'
textures.c:(.text+0x255): undefined reference to `glBindTexture'
textures.c:(.text+0x271): undefined reference to `glTexParameteri'
textures.c:(.text+0x2c3): undefined reference to `glTexImage2D'
textures.c:(.text+0x322): undefined reference to `SDL_FreeSurface'
/tmp/ccJCPn6B.o: In function `tilebychar':
maps.c:(.text+0x1e): undefined reference to `glBindTexture'
maps.c:(.text+0x3d): undefined reference to `glNormal3f'
maps.c:(.text+0x53): undefined reference to `glTexCoord2f'
maps.c:(.text+0x73): undefined reference to `glBindTexture'
maps.c:(.text+0x7f): undefined reference to `glBegin'
maps.c:(.text+0x9e): undefined reference to `glColor3f'
maps.c:(.text+0xeb): undefined reference to `glEnd'
maps.c:(.text+0x10c): undefined reference to `glBindTexture'
maps.c:(.text+0x12b): undefined reference to `glColor3f'
maps.c:(.text+0x18a): undefined reference to `glBindTexture'
maps.c:(.text+0x196): undefined reference to `glBegin'
maps.c:(.text+0x1b5): undefined reference to `glColor3f'
maps.c:(.text+0x202): undefined reference to `glEnd'
maps.c:(.text+0x223): undefined reference to `glBindTexture'
maps.c:(.text+0x22f): undefined reference to `glBegin'
maps.c:(.text+0x24e): undefined reference to `glColor3f'
maps.c:(.text+0x265): undefined reference to `glEnd'
maps.c:(.text+0x286): undefined reference to `glBindTexture'
maps.c:(.text+0x292): undefined reference to `glBegin'
maps.c:(.text+0x2b1): undefined reference to `glColor3f'
maps.c:(.text+0x2da): undefined reference to `glEnd'
maps.c:(.text+0x2fb): undefined reference to `glBindTexture'
maps.c:(.text+0x31a): undefined reference to `glColor3f'
maps.c:(.text+0x34d): undefined reference to `glBindTexture'
maps.c:(.text+0x36c): undefined reference to `glColor3f'
maps.c:(.text+0x394): undefined reference to `glBindTexture'
maps.c:(.text+0x3cd): undefined reference to `glBindTexture'
/tmp/ccJCPn6B.o: In function `set_spot_light':
maps.c:(.text+0x4a0): undefined reference to `glLightfv'
maps.c:(.text+0x4ba): undefined reference to `glLightfv'
maps.c:(.text+0x4d4): undefined reference to `glLightfv'
maps.c:(.text+0x4ee): undefined reference to `glLightfv'
maps.c:(.text+0x50a): undefined reference to `glLightf'
maps.c:(.text+0x526): undefined reference to `glLightf'
maps.c:(.text+0x542): undefined reference to `glLightf'
maps.c:(.text+0x55c): undefined reference to `glLightfv'
maps.c:(.text+0x56f): undefined reference to `glLightModelfv'
maps.c:(.text+0x57a): undefined reference to `glEnable'
maps.c:(.text+0x586): undefined reference to `glEnable'
/tmp/cczu8hA1.o: In function `draw_wfobj':
wfobj.c:(.text+0x424): undefined reference to `glBegin'
wfobj.c:(.text+0x446): undefined reference to `glTexCoord2f'
wfobj.c:(.text+0x4b9): undefined reference to `glVertex3f'
wfobj.c:(.text+0x4d0): undefined reference to `glEnd'
/tmp/ccDLKVuS.o: In function `initGL':
drawing.c:(.text+0x27): undefined reference to `glEnable'
drawing.c:(.text+0x33): undefined reference to `glShadeModel'
drawing.c:(.text+0x5b): undefined reference to `glClearColor'
drawing.c:(.text+0x65): undefined reference to `glClearDepth'
drawing.c:(.text+0x71): undefined reference to `glEnable'
drawing.c:(.text+0x7d): undefined reference to `glDepthFunc'
drawing.c:(.text+0x99): undefined reference to `glLightfv'
drawing.c:(.text+0xb5): undefined reference to `glLightfv'
drawing.c:(.text+0xd1): undefined reference to `glLightfv'
drawing.c:(.text+0xdd): undefined reference to `glEnable'
drawing.c:(.text+0x118): undefined reference to `glBlendFunc'
/tmp/ccDLKVuS.o: In function `drawGLScene':
drawing.c:(.text+0x192): undefined reference to `glClear'
drawing.c:(.text+0x19e): undefined reference to `glEnable'
drawing.c:(.text+0x1b2): undefined reference to `glBlendFunc'
drawing.c:(.text+0x1be): undefined reference to `glEnable'
drawing.c:(.text+0x1d1): undefined reference to `glFogfv'
drawing.c:(.text+0x1e6): undefined reference to `glFogf'
drawing.c:(.text+0x1fb): undefined reference to `glFogf'
drawing.c:(.text+0x210): undefined reference to `glFogf'
drawing.c:(.text+0x22d): undefined reference to `SDL_GL_SwapBuffers'
drawing.c:(.text+0x24a): undefined reference to `SDL_GL_SwapBuffers'
drawing.c:(.text+0x263): undefined reference to `glLoadIdentity'
drawing.c:(.text+0x28e): undefined reference to `glRotatef'
drawing.c:(.text+0x2b4): undefined reference to `glRotatef'
drawing.c:(.text+0x2cd): undefined reference to `glTranslatef'
drawing.c:(.text+0x408): undefined reference to `glPushMatrix'
drawing.c:(.text+0x40d): undefined reference to `glLoadIdentity'
drawing.c:(.text+0x417): undefined reference to `glPopMatrix'
drawing.c:(.text+0x41c): undefined reference to `SDL_GL_SwapBuffers'
drawing.c:(.text+0x42e): undefined reference to `SDL_GetTicks'
collect2: ld returned 1 exit status
make: *** [all] Error 1

```

---

### Post by xmorg on 2012-04-01
What? spam?

---

### Post by imachavel on 2012-04-01
lol kind of looks like your file compiled. Open gl project eh? Working on video library api? Hey, I don't know what is up with your updates, try rebooting the computer, and from grub selecting the oldest kernel, should be kind of an equivalent to windows system restore or roll back mode. 

also, I promise not to try and take credit for your open gl project, but to test your code in c, show me the code in the files, and names of file. I will use text editor to save each file, in a folder if need be so it's seperated from other files, and then will compile each file:

gcc -o example example.c

then will open the main compiled input file with

./mainfileexample.c

do you have all the color panels coded in already? Let's get started

---

### Post by xmorg on 2012-04-02
> **imachavel said:**
> lol kind of looks like your file compiled. Open gl project eh? Working on video library api? Hey, I don't know what is up with your updates, try rebooting the computer, and from grub selecting the oldest kernel, should be kind of an equivalent to windows system restore or roll back mode. 

also, I promise not to try and take credit for your open gl project, but to test your code in c, show me the code in the files, and names of file. I will use text editor to save each file, in a folder if need be so it's seperated from other files, and then will compile each file:

gcc -o example example.c

then will open the main compiled input file with

./mainfileexample.c

do you have all the color panels coded in already? Let's get started

Hi thanks for responding.
Here is a fairly recent snapshot   
[http://www.cooperlabs.net/packages/spearfall.tar.gz](http://www.cooperlabs.net/packages/spearfall.tar.gz)

I use a makefile which i primarily just type "make"  from freebsd to get it to compile, and also it was working fine with linux a few days ago.
the only libs it really uses are SDL, GL, and GLU
Oh yea, it DID compile but did not link :p

---

### Post by imachavel on 2012-04-02
I don't know if I'm doing this right, but I got an error when I tried to compile the makefile:


cc -o spearfall -lGL -lGLU -lm
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

like I said I'm not too familiar with c++, not sure if I'm compiling it right but I got that error. Don't know if I have all the libraries downloaded, but sdl? I have that one. Recently downloaded it for a project I was trying out.

---

### Post by xmorg on 2012-04-02
> **imachavel said:**
> I don't know if I'm doing this right, but I got an error when I tried to compile the makefile:


cc -o spearfall -lGL -lGLU -lm
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

like I said I'm not too familiar with c++, not sure if I'm compiling it right but I got that error. Don't know if I have all the libraries downloaded, but sdl? I have that one. Recently downloaded it for a project I was trying out.

are you compiling any files? try this.
gcc -o spearfall -lGL -lGLU -lm `sdl-config --cflags --libs` Main.c drawprims.c textures.c maps.c wfobj.c datafile.c drawing.c movement.c

Edit: or what if you just typed "make" from the spearfall directory?  You should only need GL, GLU, SDL but of course you need gcc/ and all required headers libs, etc :)

---

### Post by imachavel on 2012-04-02
gcc -o spearfall -lGL -lGLU -lm `sdl-config --cflags --libs` Main.c drawprims.c textures.c maps.c wfobj.c datafile.c drawing.c movement.c
/tmp/cc0gsAjD.o: In function `main':
Main.c:(.text+0x112): undefined reference to `SDL_Init'
Main.c:(.text+0x11b): undefined reference to `SDL_GetError'
Main.c:(.text+0x147): undefined reference to `SDL_GetVideoInfo'
Main.c:(.text+0x157): undefined reference to `SDL_GetError'
Main.c:(.text+0x1d6): undefined reference to `SDL_GL_SetAttribute'
Main.c:(.text+0x200): undefined reference to `SDL_SetVideoMode'

Main.c:(.text+0x931): undefined reference to `glLoadIdentity'
/tmp/cc8TWU2B.o: In function `drawHFace':
drawing.c:(.text+0x42e): undefined reference to `SDL_GetTicks'
collect2: ld returned 1 exit status


unless I have the same broken packages, then you wrote the code incorrectly. Sorry. Or possibly a package dependency that doesn't exist? I'm no opengl master, my sdl file is sitting in downloads as:

sdl-1.2.15-1.src.rpm

I thought it'd be enough. Anyway help you troubleshoot anything?(btw, had to remove some of the syntax return as ubuntu forums clipped my post) Btw, this would be your exit status would it not?:

Main.c: In function &#8216;main&#8217;:

---

### Post by xmorg on 2012-04-02
> **imachavel said:**
> gcc -o spearfall -lGL -lGLU -lm `sdl-config --cflags --libs` Main.c drawprims.c textures.c maps.c wfobj.c datafile.c drawing.c movement.c
/tmp/cc0gsAjD.o: In function `main':
Main.c:(.text+0x112): undefined reference to `SDL_Init'
Main.c:(.text+0x11b): undefined reference to `SDL_GetError'
Main.c:(.text+0x147): undefined reference to `SDL_GetVideoInfo'
Main.c:(.text+0x157): undefined reference to `SDL_GetError'
Main.c:(.text+0x1d6): undefined reference to `SDL_GL_SetAttribute'
Main.c:(.text+0x200): undefined reference to `SDL_SetVideoMode'

Main.c:(.text+0x931): undefined reference to `glLoadIdentity'
/tmp/cc8TWU2B.o: In function `drawHFace':
drawing.c:(.text+0x42e): undefined reference to `SDL_GetTicks'
collect2: ld returned 1 exit status


unless I have the same broken packages, then you wrote the code incorrectly. Sorry. Or possibly a package dependency that doesn't exist? I'm no opengl master, my sdl file is sitting in downloads as:

sdl-1.2.15-1.src.rpm

I thought it'd be enough. Anyway help you troubleshoot anything?(btw, had to remove some of the syntax return as ubuntu forums clipped my post) Btw, this would be your exit status would it not?:

Main.c: In function ‘main’:

If you dont mind, can you try this package?
[http://www.cooperlabs.net/packages/sdldf.tar.gz](http://www.cooperlabs.net/packages/sdldf.tar.gz)

This is another project of mine with a similar makefile but has no openGL only SDL.  this one makes just fine on ubuntu.  This leads me to believe that its the OpenGL or mesa thats somehow messed up by the update.

Again, i had a binary that did build and run only a few days ago that i build using this makefile.  I remember because my camera was running around in the dark because i didnt add enough ambient light.

---

### Post by mc4man on 2012-04-02
Maybe something like 
gcc -o spearfall  Main.c drawprims.c textures.c maps.c wfobj.c datafile.c drawing.c movement.c -lGL -lGLU -lm `sdl-config --cflags --libs`

---

### Post by xmorg on 2012-04-07
> **mc4man said:**
> Maybe something like 
gcc -o spearfall  Main.c drawprims.c textures.c maps.c wfobj.c datafile.c drawing.c movement.c -lGL -lGLU -lm `sdl-config --cflags --libs`

Tried it and got the same results.  

I know this is free software so I don,t have any right to complain, but, this is a showstopper for me.  I primarily use my laptop for skype and making little programs to experiment with code.  IT worked before it doesn't work now.  I am linking to the libraries and there is nothing in the code that says the libraries are not found now.  OpenGL programs still work but they do not build.


:(

---

