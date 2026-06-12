---
title: "32-bit and 64-bit Firefox at the same time"
date: 2010-02-18
forum: General Help
---

### Post by digitaleagle on 2010-02-18
Is it possible to run both a 32-bit version of Firefox and a 64-bit version of Firefox at the same time?

Here is my problem:
WebEx [requires]("http://support.webex.com/support/system-requirements.html") 32-bit for Ubuntu Linux.  But, I need a 64-bit OS for other software that I run.  I also have 64-bit Java running Eclipse and a couple of other Swing applications with no problems.  So, I don't really want to switch everything over to 32-bit.

Here is what I was able to do:
- I can create a separate Firefox Profile for WebEx.  I launch it using the -P switch.
- I can have multiple Firefox Profiles open at the same time with the --no-remote switch.
- I downloaded the 32-bit version of Firefox from the Firefox website and extracted it into a directory underneath my home directory.
- I can run that version of Firefox, and I am assuming that is a 32-bit version running.

The problem is that it does not load any of my plugins because they are 64-bit.  I see in the terminal output these messages:
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]

I have a 32-bit version of Java installed at ~/bin/java/jdk1.6.0_18, and I created a link to the plugin in my 32-bit firefox plugins directory:
~/bin/java/firefox/plugins$ sudo ln -s /home/skp/bin/java/jdk1.6.0_18/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

From what I can tell, Firefox is not looking in that directory for Java.

---

### Post by Dayofswords on 2010-02-18
why not do it in a virtual machine running 32-bit ubuntu?

---

### Post by wojox on 2010-02-18
Link it to 

```
/.mozilla/plugins
```

In your home directory.

---

### Post by digitaleagle on 2010-02-18
That is a good idea.  I think I will try that next.

I have been using remote desktop to a Windows machine to do all of my WebEx meetings.  The response time has been horrible when I view the desktop of the other person in the meeting.

I think the problem is because I have multiple layers of screens streaming to my PC.  The remote PC is the first layer, and the other person's desktop is the second layer.  A virtual machine would have multiple layers, but because the first layer is not across the Internet, the performance might be better.

Another thing that is not that important is my video camera.  I would love to be able to use my video camera.  I am not sure how hard it would be to make the laptop camera available to the virtual PC.

Anyway, I will give it a try and see if it works better.  Thanks for the idea.

---

### Post by digitaleagle on 2010-02-18
> **wojox said:**
> Link it to 

```
/.mozilla/plugins
```

In your home directory.

I will give that a try.  I don't think I already tried that.  The problem is that my 64-bit firefox would also use that directory.  Maybe it wouldn't matter, the 64-bit version would just spit out the error that it can't load that plugin.

I will let you know once I give that a shot.  I have to run now, but as soon as I get back, I will try.

Thanks for the suggestion.

---

### Post by wojox on 2010-02-18
[running two or more copies of firefox]("http://www.cts.wustl.edu/~allen/2copiesoffirefox.html")

---

### Post by digitaleagle on 2010-02-19
> **wojox said:**
> Link it to 

```
/.mozilla/plugins
```

In your home directory.

I have tried that and it didn't seem to work.

I am running firefox from here:

```
skp@pecan:~/bin/java$ source env.sh 
skp@pecan:~/bin/java$ which firefox
/home/skp/bin/java/firefox/firefox

```

My Java version looks like this:

```
skp@pecan:~/bin/java$ which java
/home/skp/bin/java/jdk1.6.0_18/jre/bin//java
skp@pecan:~/bin/java$ java -version
java version "1.6.0_18"
Java(TM) SE Runtime Environment (build 1.6.0_18-b07)

```

I have setup the links in both places:

```
skp@pecan:~/bin/java$ ls -l /home/skp/.mozilla/plugins/libjavapluin_oji.so 
lrwxrwxrwx 1 skp skp 71 2010-02-19 13:05 /home/skp/.mozilla/plugins/libjavapluin_oji.so -> /home/skp/bin/java/jdk1.6.0_18/jre/plugin/i386/ns7/libjavaplugin_oji.so
skp@pecan:~/bin/java$ ls -l firefox/plugins/libjavaplugin_oji.so 
lrwxrwxrwx 1 root root 71 2010-02-18 17:07 firefox/plugins/libjavaplugin_oji.so -> /home/skp/bin/java/jdk1.6.0_18/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

When I run Firefox, my page with the applet still says:

"Java Applet Support Required"

The output on the terminal looks like this:

```
skp@pecan:~/bin/java$ firefox --no-remote -P WebEx file:///home/skp/bin/javaTest/javaTest.html
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so [/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-mully-plugin.so [/usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so [/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]

```

---

### Post by digitaleagle on 2010-02-19
> **wojox said:**
> [running two or more copies of firefox]("http://www.cts.wustl.edu/~allen/2copiesoffirefox.html")

I looked at this link, and it looks promising, but I think I have already accomplished everything that it says to do.  It looks like they were trying to run two copies of the same version of Firefox because they make a copy of it.

I have a 64bit version installed from the repository installed at /usr/bin/firefox.  Then, I have a 32bit version installed manually in ~/bin/java/firefox.

I did uncomment the debug line in the firefox script changing it from this:

```
#uncomment for debugging
#set -x

moz_libdir=/usr/local/lib/firefox-3.6

# Use run-mozilla.sh in the current dir if it exists
# If not, then start resolving symlinks until we find run-mozilla.sh

```

to this:

```
#uncomment for debugging
set -x

moz_libdir=/usr/local/lib/firefox-3.6

# Use run-mozilla.sh in the current dir if it exists
# If not, then start resolving symlinks until we find run-mozilla.sh

```

I still don't have Java support.  Here is the output:

```
skp@pecan:~/bin/java$ firefox --no-remote -P WebEx file:///home/skp/bin/javaTest/javaTest.html
+ moz_libdir=/usr/local/lib/firefox-3.6
+ found=0
+ progname=/home/skp/bin/java/firefox/firefox
+ dirname /home/skp/bin/java/firefox/firefox
+ curdir=/home/skp/bin/java/firefox
+ basename /home/skp/bin/java/firefox/firefox
+ progbase=firefox
+ run_moz=/home/skp/bin/java/firefox/run-mozilla.sh
+ test -x /home/skp/bin/java/firefox/run-mozilla.sh
+ dist_bin=/home/skp/bin/java/firefox
+ found=1
+ [ 1 = 0 ]
+ script_args=
+ debugging=0
+ MOZILLA_BIN=firefox-bin
+ [  = beos ]
+ pass_arg_count=0
+ [ 4 -gt 0 ]
+ arg=--no-remote
+ shift
+ set -- -P WebEx file:///home/skp/bin/javaTest/javaTest.html --no-remote
+ expr 0 + 1
+ pass_arg_count=1
+ [ 4 -gt 1 ]
+ arg=-P
+ shift
+ set -- WebEx file:///home/skp/bin/javaTest/javaTest.html --no-remote -P
+ expr 1 + 1
+ pass_arg_count=2
+ [ 4 -gt 2 ]
+ arg=WebEx
+ shift
+ set -- file:///home/skp/bin/javaTest/javaTest.html --no-remote -P WebEx
+ expr 2 + 1
+ pass_arg_count=3
+ [ 4 -gt 3 ]
+ arg=file:///home/skp/bin/javaTest/javaTest.html
+ shift
+ set -- --no-remote -P WebEx file:///home/skp/bin/javaTest/javaTest.html
+ expr 3 + 1
+ pass_arg_count=4
+ [ 4 -gt 4 ]
+ [ 0 = 1 ]
+ /home/skp/bin/java/firefox/run-mozilla.sh /home/skp/bin/java/firefox/firefox-bin --no-remote -P WebEx file:///home/skp/bin/javaTest/javaTest.html
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so [/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-mully-plugin.so [/usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so [/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
+ exitcode=0
+ exit 0

```

I also tried to change the library directory at the top of the script to look like this:

```
#uncomment for debugging
set -x

moz_libdir=/bin/home/skp/bin/java/firefox

# Use run-mozilla.sh in the current dir if it exists
# If not, then start resolving symlinks until we find run-mozilla.sh

```

I still get the same result/output:


```
skp@pecan:~/bin/java$ firefox --no-remote -P WebEx file:///home/skp/bin/javaTest/javaTest.html
+ moz_libdir=/bin/home/skp/bin/java/firefox
+ found=0
+ progname=/home/skp/bin/java/firefox/firefox
+ dirname /home/skp/bin/java/firefox/firefox
+ curdir=/home/skp/bin/java/firefox
+ basename /home/skp/bin/java/firefox/firefox
+ progbase=firefox
+ run_moz=/home/skp/bin/java/firefox/run-mozilla.sh
+ test -x /home/skp/bin/java/firefox/run-mozilla.sh
+ dist_bin=/home/skp/bin/java/firefox
+ found=1
+ [ 1 = 0 ]
+ script_args=
+ debugging=0
+ MOZILLA_BIN=firefox-bin
+ [  = beos ]
+ pass_arg_count=0
+ [ 4 -gt 0 ]
+ arg=--no-remote
+ shift
+ set -- -P WebEx file:///home/skp/bin/javaTest/javaTest.html --no-remote
+ expr 0 + 1
+ pass_arg_count=1
+ [ 4 -gt 1 ]
+ arg=-P
+ shift
+ set -- WebEx file:///home/skp/bin/javaTest/javaTest.html --no-remote -P
+ expr 1 + 1
+ pass_arg_count=2
+ [ 4 -gt 2 ]
+ arg=WebEx
+ shift
+ set -- file:///home/skp/bin/javaTest/javaTest.html --no-remote -P WebEx
+ expr 2 + 1
+ pass_arg_count=3
+ [ 4 -gt 3 ]
+ arg=file:///home/skp/bin/javaTest/javaTest.html
+ shift
+ set -- --no-remote -P WebEx file:///home/skp/bin/javaTest/javaTest.html
+ expr 3 + 1
+ pass_arg_count=4
+ [ 4 -gt 4 ]
+ [ 0 = 1 ]
+ /home/skp/bin/java/firefox/run-mozilla.sh /home/skp/bin/java/firefox/firefox-bin --no-remote -P WebEx file:///home/skp/bin/javaTest/javaTest.html
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so [/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-mully-plugin.so [/usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so [/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
+ exitcode=0
+ exit 0

```


I don't understand why it seems to ignore the java plugin that I placed in the plugins folders.

---

### Post by dvo on 2010-02-25
You can use MOZ_PLUGIN_PATH to point to the appropriate plugins directory. 
For instance, I have a startup script for each of the two FF binary variants,
one using
```
export MOZ_PLUGIN_PATH=~/.mozilla/plugins_i386
```
and the other
```
export MOZ_PLUGIN_PATH=~/.mozilla/plugins_amd64
```

Other candidates are, for example:
* to use the (64-bit) plugins officially installed by ubuntu:
```
export MOZ_PLUGIN_PATH=/usr/lib/firefox-addons/plugins/
```
* to use the (32-bit) plugins you might have placed in ~/.mozilla/plugins:
```
export MOZ_PLUGIN_PATH=~/.mozilla/plugins
```

---

### Post by digitaleagle on 2010-03-03
> **dvo said:**
> You can use MOZ_PLUGIN_PATH to point to the appropriate plugins directory. 
For instance, I have a startup script for each of the two FF binary variants,
one using
```
export MOZ_PLUGIN_PATH=~/.mozilla/plugins_i386
```
and the other
```
export MOZ_PLUGIN_PATH=~/.mozilla/plugins_amd64
```

Other candidates are, for example:
* to use the (64-bit) plugins officially installed by ubuntu:
```
export MOZ_PLUGIN_PATH=/usr/lib/firefox-addons/plugins/
```
* to use the (32-bit) plugins you might have placed in ~/.mozilla/plugins:
```
export MOZ_PLUGIN_PATH=~/.mozilla/plugins
```

Thanks dvo.  This is exactly what I needed!  But, I am still missing something.  It is still not recognizing the Java plugin.

I setup an environment script that looks like this:

```
skp@pecan:~/bin/java$ cat env.sh
#!/bin/sh

export PATH=~/bin/java/firefox:~/bin/java/jdk1.6.0_18/jre/bin/:~/bin/java/jdk1.6.0_18/bin/:$PATH
export JAVA_HOME=~/bin/java/jdk1.6.0_18/jre
export MOZ_PLUGIN_PATH=~/bin/java/firefox/plugins


```

This gives me an environment that looks like this:
```
skp@pecan:~/bin/java$ . env.sh
skp@pecan:~/bin/java$ which firefox
/home/skp/bin/java/firefox/firefox
skp@pecan:~/bin/java$ firefox -version
Mozilla Firefox 3.6, Copyright (c) 1998 - 2010 mozilla.org
skp@pecan:~/bin/java$ which java
/home/skp/bin/java/jdk1.6.0_18/jre/bin//java
skp@pecan:~/bin/java$ java -version
java version "1.6.0_18"
Java(TM) SE Runtime Environment (build 1.6.0_18-b07)
Java HotSpot(TM) Server VM (build 16.0-b13, mixed mode)
skp@pecan:~/bin/java$ ls -l $MOZ_PLUGIN_PATH
total 20
lrwxrwxrwx 1 root root    71 2010-02-18 17:07 libjavaplugin_oji.so -> /home/skp/bin/java/jdk1.6.0_18/jre/plugin/i386/ns7/libjavaplugin_oji.so
-rwxr-xr-x 1 skp  skp  15716 2010-01-15 17:41 libnullplugin.so

```

At one point, while I was playing with all of this, I clicked disable on the Java plugin.  But, now I don't have the option to enable it.  I am assuming that is because it is not finding the plugin rather than anything to do with my disabling it earlier.

---

### Post by digitaleagle on 2010-03-03
I was just reading this link:

[http://dougdiego.com/2008/12/04/install-sun-jdk-on-fedora-10/](http://dougdiego.com/2008/12/04/install-sun-jdk-on-fedora-10/)

I noticed the dependencies on libstdc++.  I wonder if that is my problem.  They solve it with:

yum install compat-libstdc++-33 compat-libstdc++-296

I wonder if I have to figure out how I can install it manually so that I can get the 32bit version.

I am just making wild guesses now.  It would nice to have some sort of error message or something to tell me why it doesn't load the plugin.

---

### Post by dvo on 2010-03-04
Hi digitaleagle,

your environment variable settings and installed versions look all fine.
I am pretty sure your problem is that you use libjavaplugin_oji.so, 
while it seems that one meanwhile needs libnpjp2.so instead. 
This should be the reason why your firefox ignores the Java plugin. 
I use (via symbolic links):

```
/usr/lib/jvm/ia32-java-6-sun-1.6.0.15/jre/lib/i386/libnpjp2.so
```
of the ia32-sun-java6-bin package, and

```
/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so
```
of the sun-java6-bin package, respectively.

---

### Post by digitaleagle on 2010-03-04
> **dvo said:**
> Hi digitaleagle,

your environment variable settings and installed versions look all fine.
I am pretty sure your problem is that you use libjavaplugin_oji.so, 
while it seems that one meanwhile needs libnpjp2.so instead. 
This should be the reason why your firefox ignores the Java plugin. 
I use (via symbolic links):

```
/usr/lib/jvm/ia32-java-6-sun-1.6.0.15/jre/lib/i386/libnpjp2.so
```
of the ia32-sun-java6-bin package, and

```
/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so
```
of the sun-java6-bin package, respectively.

dvo, Thank you, thank you, thank you!

It works now!  I was able to not only load Java applets, but WebEx now works for me.  I am one happy camper.


Here is what I did:

```
. env.sh
cd $MOZ_PLUGIN_PATH
rm libjavaplugin_oji.so
ln -s $JAVA_HOME/lib/i386/libnpjp2.so libnpgp2.so

```

I don't think it has changed, but let me post my env.sh file:
```
#!/bin/sh

export PATH=~/bin/java/firefox:~/bin/java/jdk1.6.0_18/jre/bin/:~/bin/java/jdk1.6.0_18/bin/:$PATH
export JAVA_HOME=~/bin/java/jdk1.6.0_18/jre
export MOZ_PLUGIN_PATH=~/bin/java/firefox/plugins

```

Again, thanks for you help.

---

### Post by teotanin on 2012-09-22
I am looking for so long to find this env variable MOZ_PLUGIN_PATH.

And about the java plugin I was using a single ~/.mozilla/pluging directory for both 32 AND 64 bit firefox like this:
[INDENT] libnpjp2.so -> /opt/jdk-1.6.0_24_32bit/jre/lib/i386/libnpjp2.so
[/INDENT][INDENT] libnpjp2.so.64 -> /opt/jdk-1.6.0_24/jre/lib/amd64/libnpjp2.so
[/INDENT] When I tried to install the other plugins (like flash) using the same name space convention only the file with non modified name was loaded. Just the java plugin works fine :-)

---

