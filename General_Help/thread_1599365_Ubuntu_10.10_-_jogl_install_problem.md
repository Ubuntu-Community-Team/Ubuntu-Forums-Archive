---
title: "Ubuntu 10.10 - jogl install problem"
date: 2010-10-17
forum: General Help
---

### Post by nlneilson on 2010-10-17
I just installed 10.10.

Running a java .jar app that requires jogl gives errors.

Exception in thread "main" java.lang.UnsatisfiedLinkError: no gluegen-rt in java.library.path

In 8.04 up to and including 10.04 installing jogl thru synaptics worked but in 10.10 it does not work.

I would prefer that anyone that uses the java app on their computer if they have 10.10 not be required to tinker with setting paths, etc..

java version "1.6.0_21"
Java(TM) SE Runtime Environment (build 1.6.0_21-b06)
Java HotSpot(TM) Server VM (build 17.0-b16, mixed mode)

---

### Post by nlneilson on 2010-10-18
Here is a link to how (where) jogl can be installed manually.
[http://nathanpowell.org/blog/archives/173](http://nathanpowell.org/blog/archives/173)

"Unzip that file, and copy the jogl.jar to: /usr/lib/jvm/java-1.5.0-sun/jre/lib/ext and the libjogl*.so files to: /usr/lib/jvm/java-1.5.0-sun/jre/lib/ext"

This would depend on the java version.

Wherever or what path was set in Ubuntu 8.04 to 10.04 when jogl was installed thru synaptics worked.

Seems strange 10.10 should not work the same.

Tell someone "Try this java app but first you need to jump through a hoop and manually install jogl on Ubuntu 10.10."

Not good.

Maybe this is a bug the 10.10 devs are not aware of.

---

### Post by P4man on 2010-10-18
Sun (oracle) Java is no longer in the repo or supported, its been replaced by openjdk. Thats probably what caused the issue. Jogl is just in the repo;s, I assume it works fine with openjdk.

---

### Post by nlneilson on 2010-10-19
Sun's java is a "partner" and can be added to the repo.
[http://aroundtheweb.info/2010/10/install-sun-java-ubuntu-10-10-maverick-meerkat-official-partner-repository/](http://aroundtheweb.info/2010/10/install-sun-java-ubuntu-10-10-maverick-meerkat-official-partner-repository/)

I was never able to run the app based on NASA WorldWind Java with openjdk, others may have so have started a thread on that forum to see if and how it can be done.

---

### Post by nlneilson on 2010-10-19
Here is a portion of the response on the NASA WWJ forum.

> I have an app that runs on Windows, Linux, MacOS, and Solaris.
I just include the dll's/so's in the jar at build.
Because linux and solaris both use so's with the same names,
i had to do a build profile for those so it included the correct
files based on my target machine.

---

