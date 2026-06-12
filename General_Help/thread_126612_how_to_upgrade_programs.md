---
title: "how to upgrade programs"
date: 2006-02-06
forum: General Help
---

### Post by tikal26 on 2006-02-06
Hey:
I have being using Linux for about a year (my anniversary is coming soon) and I just ran into a problem. I finally installed things outside the repose, like real player and java, but now I am wondering how do I upgrade them. Do I have to remove them completely and reinstall the whole new version? It there an easier way?

---

### Post by lol on 2006-02-07
No, no other way (I mean, you have to remove and reinstall them).

But both Java and real player are available in repositories (I don't remember which one though). If they do not appear in your packages list, you should then add the backports in your repositories list, as well as the following:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

---

### Post by tikal26 on 2006-02-07
lol:
thanks, but now I have another problem. How do I run a script?
I am installing a program, but I don't know how to do number 4 of the instructions
1.- Create a folder where you are going to install RealFlow©. Be sure that you have the system permissions to do it. 
 $ mkdir RealFlow
 
 
 2.- Copy the downloaded "realflow.tar.gz" file to that folder.
3.- Uncompress and untar the package.
 $ gzip -d realflow.tar.gz
 $ tar -xvf realflow.tar
4.- Use the "realflow" script to launch RealFlow© or "realflownode" to launch the RealFlow© simulation node. Because the folder where the RealFlow© binaries are is not in the &#8220;PATH&#8221; environment variable we recommend that you edit your account initialization script to add the RealFlow© binaries path to it. You can do it manually before launch RealFlow using the following command (bash shell running is assumed).
 $ export PATH=$PATH:/usr/local/RealFlow/bin

so I did 1-3, but I have no idea how to do nuber 4. what is a bash shell?

---

### Post by greenpenguin on 2006-02-07
The bash shell is what you've been typing inside :D.
If you just did it all graphically, open a terminal (Apps->Accessories->Terminal) and type in there.  then type the program name.

Hope that helps :D.

---

### Post by tikal26 on 2006-02-07
green penguin thanks for the quick reply, but I am wondering what I am supposed to type before the program name. A dot? bacause that did not worked

---

### Post by nrwilk on 2006-02-07
[QUOTE=tikal26]A dot? bacause that did not worked[/QUOTE]

No, a dot-slash.

So, if the script is called progRun, then type this:

```
./progRun
```

---

### Post by tikal26 on 2006-02-08
thanks

---

### Post by nrwilk on 2006-02-08
[QUOTE=tikal26]thanks[/QUOTE]
sure thing!:)

---

