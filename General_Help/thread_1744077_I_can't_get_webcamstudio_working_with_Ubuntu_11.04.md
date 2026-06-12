---
title: "I can't get webcamstudio working with Ubuntu 11.04"
date: 2011-04-30
forum: General Help
---

### Post by oopsie on 2011-04-30
I've had a lot of trouble installing webcam studio. I've managed to get past some problems, but it still wont work.

When I start it the title comes up for a few seconds then disappears.

If I run it from the console, I get this.

```

Using JRE: /usr/lib/jvm/java-6-openjdk/bin
Exception in thread "main" java.lang.UnsatisfiedLinkError: Unable to load library 'glib-2.0': libglib-2.0.so: cannot open shared object file: No such file or directory
	at com.sun.jna.NativeLibrary.loadLibrary(NativeLibrary.java:164)
	at com.sun.jna.NativeLibrary.getInstance(NativeLibrary.java:237)
	at com.sun.jna.Library$Handler.<init>(Library.java:140)
	at com.sun.jna.Native.loadLibrary(Native.java:374)
	at org.gstreamer.lowlevel.GNative.loadNativeLibrary(GNative.java:48)
	at org.gstreamer.lowlevel.GNative.loadLibrary(GNative.java:45)
	at org.gstreamer.lowlevel.GlibAPI.<clinit>(GlibAPI.java:36)
	at org.gstreamer.lowlevel.GMainContext.<init>(GMainContext.java:30)
	at org.gstreamer.Gst.init(Gst.java:224)
	at webcamstudio.Main.<init>(Main.java:83)
	at webcamstudio.Main.main(Main.java:2419)

```

Can anybody help me?

---

### Post by andreselsuave on 2011-04-30
This solved the issue for me:
```
sudo apt-get install libglib2*

```

---

### Post by wgarcia on 2011-04-30
There is an issue opened on this, and the above workaround proposed:

[http://code.google.com/p/webcamstudio/issues/detail?id=21](http://code.google.com/p/webcamstudio/issues/detail?id=21)

which also solved it for me. Actually with

sudo apt-get install libglib2.0-dev

it is sufficient, it seems.

---

### Post by WvanWaas on 2011-05-20
This did it for me. Processing 1.5 did work with the same libraries. After all there is no way they will get me off an Linux PC ever again ;-) Thanks guys

---

### Post by timgood on 2011-05-20
I'm trying to use this with a Logitech HD720p webcam as a source. Camera works, but I'm bright blue. Camera works fine in Skype and guvcview. Looks like the colours are inverted? See attached picture:

Any idea how I can get this working? Also I can't seem to get a resolution above 320 x 240. Frame size changes, but picture remains same size. 

Help would be appreciated.

---

### Post by ZeroFossilFuel on 2012-07-11
@timgood - looks a lot like the blue smurf problem I ran into with my Nvidia cards when viewing YouTube videos after Adobe sabotaged Flash for Linux. Had to disable hardware acceleration to get back to normal colors. Hope this gives you a clue where to look.

As far as not being able to get WCS to launch, sorry but this is not fixed. I'm running Xubuntu 12.04 on 3 different machines configured very much the same on all. #1 Asus 1018P with 2GB upgrade; #2 Dell Precision 670, dual Xeon 2.8GHz, 2GB and Nvidia G220 1GB; #3 White Box i5-760, Xubuntu 64bit, 8GB, Nvidia GT9600 512MB.

WCS will run on the Dell, not the Asus or the i5. sudo apt-get install libglib2* did not work for me. Not much better luck with 0.60. (sigh) :(

---

### Post by wildmanne39 on 2012-07-11
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

