---
title: "java webex 10.10 audio &quot;unaccessible&quot;"
date: 2011-10-11
forum: General Help
---

### Post by zephyr707 on 2011-10-11
hi there,

I just missed a nice webex session b/c my audio wasn't working.  I'm running ubuntu 10.10 64-bit:

Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick
Linux thomas 2.6.35-30-generic #59-Ubuntu SMP Tue Aug 30 19:00:03 UTC 2011 x86_64 GNU/Linux

When I try to activate the sound in the webex I get a message that says:

"the audio device is unaccessible"

or something along those lines.  I have tried installing sun-java over openjdk and many other attempts with .java.policy files, symlinking directories, removing my .java dir, etc.  From what I have read I gather that it is a bug with pulseaudio and java in ubuntu.

Does anyone know a fix for this?  It is incredibly frustrating and I no longer have a windows box to use, so I am dead in the water and have another webex meeting in less than a week.

Any help would be greatly appreciated,
thanks
z

---

### Post by zephyr707 on 2011-10-16
bump... any java experts in here?

---

### Post by zephyr707 on 2011-10-25
sitting here watching a presentation with no audio...  does anyone know of a linux distro that definitely works with webex and can do the VOIP audio?

---

### Post by Daniel Menes on 2012-03-11
The issue is that the WebEx applet attempts to load a 32-bit native module in order to access the sound.  The usual solution is to run a 32-bit browser when using WebEx.  However, I have found a way to run a 32-bit JVM in 64-bit firefox using the nspluginwrapper utility

As supplied, the latest version of nspluginwrapper (1.4.4) does not work with the Java plugin.  That is because the Java plugin expects the library libstdc++.so to be loaded before it starts.  It is a simple matter to patch nspluginwrapper so that it loads the necessary library.

Download the latest sources for nspluginwrapper from [http://nspluginwrapper.org/download/](http://nspluginwrapper.org/download/)

Expand the file (tar -xvzf) in a convenient location

Apply the following patch to the file npw-viewer.c:


```
--- npw-viewer.c    2011-06-30 23:18:57.000000000 -0400
+++ nspluginwrapper-1.4.4/src/npw-viewer.c    2012-03-11 14:09:35.104158681 -0400
@@ -5128,6 +5128,17 @@
     }
     handles[n_handles++] = handle;
     dlerror();
+#else
+    /* Install libstdc++ for java */
+    const char libstcpp[] = "libstdc++.so.6";
+    D(bug("  trying to open standard C++ runtime '%s'\n", libstcpp ));
+    if ((handle = dlopen(libstcpp, RTLD_LAZY|RTLD_GLOBAL)) == NULL) {
+      npw_printf("ERROR: %s\n", dlerror());
+      return 1;
+    }
+    handles[n_handles++] = handle;
+    dlerror();
+
 #endif
     D(bug("  %s\n", plugin_path));
     if ((handle = dlopen(plugin_path, RTLD_LAZY)) == NULL) {

```You may need to get some additional libraries to make things work.  In particular, I installed:

sudo apt-get install libcurl4-nss-dev libxt-dev libgtk2.0-dev g++-multilib

YMMV.

After getting the dependencies, its
```

./configure
make
sudo make install

```Then you will need a 32-bit jre. This can be downloaded from Oracle's website and installed.

Finally, locate the file libnpjp2.so in the "lib" directory of the 32-bit Java installation.  I found it in /usr/lib/jvm/ia32-java-6-sun/jre/lib/i386/.

Execute

```
sudo nspluginwrapper -i /usr/lib/jvm/ia32-java-6-sun/jre/lib/i386/libnpjp2.so
```(Or wherever your Java was installed.)

Then (re) start Firefox.  Type "about:plugins" in the address bar.  You should see your newly installed 32-bit Java plugin.

Try joining a WebEx meeting with sound

---

### Post by Geremia on 2012-08-28
> **Daniel Menes said:**
> The issue is that the WebEx applet attempts to load a 32-bit native module in order to access the sound.  The usual solution is to run a 32-bit browser when using WebEx.  However, I have found a way to run a 32-bit JVM in 64-bit firefox using the nspluginwrapper utility

As supplied, the latest version of nspluginwrapper (1.4.4) does not work with the Java plugin.  That is because the Java plugin expects the library libstdc++.so to be loaded before it starts.  It is a simple matter to patch nspluginwrapper so that it loads the necessary library.

Download the latest sources for nspluginwrapper from [http://nspluginwrapper.org/download/](http://nspluginwrapper.org/download/)

Expand the file (tar -xvzf) in a convenient location

Apply the following patch to the file npw-viewer.c:


```
--- npw-viewer.c    2011-06-30 23:18:57.000000000 -0400
+++ nspluginwrapper-1.4.4/src/npw-viewer.c    2012-03-11 14:09:35.104158681 -0400
@@ -5128,6 +5128,17 @@
     }
     handles[n_handles++] = handle;
     dlerror();
+#else
+    /* Install libstdc++ for java */
+    const char libstcpp[] = "libstdc++.so.6";
+    D(bug("  trying to open standard C++ runtime '%s'\n", libstcpp ));
+    if ((handle = dlopen(libstcpp, RTLD_LAZY|RTLD_GLOBAL)) == NULL) {
+      npw_printf("ERROR: %s\n", dlerror());
+      return 1;
+    }
+    handles[n_handles++] = handle;
+    dlerror();
+
 #endif
     D(bug("  %s\n", plugin_path));
     if ((handle = dlopen(plugin_path, RTLD_LAZY)) == NULL) {

```You may need to get some additional libraries to make things work.  In particular, I installed:

sudo apt-get install libcurl4-nss-dev libxt-dev libgtk2.0-dev g++-multilib

YMMV.

After getting the dependencies, its
```

./configure
make
sudo make install

```Then you will need a 32-bit jre. This can be downloaded from Oracle's website and installed.

Finally, locate the file libnpjp2.so in the "lib" directory of the 32-bit Java installation.  I found it in /usr/lib/jvm/ia32-java-6-sun/jre/lib/i386/.

Execute

```
sudo nspluginwrapper -i /usr/lib/jvm/ia32-java-6-sun/jre/lib/i386/libnpjp2.so
```(Or wherever your Java was installed.)

Then (re) start Firefox.  Type "about:plugins" in the address bar.  You should see your newly installed 32-bit Java plugin.

Try joining a WebEx meeting with soundThis is a nice solution, although I still have the same problem even with 32 bit JRE libs… Do you know why? thanks

---

### Post by 910Radar on 2012-10-10
HI All

I'm trying this on Ubuntu 12.04 and I get a link error (I think) - 

make
gcc -std=c99   -o npplayer npplayer-npw-player.o npplayer-debug.o npplayer-rpc.o npplayer-utils.o npplayer-glibcurl.o npplayer-gtk2xtbin.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0   -lglib-2.0   -lcurl   -lXt -lX11   -lpthread 
npplayer-npw-player.o: In function `main':
/home/rstones/Downloads/nsplugginwrapper/nspluginwrapper-1.4.4/src/npw-player.c:2486: undefined reference to `g_thread_init'

Any hints gratefully accepted

Rgds

910

---

### Post by 910Radar on 2012-10-10
Ha, things have moved on a bit.  I surfed and found that -lgthread-2.0 added to the compile line could help so I copied the out put of make and tagged it on:

gcc -std=c99   -o npplayer npplayer-npw-player.o npplayer-debug.o npplayer-rpc.o npplayer-utils.o npplayer-glibcurl.o npplayer-gtk2xtbin.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0   -lglib-2.0   -lcurl   -lXt -lX11   -lpthread -lgthread-2.0

it executed and no (apparent) errors were seen, so off we go with the "sudo make install" - that appeared to work too (on a role now . . .)

Unfortunately when i tried 

sudo nspluginwrapper -i /home/rstones/Downloads/jre1.6.0_31/lib/i386/libnpjp2.so

I get 
nspluginwrapper: no appropriate viewer found for /home/rstones/Downloads/jre1.6.0_31/lib/i386/libnpjp2.so

Again, any hints gratefully accepted

Rgds

910

---

### Post by panamik on 2012-11-03
910Radar,


Have you applied the patch from Daniel Menes?
The error "nspluginwrapper: no appropriate viewer found for .../libnpjp2.so" occurred when I was trying to use the original (not patched) nspluginwrapper.

As far as I understand, this patch makes nspluginwrapper support the java library.


With the patch applied, I've managed to install the 32b java firefox plugin, and I see it on about:plugins page. But webex still doesn't work: this time, it just silently doesn't start at all (I'm on Ubuntu 12.10).

I didn't yet have a chance to dig deeper.


Can anybody confirm this approach works with latest Ubuntu?

---

### Post by Geremia on 2012-11-03
I called WebEx regarding its lack of full Linux support, and they asked me many Linux-specific questions, but obviously they don't care about fully supporting Linux.

---

### Post by Normalex on 2013-03-12
To make Webex fully work under Ubuntu 12.04
The official page is quite clear: [https://meetings.webex.com/collabs/support/nfaqs?_iframe=/webex/v1.2/support/en_US/rn/system_rn.htm](https://meetings.webex.com/collabs/support/nfaqs?_iframe=/webex/v1.2/support/en_US/rn/system_rn.htm)

Java PPA, [http://www.ubuntuupdates.org/ppa/webupd8_java](http://www.ubuntuupdates.org/ppa/webupd8_java)

sudo apt-get install oracle-java6-installer
sudo apt-get install libstdc++6
sudo apt-get install libstdc++5

Optionally, depending on whether you have version 7 as well, you would need to change Firefox plugin to either v6 or v7.
If the plugin is v7 then you can choose which java to use for web apps through
Open, Oracle Java 7 Plugin Control Panel from regular Start Menu.
Under Java tab, click View, click Enabled only on v 1.6

Switching them is through:
sudo update-alternatives --config java
sudo update-alternatives --config libnpjp2.so

---

