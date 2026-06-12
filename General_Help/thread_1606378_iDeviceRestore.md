---
title: "iDeviceRestore"
date: 2010-10-26
forum: General Help
---

### Post by icehammer on 2010-10-26
So, here's what i'm trying to do.
[http://github.com/posixninja/idevicerestore]("http://github.com/posixninja/idevicerestore")

I got all the required libraries, as mentioned anyway, but when I try :

```
cmake ~/usbmuxd
```

I get :

```
-- Configuring usbmuxd v1.0.5-6-ge534cc5
-- Found PLIST 
-- Will build usbmuxd: YES
-- libusbmuxd will be built with protocol version 1 support
-- checking for module 'libusb-1.0>=1.0.3'
--   package 'libusb-1.0>=1.0.3' not found
USB_INCLUDE_DIR=USB_INCLUDE_DIR-NOTFOUND
USB_LIBRARY=USB_LIBRARY-NOTFOUND
CMake Error at Modules/LibFindMacros.cmake:74 (message):
  Required library USB NOT FOUND.

  Install the library (dev version) and try again.  If the library is already
  installed, use ccmake to set the missing variables manually.
Call Stack (most recent call first):
  Modules/FindUSB.cmake:40 (libfind_process)
  daemon/CMakeLists.txt:1 (find_package)


-- Configuring incomplete, errors occurred!

```

I do have all the libraries, and build-essential is complete as well :

```
apoorv@AC-ubuntu:~/usbmuxd$ sudo apt-get install build-essential libusb-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libusb-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

Help!

---

### Post by theShaggy on 2010-10-27
Look for the libusb dev file.  I had the same problem, but installing the libusb-1.0-0-dev package solved the issue.

---

### Post by icehammer on 2010-10-28
Awesome! That worked. Here's the next one now. (Sorry, i'm still a noob!)

```
make linux && sudo make install
gcc -o libirecovery.o -c src/libirecovery.c -g -I./include -lreadline -fPIC 
src/libirecovery.c: In function ‘irecv_send_buffer’:
src/libirecovery.c:436: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
src/libirecovery.c:436: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘long unsigned int’
gcc -o libirecovery.so libirecovery.o -g -shared -Wl,-soname,libirecovery.so -lusb-1.0
gcc -o irecovery src/irecovery.c -g -I./include -L. -lirecovery -lreadline
src/irecovery.c:23:31: error: readline/readline.h: No such file or directory
src/irecovery.c:24:30: error: readline/history.h: No such file or directory
src/irecovery.c: In function ‘parse_command’:
src/irecovery.c:52: warning: incompatible implicit declaration of built-in function ‘strdup’
src/irecovery.c:53: warning: initialization makes pointer from integer without a cast
src/irecovery.c:64: warning: initialization makes pointer from integer without a cast
src/irecovery.c:73: warning: initialization makes pointer from integer without a cast
src/irecovery.c:83: warning: initialization makes pointer from integer without a cast
src/irecovery.c: In function ‘init_shell’:
src/irecovery.c:117: warning: initialization makes pointer from integer without a cast
src/irecovery.c: In function ‘precommand_cb’:
src/irecovery.c:155: warning: incompatible implicit declaration of built-in function ‘strdup’
src/irecovery.c:156: warning: assignment makes pointer from integer without a cast
src/irecovery.c:159: warning: assignment makes pointer from integer without a cast
src/irecovery.c: In function ‘postcommand_cb’:
src/irecovery.c:181: warning: incompatible implicit declaration of built-in function ‘strdup’
src/irecovery.c:182: warning: assignment makes pointer from integer without a cast
make: *** [linux] Error 1
```

Doesn't look like a dependency thing but more of a coding issue. Am I right?

---

### Post by theShaggy on 2010-10-28
Same thing - go to Synaptic and add all the readline development packages.

The one thing I'm learning lately (the first time I tried to compile this thing I spent HOURS trying to sort it out) is that the dev packages is pretty much Where It's At.

---

### Post by icehammer on 2010-10-28
Ok, I was missing one of them. So I got that, and this is the new error message.

```
gcc -o libirecovery.o -c src/libirecovery.c -g -I./include -lreadline -fPIC 
src/libirecovery.c: In function ‘irecv_send_buffer’:
src/libirecovery.c:436: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
src/libirecovery.c:436: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘long unsigned int’
gcc -o libirecovery.so libirecovery.o -g -shared -Wl,-soname,libirecovery.so -lusb-1.0
gcc -o irecovery src/irecovery.c -g -I./include -L. -lirecovery -lreadline
#cp libirecovery.so /usr/local/lib/libirecovery.so
cp libirecovery.dylib /usr/local/lib/libirecovery.dylib
cp: cannot stat `libirecovery.dylib': No such file or directory
make: *** [install] Error 1

```

---

### Post by theShaggy on 2010-10-28
That one is easy.  Open up the Makefile and comment out (#) the .dylib in the "Install" section.

When you get it working, let me know how it goes.  I can't seem to update my phone, I am told that it can't transfer the "iBEC" to my device.

---

### Post by icehammer on 2010-10-28
Do you have "libusbmuxd" installed? Apparently I dont and its not in the repo either.

edit: Nevermind. Figured it out. Brainfart.

---

### Post by icehammer on 2010-10-28
```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for libimobiledevice... yes
checking for libplist... yes
checking for libzip... yes
checking for libcurl... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands
apoorv@AC-ubuntu:~/idevicerestore$ make && sudo make install
Making all in src
make[1]: Entering directory `/home/apoorv/idevicerestore/src'
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-idevicerestore.o -MD -MP -MF .deps/idevicerestore-idevicerestore.Tpo -c -o idevicerestore-idevicerestore.o `test -f 'idevicerestore.c' || echo './'`idevicerestore.c
idevicerestore.c: In function ‘main’:
idevicerestore.c:199: warning: format ‘%llu’ expects type ‘long long unsigned int’, but argument 2 has type ‘uint64_t’
mv -f .deps/idevicerestore-idevicerestore.Tpo .deps/idevicerestore-idevicerestore.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-common.o -MD -MP -MF .deps/idevicerestore-common.Tpo -c -o idevicerestore-common.o `test -f 'common.c' || echo './'`common.c
common.c: In function ‘write_file’:
common.c:43: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘size_t’
common.c:43: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘size_t’
common.c: In function ‘read_file’:
common.c:70: warning: incompatible implicit declaration of built-in function ‘malloc’
common.c:81: warning: incompatible implicit declaration of built-in function ‘free’
common.c: In function ‘debug_plist’:
common.c:95: warning: incompatible implicit declaration of built-in function ‘free’
mv -f .deps/idevicerestore-common.Tpo .deps/idevicerestore-common.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-tss.o -MD -MP -MF .deps/idevicerestore-tss.Tpo -c -o idevicerestore-tss.o `test -f 'tss.c' || echo './'`tss.c
tss.c: In function ‘tss_create_request’:
tss.c:85: warning: format ‘%qu’ expects type ‘long long unsigned int’, but argument 4 has type ‘uint64_t’
tss.c:85: warning: format ‘%qu’ expects type ‘long long unsigned int’, but argument 4 has type ‘uint64_t’
tss.c: In function ‘tss_send_request’:
tss.c:168: warning: call to ‘_curl_easy_setopt_err_write_callback’ declared with attribute warning: curl_easy_setopt expects a curl_write_callback argument for this option
mv -f .deps/idevicerestore-tss.Tpo .deps/idevicerestore-tss.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-img3.o -MD -MP -MF .deps/idevicerestore-img3.Tpo -c -o idevicerestore-img3.o `test -f 'img3.c' || echo './'`img3.c
mv -f .deps/idevicerestore-img3.Tpo .deps/idevicerestore-img3.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-ipsw.o -MD -MP -MF .deps/idevicerestore-ipsw.Tpo -c -o idevicerestore-ipsw.o `test -f 'ipsw.c' || echo './'`ipsw.c
mv -f .deps/idevicerestore-ipsw.Tpo .deps/idevicerestore-ipsw.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-normal.o -MD -MP -MF .deps/idevicerestore-normal.Tpo -c -o idevicerestore-normal.o `test -f 'normal.c' || echo './'`normal.c
mv -f .deps/idevicerestore-normal.Tpo .deps/idevicerestore-normal.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-dfu.o -MD -MP -MF .deps/idevicerestore-dfu.Tpo -c -o idevicerestore-dfu.o `test -f 'dfu.c' || echo './'`dfu.c
mv -f .deps/idevicerestore-dfu.Tpo .deps/idevicerestore-dfu.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-recovery.o -MD -MP -MF .deps/idevicerestore-recovery.Tpo -c -o idevicerestore-recovery.o `test -f 'recovery.c' || echo './'`recovery.c
recovery.c: In function ‘recovery_get_ecid’:
recovery.c:377: warning: passing argument 2 of ‘irecv_get_ecid’ from incompatible pointer type
/usr/local/include/libirecovery.h:112: note: expected ‘long long unsigned int *’ but argument is of type ‘uint64_t *’
mv -f .deps/idevicerestore-recovery.Tpo .deps/idevicerestore-recovery.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-restore.o -MD -MP -MF .deps/idevicerestore-restore.Tpo -c -o idevicerestore-restore.o `test -f 'restore.c' || echo './'`restore.c
mv -f .deps/idevicerestore-restore.Tpo .deps/idevicerestore-restore.Po
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I.     -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -MT idevicerestore-asr.o -MD -MP -MF .deps/idevicerestore-asr.Tpo -c -o idevicerestore-asr.o `test -f 'asr.c' || echo './'`asr.c
mv -f .deps/idevicerestore-asr.Tpo .deps/idevicerestore-asr.Po
gcc  -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/local/include -g -O2 -pthread -L/usr/local/lib -limobiledevice -lplist -lusbmuxd -lgthread-2.0 -lrt -lgnutls -ltasn1 -lglib-2.0   -lplist   -lzip -lz   -lcurl   -L/usr/local/lib -lirecovery -lusb-1.0  -o idevicerestore idevicerestore-idevicerestore.o idevicerestore-common.o idevicerestore-tss.o idevicerestore-img3.o idevicerestore-ipsw.o idevicerestore-normal.o idevicerestore-dfu.o idevicerestore-recovery.o idevicerestore-restore.o idevicerestore-asr.o  
/usr/bin/ld: cannot find -lirecovery
collect2: ld returned 1 exit status
make[1]: *** [idevicerestore] Error 1
make[1]: Leaving directory `/home/apoorv/idevicerestore/src'
make: *** [all-recursive] Error 1
```

I have no idea what this all means LOL.
I feel like an idiot. I should dual boot and get iTunes.

---

### Post by JIMIneitor on 2010-12-13
Ok, I just sorted out that error.

The thing is that idevicerestore needs some binary called irecovery, which is installed among libirecovery (pretty obvious huh?).

You need to make sure that libirecovery is installed correctly, without any errors, and type "sudo ldconfig" after it, then idevicerestore won't complain about it, and when you finish with "make install" in idevicerestore type "sudo ldconfig" again to make sure everything is laoded correctly

---

### Post by lt_gustavsen on 2010-12-15
Thanks everybody. I was able to compile the entire set of idevice tools  know after reading this thread. :D

I just followed the url in the first post and with all the additional suggestions here. I had to install libplist++1 swig with apt-get also.

I will try this in a few days when my wifes ipad enter the house, Have anyone upgraded to  ios 4.2.1 with idevicerestore?

---

### Post by lt_gustavsen on 2010-12-17
Just for the record. I was not able to restore the ipad to firmware 4.2.1.

I actually also installed those tools one more time and wrote down each step.

This was on 10.10 but I think it's close on 10.04
1. As an addition to the other apt-get's in the github readme 

```
sudo apt-get install libusb-1.0-0-dev libplist++1 swig libreadline-dev
```

in libimobiledevice/Makefile
comment/uncomment this lines  before make install
```

	cp libirecovery.so /usr/local/lib/libirecovery.so
#       cp libirecovery.dylib /usr/local/lib/libirecovery.dylib
        cp include/libirecovery.h /usr/local/include/libirecovery.h
        cp irecovery /usr/local/bin/irecovery
```


I was able to activate my ipad but to so I had to use the forked ideviceactivate from here
```
git clone git://github.com/boxingsquirrel/ideviceactivate.git
``` insted of the one described in the github readme.

And something is wrong with the udev rules so I ha best result when I run with **sudo**. 

As I described at top I was not able to upgrade to 4.2.1. 

Here is a typical log:
[PHP]sudo idevicerestore -e  iPad1,1_4.2.1_8C148_Restore.ipsw.1 
[sudo] password for ltg: 
Found device in Normal mode
Identified device as iPad1,1
Extracting BuildManifest from IPSW
ERROR: zip_name_locate: BuildManifesto.plist
Product Version: 4.2.1
Product Build: 8C148
Variant: Customer Erase Install (IPSW)
This restore will erase your device data.
Found ECID 1479633630711
Sending TSS request... received SHSH blobs
Extracting filesystem from IPSW
[==================================================] 100.0%
Entering recovery mode...
ERROR: Unable to reset auto-boot variable
ERROR: Unable to place device into recovery mode[/PHP]

I think the line above "ERROR: zip_name_locate: BuildManifesto.plist" is pretty strange. Since the file is actually called BuildManifest.plist in the ipsw file.
After this failure I could no longer talk to the ipad
[PHP]ideviceinfo |egrep "DeviceName|ActivationState|ProductVersion:"
usbmuxd_get_device_list: error opening socket![/PHP]

To get out of this and get the ipad back to normal I had to:
```
$ sudo irecovery  -s
Entering recovery mode, starting command prompt
> setenv auto-boot true
> saveenv
> reboot
```


In the end I gave up and was a afraid of destroying my wifes ipad so i upgraded it with itunes on windows :(

---

### Post by iPhoneNewbie on 2010-12-29
Hi guys!

I am a newbie. I want to use library imobiledevice 1.1.0 to restore iPhone 2G iOS 3.1.3 and iPhone 3GS 4.2.1. But i only restored iPhone 2G successfully. When i restore iPhone 3GS, it display message:

[SIZE=2][COLOR=Blue][B]Found device in Normal mode
GNUTLS ERROR: A TLS packet with unexpected length was received.[/B][/COLOR][/SIZE]

Can anyone help me?

And i want to ask another question? Can imobiledevice restore multiple iPhones at once. Because i want to try restore iPhone 2G and iPhone 3GS.

Thanks for your help!

---

### Post by theShaggy on 2010-12-30
Blows my mind that there hasn't been a solution to this problem, since the iDevicerestore git page has numerous people asking.

I can get this thing to put my phone in recovery mode, but then it can't send the iBEC.  For whatever reason, it refuses to work.

I THINK I have put my phone in DFU mode, but since I don't have iTunes, I don't know for sure.

If anyone has any idea how to get it to upload my iBEC?  I get this error:

Found device in Recovery mode
Identified device as iPhone1,2
Extracting BuildManifest from IPSW
Product Version: 3.1.3
Product Build: 7E18
Custom firmware requested. Disabled TSS request.
Variant: Customer Upgrade Install (IPSW)
This restore will update your device without loosing data.
Extracting filesystem from IPSW
[==================================================] 100.0%
Resetting recovery mode connection...
Extracting iBEC.n82ap.RELEASE.dfu
Sending iBEC (105844 bytes)...
ERROR: Unable to send iBEC component: Unable to upload data to device
ERROR: Unable to send iBEC to device.
ERROR: Unable to send iBEC
ERROR: Unable to place device into restore mode

---

### Post by iPhoneNewbie on 2010-12-30
> **theShaggy said:**
> Blows my mind that there hasn't been a solution to this problem, since the iDevicerestore git page has numerous people asking.

I can get this thing to put my phone in recovery mode, but then it can't send the iBEC.  For whatever reason, it refuses to work.

I THINK I have put my phone in DFU mode, but since I don't have iTunes, I don't know for sure.

If anyone has any idea how to get it to upload my iBEC?  I get this error:

Found device in Recovery mode
Identified device as iPhone1,2
Extracting BuildManifest from IPSW
Product Version: 3.1.3
Product Build: 7E18
Custom firmware requested. Disabled TSS request.
Variant: Customer Upgrade Install (IPSW)
This restore will update your device without loosing data.
Extracting filesystem from IPSW
[==================================================] 100.0%
Resetting recovery mode connection...
Extracting iBEC.n82ap.RELEASE.dfu
Sending iBEC (105844 bytes)...
ERROR: Unable to send iBEC component: Unable to upload data to device
ERROR: Unable to send iBEC to device.
ERROR: Unable to send iBEC
ERROR: Unable to place device into restore mode

I tested and detected that Recovery Mode was not initialized. Maybe someone commented it to test. Then he or she forgot to remove it.
These codes are on in line 385-390 in file libirecovery/src/libirecovery.c.

```
/* initiate transfer */
    if (recovery_mode) {
        error = libusb_control_transfer(client->handle, 0x41, 0, 0, 0, NULL, 0, 1000);
        if (error != IRECV_E_SUCCESS) {
            return error;
        }
    }
```Have funs!

---

### Post by iPhoneNewbie on 2010-12-30
> **lt_gustavsen said:**
> Just for the record. I was not able to restore the ipad to firmware 4.2.1.

I actually also installed those tools one more time and wrote down each step.

This was on 10.10 but I think it's close on 10.04
1. As an addition to the other apt-get's in the github readme 

```
sudo apt-get install libusb-1.0-0-dev libplist++1 swig libreadline-dev
```in libimobiledevice/Makefile
comment/uncomment this lines  before make install
```

    cp libirecovery.so /usr/local/lib/libirecovery.so
#       cp libirecovery.dylib /usr/local/lib/libirecovery.dylib
        cp include/libirecovery.h /usr/local/include/libirecovery.h
        cp irecovery /usr/local/bin/irecovery
```I was able to activate my ipad but to so I had to use the forked ideviceactivate from here
```
git clone git://github.com/boxingsquirrel/ideviceactivate.git
``` insted of the one described in the github readme.

And something is wrong with the udev rules so I ha best result when I run with **sudo**. 

As I described at top I was not able to upgrade to 4.2.1. 

Here is a typical log:
[PHP]sudo idevicerestore -e  iPad1,1_4.2.1_8C148_Restore.ipsw.1 
[sudo] password for ltg: 
Found device in Normal mode
Identified device as iPad1,1
Extracting BuildManifest from IPSW
ERROR: zip_name_locate: BuildManifesto.plist
Product Version: 4.2.1
Product Build: 8C148
Variant: Customer Erase Install (IPSW)
This restore will erase your device data.
Found ECID 1479633630711
Sending TSS request... received SHSH blobs
Extracting filesystem from IPSW
[==================================================] 100.0%
Entering recovery mode...
ERROR: Unable to reset auto-boot variable
ERROR: Unable to place device into recovery mode[/PHP]I think the line above "ERROR: zip_name_locate: BuildManifesto.plist" is pretty strange. Since the file is actually called BuildManifest.plist in the ipsw file.
After this failure I could no longer talk to the ipad
[PHP]ideviceinfo |egrep "DeviceName|ActivationState|ProductVersion:"
usbmuxd_get_device_list: error opening socket![/PHP]To get out of this and get the ipad back to normal I had to:
```
$ sudo irecovery  -s
Entering recovery mode, starting command prompt
> setenv auto-boot true
> saveenv
> reboot
```In the end I gave up and was a afraid of destroying my wifes ipad so i upgraded it with itunes on windows :(
After you typed:
```
$ sudo irecovery  -s
Entering recovery mode, starting command prompt
> setenv auto-boot true
> saveenv
> /exit
```You continue restore iPad again and it pass this step. Because these codes implement this part doesn't run, so you have to perform it by yourself.
Note: Don't reboot iPhone.

Have funs!

:p:p

---

### Post by theShaggy on 2010-12-31
No luck, I'm also getting this error, along with the iBEC error above.

Entering recovery mode...
ERROR: Unable to reset auto-boot variable
ERROR: Unable to place device into recovery mode

There is something amiss, any idea?

---

### Post by iPhoneNewbie on 2010-12-31
> **theShaggy said:**
> No luck, I'm also getting this error, along with the iBEC error above.

Entering recovery mode...
ERROR: Unable to reset auto-boot variable
ERROR: Unable to place device into recovery mode

There is something amiss, any idea?

Because there is a issue while sending command code to system. So iPhone cannot pass in Recovery Mode. You must type:

```
$ sudo irecovery  -s
Entering recovery mode, starting command prompt
> setenv auto-boot true
> saveenv
> /exit
```Then, you continue restore iPhone in Recovery Mode. Don't reboot iPhone.

```
sudo idevicerestore[COLOR=Blue] iPhone_Firmware[/COLOR].ipsw 
```

---

### Post by theShaggy on 2010-12-31
Tried that, with no luck.

It is still giving me the "cannot transfer iBEC" error, after uncommenting the earlier lines of code.

---

### Post by iPhoneNewbie on 2011-01-03
> **theShaggy said:**
> Tried that, with no luck.

It is still giving me the "cannot transfer iBEC" error, after uncommenting the earlier lines of code.

Do you compile libirecovery again after you remove comment code?

---

### Post by theShaggy on 2011-01-04
I'm pretty sure I did, but I'll try it again.

---

### Post by iPhoneNewbie on 2011-01-07
Nobody can help me. :confused:

---

### Post by theShaggy on 2011-01-14
I got my phone upgraded to 3.1.3!  Thanks, iPhoneNewbie!

AS for getting it up post-4.0: I think the problem is that "buildmanifesto" thing.  It refused to put my phone into Restore mode when trying to upgrade to 4.0.1, but worked fine with 3.1.3, and the only difference I could see was that 3.1.3 extracted "BuildManifest" while 4.0.1 couldn't extract "BuildManifesto."

The question is: where is this slight change coming from, and is there anything we can do to fix that?

---

### Post by theShaggy on 2011-01-15
Curses!

I have forgotten how I got past this part:

Please unplug your device, then plug it back in
Hit any key to continue...
Resetting recovery mode connection...
Extracting kernelcache.release.n82
Sending RestoreKernelCache (4309940 bytes)...
[==================================================] 100.0%
Waiting for device to enter restore mode
ERROR: Unable to connect to device in restore mode
ERROR: Unable to connect to device in restore mode
ERROR: Unable to place device into restore mode


How do I get the phone into restore mode?  I know I did it with 3.1.3, but I would like 4.1 now.

---

### Post by iPhoneNewbie on 2011-01-16
I debugged and detected that iPhone needed a delay time to shift to Restore Mode. So, I added a delay time to file idevicerestore\restore.c at line 230:


```
	if(client->restore == NULL) {
		client->restore = (struct restore_client_t*) malloc(sizeof(struct restore_client_t));
		if(client->restore == NULL) {
			error("ERROR: Out of memory\n");
			return -1;
		}
	}
	[COLOR="Blue"]//add the following code;
	if(restore_device_connected == 0){
		sleep(20);
	}[/COLOR]
	device_error = idevice_event_subscribe(&restore_device_callback, client);
	if (device_error != IDEVICE_E_SUCCESS) {
		error("ERROR: Unable to subscribe to device events\n");
		return -1;
	}
```

Why is 20 seconds? Because it is enough for my iPhone.

---

### Post by theShaggy on 2011-01-16
Awesome... I will try that in my code.  I had read somewhere that it needed a wait time, but figure that if I held it and counted it would ultimately work.  Clearly, I'm wrong.

Hey, how do you get this debugging output?  I've tried it with idevicerestore -d, but it doesn't really show me much of anything.  I'd love to be able to contribute some brain power (without having the C scripting experience), so any way I can do some problem solving with/for you would definitely make me happy.

<i>Added:</i> No luck.  It just doesn't want to enter restore mode.  I'm still trying to figure out how I managed to do it before.

Maybe I reboot the device?

---

### Post by theShaggy on 2011-01-16
Is there any way to permanently save the "auto-boot true" on the iPhone?  It interrupts the phone update process, which might be part of the problem.

---

### Post by iPhoneNewbie on 2011-01-17
> **theShaggy said:**
> Awesome... I will try that in my code.  I had read somewhere that it needed a wait time, but figure that if I held it and counted it would ultimately work.  Clearly, I'm wrong.

Hey, how do you get this debugging output?  I've tried it with idevicerestore -d, but it doesn't really show me much of anything.  I'd love to be able to contribute some brain power (without having the C scripting experience), so any way I can do some problem solving with/for you would definitely make me happy.

<i>Added:</i> No luck.  It just doesn't want to enter restore mode.  I'm still trying to figure out how I managed to do it before.

Maybe I reboot the device?

I see the messages are displayed on screen. Then i guess which files contain them. Finally, i add my messages into these files to debug them.
I detect and guess that if my iPhone need a delay time to enter Restore Mode. So, i add my code to file restore.c.
That is all i did.
Have funs! :D

---

### Post by iPhoneNewbie on 2011-01-17
> **theShaggy said:**
> Is there any way to permanently save the "auto-boot true" on the iPhone?  It interrupts the phone update process, which might be part of the problem.

I have already tested and modified them but until now, there is no effect. This library is very big and i cannot understand it exactly.
Can you help me :).

---

### Post by XiiiX on 2011-01-19
I Need Help! make linux && sudo make install not working et all!

and, does the iDeviceRestore restore without the SHSHs? if i am in 4.1 and i wanna go to 4.0.1 without SHSHs of 4.0.1 can i use iDeviceResotre to help me?

---

### Post by iPhoneNewbie on 2011-01-20
idevicerestore doesn't depend on something. It simply erase all iPhone data and then write the firmware to iPhone.
With the new ifuse version release 12.01.2011, i think you can restore iPhone 4.2.1. I don't restore iOS 4.2.1 successfully, but it can enter recovery mode.

;);)

---

### Post by XiiiX on 2011-01-20
can anyone compile and share with me the idevicerestore binary for linux? i cant compile it. GitHub account of chronic dev in 401 HTTP error.

---

### Post by iPhoneNewbie on 2011-01-24
You can see information at link: [http://www.libimobiledevice.org/]("http://www.libimobiledevice.org/") and download at link: [https://github.com/posixninja/idevicerestore/archives/master]("https://github.com/posixninja/idevicerestore/archives/master")

:D:D

---

### Post by ubunt me on 2011-09-03
I have a new kind of problem. idevicerestore is not able to find my ipod touch 4g. It finds a device in recovery mode but identifies it as ipad 1,1. Also i cannot find any line to comment/uncomment in libimobiledevice/makefile. I had compiled perfectly with no error but in normal mode it says make sure a device is connected and in dfu mode it says usbmuxd open socket erro!

WHAT DO I DO!

---

### Post by ubunt me on 2011-09-03
I just discovered an Awesome Thing.....Instead of using the default poisix gi repo use this one
" [http://github.com/boxingsquirrel/idevicerestore]("https://github.com/boxingsquirrel/idevicerestore").git"
I got past the sending iBEC but still stuck on cannot put in restore mode!

---

