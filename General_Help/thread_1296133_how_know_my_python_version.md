---
title: "how know my python version?"
date: 2009-10-20
forum: General Help
---

### Post by pixrael on 2009-10-20
ok i know i know this maybe very easy question so sorry for that but im newbie in linux, 

im compiling blender so im getting an error:
source/blender/blenkernel/intern/node.c:31:20: error: Python.h: No such file or directory

i think i found how to solve the above error [http://bugs.lunar-linux.org/view.php?id=368](http://bugs.lunar-linux.org/view.php?id=368)

but i dont know my version of python, how can i know my version? using  the terminal or any other way...

---

### Post by diesch on 2009-10-20
> **pixrael said:**
> ok i know i know this maybe very easy question so sorry for that but im newbie in linux, 

im compiling blender so im getting an error:
source/blender/blenkernel/intern/node.c:31:20: error: Python.h: No such file or directory


Install the package python-dev

> **pixrael said:**
> 
but i dont know my version of python, how can i know my version? using  the terminal or any other way...

Run ```
python --version
``` on the command line

---

### Post by Giblet5 on 2009-10-20
+1 on the python-dev suggestion, but if you just can't do that for some reason, this will get you in the ballpark.

On Ubuntu ```
ls -l /usr/bin/python*

lrwxrwxrwx 1 root root       9 2009-10-13 08:48 /usr/bin/python -> python2.6
lrwxrwxrwx 1 root root       9 2009-10-13 08:48 /usr/bin/python2 -> python2.6
-rwxr-xr-x 1 root root 2554064 2009-10-13 13:45 /usr/bin/python2.6
```

or something similar. So, what's /usr/bin/python linked to?

---

### Post by philinux on 2009-10-20
> **pixrael said:**
> ok i know i know this maybe very easy question so sorry for that but im newbie in linux, 

im compiling blender so im getting an error:
source/blender/blenkernel/intern/node.c:31:20: error: Python.h: No such file or directory

i think i found how to solve the above error [http://bugs.lunar-linux.org/view.php?id=368](http://bugs.lunar-linux.org/view.php?id=368)

but i dont know my version of python, how can i know my version? using  the terminal or any other way...

Any reason not to install the version in synaptic?
 apt-cache policy blender
blender:
    Candidate: 2.48a+dfsg-1ubuntu3

---

### Post by pixrael on 2009-10-20
thanks a lot, 

the command "python --version" runs perfect! xD

i have already installed Python 2.5.2

before know the "python --version" i tryed install the python 2.5 so ubuntu tells i was already installed :D  but thank u a lot i really wanted know that command

diesch i just download and install the python-dev and when i run scons to compile blender the error is still there maybe i have to do this  solution [http://bugs.lunar-linux.org/view.php?id=368](http://bugs.lunar-linux.org/view.php?id=368) but to be honest i dont know where is that BUILD file

---

### Post by pixrael on 2009-10-20
ok, i found the linux2-config.py  in the python version i changed to 2.5.2 and the error still appears, maybe i need to upgrade python to that version??? the 3.1

```

LCGDIR = '../lib/linux2'
LIBDIR = "${LCGDIR}"

BF_PYTHON = '/usr'
BF_PYTHON_LIBPATH = '${BF_PYTHON}/lib'
**BF_PYTHON_VERSION = '3.1'**
WITH_BF_STATICPYTHON = False
BF_PYTHON_INC = '${BF_PYTHON}/include/python${BF_PYTHON_VERSION}'
BF_PYTHON_BINARY = '${BF_PYTHON}/bin/python${BF_PYTHON_VERSION}'
BF_PYTHON_LIB = 'python${BF_PYTHON_VERSION}' #BF_PYTHON+'/lib/python'+BF_PYTHON$
BF_PYTHON_LINKFLAGS = ['-Xlinker', '-export-dynamic']
BF_PYTHON_LIB_STATIC = '${BF_PYTHON}/lib/libpython${BF_PYTHON_VERSION}.a'

WITH_BF_OPENAL = True
WITH_BF_STATICOPENAL = False
BF_OPENAL = '/usr'
BF_OPENAL_INC = '${BF_OPENAL}/include'
BF_OPENAL_LIB = 'openal'
BF_OPENAL_LIB_STATIC = '${BF_OPENAL}/lib/libopenal.a'

BF_CXX = '/usr'
WITH_BF_STATICCXX = False
BF_CXX_LIB_STATIC = '${BF_CXX}/lib/libstdc++.a'

BF_LIBSAMPLERATE = '/usr'
BF_LIBSAMPLERATE_INC = '${BF_LIBSAMPLERATE}/include'
BF_LIBSAMPLERATE_LIB = 'samplerate'
BF_LIBSAMPLERATE_LIBPATH = '${BF_LIBSAMPLERATE}/lib'

WITH_BF_JACK = False
BF_JACK = '/usr'
BF_JACK_INC = '${BF_JACK}/include/jack'
BF_JACK_LIB = 'jack'
BF_JACK_LIBPATH = '${BF_JACK}/lib'

WITH_BF_SNDFILE = False
BF_SNDFILE = '/usr'
BF_SNDFILE_INC = '${BF_SNDFILE}/include/sndfile'
BF_SNDFILE_LIB = 'sndfile'
BF_SNDFILE_LIBPATH = '${BF_SNDFILE}/lib'

WITH_BF_SDL = True
BF_SDL = '/usr' #$(shell sdl-config --prefix)
BF_SDL_INC = '${BF_SDL}/include/SDL' #$(shell $(BF_SDL)/bin/sdl-config --cflags)
BF_SDL_LIB = 'SDL' #BF_SDL #$(shell $(BF_SDL)/bin/sdl-config --libs) -lSDL_mixer

WITH_BF_OPENEXR = True
WITH_BF_STATICOPENEXR = False
BF_OPENEXR = '/usr'
# when compiling with your own openexr lib you might need to set...
# BF_OPENEXR_INC = '${BF_OPENEXR}/include/OpenEXR ${BF_OPENEXR}/include'

BF_OPENEXR_INC = '${BF_OPENEXR}/include/OpenEXR'
BF_OPENEXR_LIB = 'Half IlmImf Iex Imath '

```

---

### Post by pixrael on 2009-10-20
heeeey it compiles!!!! xD the thing is i needed to change 
from BF_PYTHON_VERSION '3.1'
to BF_PYTHON_VERSION '2.5'

and **not** to BF_PYTHON_VERSION '2.5..2'

that was my mistake

---

