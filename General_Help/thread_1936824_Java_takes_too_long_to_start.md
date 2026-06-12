---
title: "Java takes too long to start"
date: 2012-03-06
forum: General Help
---

### Post by pulseplanet on 2012-03-06
Hello All,

  I am running ImageJ (an java based Image analysis program). Everytime I try starting it, it takes forever to load. Once it loads, it works as it should. 

Here is how I am launching it:

```

~/.ImageJ/jre/bin/java \
-Xmx2048m \
-jar ~/.ImageJ/ij.jar \
-ijpath ~/.ImageJ

```

I tried both ~/.ImageJ/jre/bin/java and /usr/bin/java

```

$> /usr/bin/java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.6) (6b22-1.10.6-0ubuntu1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

$> ~/.ImageJ/jre/bin/java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)

```

Any help will be greatly appreciated.

Thanks,
Karthik

---

### Post by scottstensland on 2012-03-06
I just did a fresh download of imageJ source code:

cd whichever/source_dir
ant   # <-- this ant command compiles the package into a jar

to execute issue :

java whichever/source_dir/ij.jar

this launches immediately for me.
In your launch syntax you supply the parm
to allocate 2 gigs of RAM 
[code]
-Xmx2048m
/[code]

- this is probably too high
and is causing your machine to swap out running applications.
Either leave off that parameter from your launch syntax
or if U really need 2 gigs then before launching exit out
of all running apps to free up enough RAM.  
If your launch time is quick when leaving off the 2 gig parm,
then its probably such a RAM swapping issue.

good luck - Scott Stensland

---

### Post by pulseplanet on 2012-03-06
Thanks Scott, but that was not the problem. Before posting, I did try:
```

~/.ImageJ/jre/bin/java -jar ~/.ImageJ/ij.jar

```

and that takes as long to start (about 3 minutes).
Memory is not an issue. My desktop has about 16 GB of RAM and just about 3 GB was used when I issued this call to ImageJ.



> **scottstensland said:**
> I just did a fresh download of imageJ source code:

cd whichever/source_dir
ant   # <-- this ant command compiles the package into a jar

to execute issue :

java whichever/source_dir/ij.jar

this launches immediately for me.
In your launch syntax you supply the parm
to allocate 2 gigs of RAM 
[code]
-Xmx2048m
/[code]

- this is probably too high
and is causing your machine to swap out running applications.
Either leave off that parameter from your launch syntax
or if U really need 2 gigs then before launching exit out
of all running apps to free up enough RAM.  
If your launch time is quick when leaving off the 2 gig parm,
then its probably such a RAM swapping issue.

good luck - Scott Stensland

---

