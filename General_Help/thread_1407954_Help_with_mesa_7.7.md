---
title: "Help with mesa 7.7"
date: 2010-02-15
forum: General Help
---

### Post by FirebirdTA01 on 2010-02-15
Compiling mesa 7.7 linux-cell driver on ps3 running ubuntu 9.10

./configure comes out with no errors but when i run:
make linux-cell
it goes for a while but then returns with error:

make[6]: Entering directory `/home/bandit/Projects/Mesa-7.7/src/gallium/state_trackers/glx/xlib'
gcc -c -I. -I../../../../../src/gallium/include -I../../../../../src/gallium/auxiliary -I../../../../../src/gallium/drivers -I/src/gallium/include -I/src/gallium/auxiliary -I/src/gallium/drivers -I../../../../../include -I../../../../../src/mesa -O3 -Wall -Winline -Wmissing-prototypes -fPIC -m32 -std=c99 -mabi=altivec -maltivec -I. -I/opt/cell/sdk/usr/include -DGALLIUM_CELL -DUSE_XSHM -D_BSD_SOURCE -D_SVID_SOURCE glx_api.c -o glx_api.o
In file included from glx_api.c:36:
xm_api.h:72:35: error: X11/extensions/XShm.h: No such file or directory
In file included from glx_api.c:36:
xm_api.h:337: error: expected specifier-qualifier-list before ‘XShmSegmentInfo’
glx_api.c: In function ‘register_with_display’:
glx_api.c:644: warning: unused variable ‘c’
glx_api.c: In function ‘glXQueryDrawable’:
glx_api.c:2076: error: ‘struct xmesa_buffer’ has no member named ‘TextureFormat’
glx_api.c:2079: error: ‘struct xmesa_buffer’ has no member named ‘TextureTarget’
glx_api.c:2082: error: ‘struct xmesa_buffer’ has no member named ‘TextureMipmap’
make[6]: *** [glx_api.o] Error 1
make[6]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src/gallium/state_trackers/glx/xlib'
make[5]: *** [subdirs] Error 1
make[5]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src/gallium/state_trackers/glx'
make[4]: *** [subdirs] Error 1
make[4]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src/gallium/state_trackers'
make[3]: *** [default] Error 1
make[3]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src/gallium'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/bandit/Projects/Mesa-7.7'
make: *** [linux-cell] Error 2

i need help... i think it may be because i need xorg-dev installed, i may be wrong about that though, but for some reason im running into dependency problems... ex:

bandit@ubuntu:~$ sudo apt-get install xorg-dev
[sudo] password for bandit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-dev: Depends: libxtst-dev but it is not going to be installed
E: Broken packages

then i run:

bandit@ubuntu:~$ sudo apt-get install libxtst-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxtst-dev: Depends: libxext-dev but it is not going to be installed
               Depends: libxi-dev but it is not going to be installed
E: Broken packages

and i know thats not true cause if i run apt-get for those missing dependencies it tells me that they're already installed and latest versions... im really confused and havent been on linux for too long so somebody please help me

---

