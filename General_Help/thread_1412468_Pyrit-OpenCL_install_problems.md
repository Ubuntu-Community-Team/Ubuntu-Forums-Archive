---
title: "Pyrit-OpenCL install problems"
date: 2010-02-21
forum: General Help
---

### Post by rockyrobin on 2010-02-21
I'm trying to compile and install the OpenCL plugin for pyrit but am having a nightmare to get this working. The main pyrit installed fine with no errors but the plugin is a nightmare.

I've followed the instructions to install ATI's Stream 2.01 SDK to the best of my ability but I think am stuck at how to edit the setup.py file included in Pyrit-OpenCL.

My env is:-
```
chris@chris-desktop:~$ env
ORBIT_SOCKETDIR=/tmp/orbit-chris
SSH_AGENT_PID=1640
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=276611d807d826819121088f4b71f7b6-1266712885.8670-666534942
GTK_RC_FILES=/etc/gtk/gtkrc:/home/chris/.gtkrc-1.2-gnome2
WINDOWID=4197889
GTK_MODULES=canberra-gtk-module
USER=chris
LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
LIBGL_DRIVERS_PATH=/usr/lib/dri
ATISTREAMSDKSAMPLESROOT=/home/chris/ati-stream-sdk-v2.01-lnx32
GNOME_KEYRING_SOCKET=/tmp/keyring-hLZaa6/socket
SSH_AUTH_SOCK=/tmp/keyring-hLZaa6/socket.ssh
SESSION_MANAGER=local/chris-desktop:@/tmp/.ICE-unix/1598,unix/chris-desktop:/tmp/.ICE-unix/1598
ATISTREAMSDKROOT=/home/chris/ati-stream-sdk-v2.01-lnx32
USERNAME=chris
DESKTOP_SESSION=gnome
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/chris
GDM_KEYBOARD_LAYOUT=gb
LANG=en_GB.UTF-8
GDM_LANG=en_GB.UTF-8
GDMSESSION=gnome
SPEECHD_PORT=7560
SHLVL=1
HOME=/home/chris
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=chris
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-uJAzpSskWH,guid=67d29c661078102965b9f8ad4b808135
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/var/run/gdm/auth-for-chris-id88Ss/database
COLORTERM=gnome-terminal
_=/usr/bin/env
chris@chris-desktop:~$ 

```

The setup.py looks like this:
```
#!/usr/bin/env python
# -*- coding: UTF-8 -*-
#
#    Copyright 2008, Lukas Lueg, lukas.lueg@gmail.com
#
#    This file is part of Pyrit.
#
#    Pyrit is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    Pyrit is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with Pyrit.  If not, see <http://www.gnu.org/licenses/>.


from distutils.core import setup, Extension
from distutils.command.build_ext import build_ext
from distutils.command.clean import clean
import os
import re
import subprocess
import sys
import zlib

OPENCL_INC_DIRS = []
for path in ('/home/chris/ati-stream-sdk-v2.01-lnx32'):
    if os.path.exists(path):
        OPENCL_INC_DIRS.append(path)
        break
else:
    print >>sys.stderr, "The headers required to build the OpenCL-kernel were not found. Trying to continue anyway..."


try:
    svn_info = subprocess.Popen(('svn', 'info'), stdout=subprocess.PIPE).stdout.read()
    version_string = '0.2.4 (svn r%i)' % int(re.compile('Revision: ([0-9]*)').findall(svn_info)[0])
except:
    version_string = '0.2.4'
EXTRA_COMPILE_ARGS = ['-DVERSION="%s"' % version_string]


class GPUBuilder(build_ext):
    def run(self):
        f = open("_cpyrit_opencl.h", 'rb')
        header = f.read()
        f.close()
        f = open("_cpyrit_oclkernel.cl", 'rb')
        kernel = f.read()
        f.close()
        oclkernel_program = header + '\n' + kernel + '\x00'
        oclkernel_packed = zlib.compress(oclkernel_program)        
        f = open("_cpyrit_oclkernel.cl.h", 'wb')
        f.write("unsigned char oclkernel_packedprogram[] = {")
        f.write(",".join(("0x%02X%s" % (ord(c), "\n" if i % 16 == 0 else "") for i, c in enumerate(oclkernel_packed))))
        f.write("};\nsize_t oclkernel_size = %i;\n" % len(oclkernel_program))
        f.close()
        
        print "Building modules..."
        build_ext.run(self)


class GPUCleaner(clean):
    def _unlink(self, node):
        try:
            if os.path.isdir(node):
                os.rmdir(node)
            else:
                os.unlink(node)
        except OSError:
            pass
    
    def run(self):
        print "Removing temporary files and pre-built GPU-kernels..."
        try:
            for f in ('_cpyrit_oclkernel.cl.h',):
                self._unlink(f)
        except Exception, (errno, sterrno):
            print >>sys.stderr, "Exception while cleaning temporary files ('%s')" % sterrno
        clean.run(self)


opencl_extension = Extension('cpyrit._cpyrit_opencl',
                    libraries = ['ssl', 'OpenCL', 'z'],
                    sources = ['_cpyrit_opencl.c'],
                    include_dirs = OPENCL_INC_DIRS,
                    extra_compile_args = EXTRA_COMPILE_ARGS)

setup_args = dict(
        name = 'CPyrit-OpenCL',
        version = '0.2.4',
        description = 'GPU-accelerated attack against WPA-PSK authentication',
        license = 'GNU General Public License v3',
        author = 'Lukas Lueg',
        author_email = 'lukas.lueg@gmail.com',
        url = 'http://pyrit.googlecode.com',
        ext_modules = [opencl_extension],
        cmdclass = {'build_ext':GPUBuilder, 'clean':GPUCleaner},
        options = {'install':{'optimize':1},'bdist_rpm':{'requires':'Pyrit = 0.2.4-1'}}
        )
        
if __name__ == "__main__":
    setup(**setup_args)
```

And the output when I try to make the above is:-
```
chris@chris-desktop:~/Downloads/CPyrit-OpenCL-0.2.4$ python setup.py build
running build
running build_ext
Building modules...
building 'cpyrit._cpyrit_opencl' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/ -I/usr/include/python2.6 -c _cpyrit_opencl.c -o build/temp.linux-i686-2.6/_cpyrit_opencl.o -DVERSION="0.2.4"
_cpyrit_opencl.c:23:19: error: CL/cl.h: No such file or directory
_cpyrit_opencl.c:40: error: expected specifier-qualifier-list before ‘cl_context’
_cpyrit_opencl.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OpenCLDevCount’
_cpyrit_opencl.c:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cpyrit_opencl.c:51: error: expected ‘)’ before ‘error’
_cpyrit_opencl.c: In function ‘opencldev_init’:
_cpyrit_opencl.c:111: error: ‘cl_int’ undeclared (first use in this function)
_cpyrit_opencl.c:111: error: (Each undeclared identifier is reported only once
_cpyrit_opencl.c:111: error: for each function it appears in.)
_cpyrit_opencl.c:111: error: expected ‘;’ before ‘errcode’
_cpyrit_opencl.c:116: error: ‘OpenCLDevCount’ undeclared (first use in this function)
_cpyrit_opencl.c:123: error: ‘OpenCLDevice’ has no member named ‘dev_ctx’
_cpyrit_opencl.c:124: error: ‘OpenCLDevice’ has no member named ‘dev_prog’
_cpyrit_opencl.c:125: error: ‘OpenCLDevice’ has no member named ‘dev_kernel’
_cpyrit_opencl.c:126: error: ‘OpenCLDevice’ has no member named ‘dev_queue’
_cpyrit_opencl.c:129: error: ‘errcode’ undeclared (first use in this function)
_cpyrit_opencl.c:129: warning: implicit declaration of function ‘clGetDeviceInfo’
_cpyrit_opencl.c:129: error: ‘OpenCLDevices’ undeclared (first use in this function)
_cpyrit_opencl.c:129: error: ‘CL_DEVICE_NAME’ undeclared (first use in this function)
_cpyrit_opencl.c:130: error: ‘CL_SUCCESS’ undeclared (first use in this function)
_cpyrit_opencl.c:132: warning: implicit declaration of function ‘getCLresultMsg’
_cpyrit_opencl.c:132: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
_cpyrit_opencl.c:142: error: ‘OpenCLDevice’ has no member named ‘dev_ctx’
_cpyrit_opencl.c:142: warning: implicit declaration of function ‘clCreateContext’
_cpyrit_opencl.c:145: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
_cpyrit_opencl.c:149: error: ‘OpenCLDevice’ has no member named ‘dev_queue’
_cpyrit_opencl.c:149: warning: implicit declaration of function ‘clCreateCommandQueue’
_cpyrit_opencl.c:149: error: ‘OpenCLDevice’ has no member named ‘dev_ctx’
_cpyrit_opencl.c:152: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
_cpyrit_opencl.c:156: error: ‘OpenCLDevice’ has no member named ‘dev_prog’
_cpyrit_opencl.c:156: warning: implicit declaration of function ‘clCreateProgramWithSource’
_cpyrit_opencl.c:156: error: ‘OpenCLDevice’ has no member named ‘dev_ctx’
_cpyrit_opencl.c:159: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
_cpyrit_opencl.c:163: warning: implicit declaration of function ‘clBuildProgram’
_cpyrit_opencl.c:163: error: ‘OpenCLDevice’ has no member named ‘dev_prog’
_cpyrit_opencl.c:167: warning: implicit declaration of function ‘clGetProgramBuildInfo’
_cpyrit_opencl.c:167: error: ‘OpenCLDevice’ has no member named ‘dev_prog’
_cpyrit_opencl.c:167: error: ‘CL_PROGRAM_BUILD_LOG’ undeclared (first use in this function)
_cpyrit_opencl.c:168: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
_cpyrit_opencl.c:172: error: ‘OpenCLDevice’ has no member named ‘dev_kernel’
_cpyrit_opencl.c:172: warning: implicit declaration of function ‘clCreateKernel’
_cpyrit_opencl.c:172: error: ‘OpenCLDevice’ has no member named ‘dev_prog’
_cpyrit_opencl.c:175: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
_cpyrit_opencl.c: In function ‘opencldev_dealloc’:
_cpyrit_opencl.c:186: error: ‘OpenCLDevice’ has no member named ‘dev_queue’
_cpyrit_opencl.c:187: warning: implicit declaration of function ‘clReleaseCommandQueue’
_cpyrit_opencl.c:187: error: ‘OpenCLDevice’ has no member named ‘dev_queue’
_cpyrit_opencl.c:188: error: ‘OpenCLDevice’ has no member named ‘dev_kernel’
_cpyrit_opencl.c:189: warning: implicit declaration of function ‘clReleaseKernel’
_cpyrit_opencl.c:189: error: ‘OpenCLDevice’ has no member named ‘dev_kernel’
_cpyrit_opencl.c:190: error: ‘OpenCLDevice’ has no member named ‘dev_prog’
_cpyrit_opencl.c:191: warning: implicit declaration of function ‘clReleaseProgram’
_cpyrit_opencl.c:191: error: ‘OpenCLDevice’ has no member named ‘dev_prog’
_cpyrit_opencl.c:192: error: ‘OpenCLDevice’ has no member named ‘dev_ctx’
_cpyrit_opencl.c:193: warning: implicit declaration of function ‘clReleaseContext’
_cpyrit_opencl.c:193: error: ‘OpenCLDevice’ has no member named ‘dev_ctx’
_cpyrit_opencl.c: In function ‘cpyrit_listDevices’:
_cpyrit_opencl.c:208: error: ‘OpenCLDevCount’ undeclared (first use in this function)
_cpyrit_opencl.c:211: error: ‘OpenCLDevices’ undeclared (first use in this function)
_cpyrit_opencl.c:211: error: ‘CL_DEVICE_NAME’ undeclared (first use in this function)
_cpyrit_opencl.c:212: error: ‘CL_DEVICE_VENDOR’ undeclared (first use in this function)
_cpyrit_opencl.c: At top level:
_cpyrit_opencl.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘calc_pmklist’
_cpyrit_opencl.c: In function ‘cpyrit_solve’:
_cpyrit_opencl.c:369: warning: implicit declaration of function ‘calc_pmklist’
_cpyrit_opencl.c:373: error: ‘CL_SUCCESS’ undeclared (first use in this function)
_cpyrit_opencl.c:376: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
_cpyrit_opencl.c: In function ‘init_cpyrit_opencl’:
_cpyrit_opencl.c:464: warning: implicit declaration of function ‘clGetDeviceIDs’
_cpyrit_opencl.c:464: error: ‘CL_DEVICE_TYPE_GPU’ undeclared (first use in this function)
_cpyrit_opencl.c:464: error: ‘OpenCLDevCount’ undeclared (first use in this function)
_cpyrit_opencl.c:464: error: ‘CL_SUCCESS’ undeclared (first use in this function)
_cpyrit_opencl.c:470: error: ‘OpenCLDevices’ undeclared (first use in this function)
_cpyrit_opencl.c:470: error: ‘cl_device_id’ undeclared (first use in this function)
_cpyrit_opencl.c:470: error: expected expression before ‘)’ token
error: command 'gcc' failed with exit status 1
chris@chris-desktop:~/Downloads/CPyrit-OpenCL-0.2.4$
```

If anyone would be kind enough to offer me some help would be very grateful.

---

### Post by elect on 2010-12-12
Look here at the middle

[http://beta.ivancover.com/wiki/index.php/Pyrit_setup#OpenCL_.28Nvidia.2FAMD.2FCell.29](http://beta.ivancover.com/wiki/index.php/Pyrit_setup#OpenCL_.28Nvidia.2FAMD.2FCell.29)

---

### Post by elect on 2010-12-12
But my problem is

```
elect@elect-desktop:~/Scaricati/pyrit_svn/cpyrit_calpp$ python setup.py build
running build
running build_ext
Building modules...
elect@elect-desktop:~/Scaricati/pyrit_svn/cpyrit_calpp$ sudo python setup.py install
unavailable enviroment variable ATISTREAMSDKROOT
Traceback (most recent call last):
  File "setup.py", line 35, in <module>
    CALPP_INC_DIR = os.environ['ATISTREAMSDKROOT']
  File "/usr/lib/python2.6/UserDict.py", line 22, in __getitem__
    raise KeyError(key)
KeyError: 'ATISTREAMSDKROOT'
elect@elect-desktop:~/Scaricati/pyrit_svn/cpyrit_calpp$ echo $ATISTREAMSDKROOT
/ati-stream-sdk

```

---

### Post by speedbaron on 2010-12-29
If you downloaded the ati-stream-sdk; you find a ATI_Stream_SDK_Installation_Notes.pdf file.  In that file, it tells you to set those variables.

Here is the snippet:
++++++++++++++++++++++++
2.2 On Linux Systems
You must have root permissions to install this SDK. Also note that the latest version of the ATI
Catalyst™ driver must be installed separately.

1. Untar the SDK to a location of your choice.
For 32-bit systems, unzip the .tgz file by entering
tar -xvzf ati-stream-sdk-v2.2-lnx32.tgz.
For 64-bit systems, unzip the .tgz file by entering
tar -xvzf ati-stream-sdk-v2.2-lnx64.tgz.

2. **Set the environment variable ATISTREAMSDKROOT**:
export ATISTREAMSDKROOT=<location where sdk is extracted>

3. **Set the environment variable ATISTREAMSDKSAMPLESROOT**:
export ATISTREAMSDKSAMPLESROOT=<location where sdk is extracted>

4. Set the library path LD_LIBRARY_PATH.
– **For 32-bit systems**:
export LD_LIBRARY_PATH=$ATISTREAMSDKROOT/lib/x86:$LD_LIBRARY_PATH
– **For 64-bit systems**:
export LD_LIBRARY_PATH=$ATISTREAMSDKROOT/lib/x86_64:$LD_LIBRARY_PATH
– **For the 32-bit SDK to run on 64-bit systems**:
export LD_LIBRARY_PATH=$ATISTREAMSDKROOT/lib/x86:$ATISTREAMSDKROOT/lib/x86_64:$LD_LIBRARY_PATH

5. **You must register the OpenCL ICD**; otherwise, samples and other applications will fail to
execute if this is not done. To register the ICD, enter (as root):
cd /
tar xfz icd-registration.tgz
If this is not done, samples and other applications do not execute, and a
CL_PLATFORM_NOT_FOUND_KHR (-1001) error is issued.
+++++++++++++++++++++++++++

---

