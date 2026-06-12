---
title: "java web start problem"
date: 2010-06-04
forum: General Help
---

### Post by andres.ordonez on 2010-06-04
Hi, I've been trying to run this:

[http://phet.colorado.edu/simulations/sims.php?sim=Gravity_Force_Lab](http://phet.colorado.edu/simulations/sims.php?sim=Gravity_Force_Lab)

I click the Run Now! button, then I'm asked to Open with Open OpenJDK Java 6 Web Start(default), I click OK, the file is downloaded but nothing happens.

I was using the icedtea6-plugin, removed it and installed sun-java6-plugin (from [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner) to see if that was the problem, then  I did update-alternatives --config java and checked /usr/lib/jvm/java-6-sun/jre/bin/java 

But it still doesn't work! What now?
Thanks in advance.

(ubuntu 10.04 64bit)

---

### Post by stinkeye on 2010-06-04
There is a tutorial here on installing java and making firefox use the plugin.
In the Firefox section he uses **&#65279;/usr/lib/jvm/java-6-sun1.6.0.20/jre/plugin/i386/ns7/libjavaplugin_oji.so ** for the plugin path.

I'm on 64bit and the line to use for the plugin path for me is
**/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/libjavaplugin_jni.so**

You should also be able to just download the file and run it.
You'll probably need to make it executable (right click > properties > permissions)
Open with **Sun Java 6 Runtime**

---

### Post by andres.ordonez on 2010-06-04
> **stinkeye said:**
> There is a tutorial here on installing java and making firefox use the plugin.
Where?:-?
BTW I tried to just save the file and run it (after making it executable) but all I got was a loading window that I eventually had to kill.
Thanks!

---

### Post by stinkeye on 2010-06-04
Oops!
[_**[COLOR="DarkRed"]http://www.ghacks.net/2010/05/21/install-java-on-ubuntu-10-04/[/COLOR]**_]("http://www.ghacks.net/2010/05/21/install-java-on-ubuntu-10-04/")

---

### Post by andres.ordonez on 2010-06-04
I followed the instructions besides removing all the openjdk packages and now everything (so far) is working!

Thanks Stinkeye

---

### Post by ronnieredd on 2012-12-08
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

Anyone?

---

### Post by howefield on 2012-12-08
Old thread back to sleep.

Please feel free to start a fresh one.

---

