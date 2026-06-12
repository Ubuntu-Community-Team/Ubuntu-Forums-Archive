---
title: "&quot;Wiring&quot; software won't run in Ubuntu 11.10 (but runs just fine in Lubuntu)"
date: 2012-03-26
forum: General Help
---

### Post by theheadlessrabbit on 2012-03-26
I'm having a problem where a program will work perfectly on my netbook which is running Lubuntu 11.04, but it will not work on my desktop which is running Ubuntu 11.10.

The software in question is for the wiring micro-controller. (Wiring in the predecessor to arduino - more info: [http://wiring.org.co/](http://wiring.org.co/))


On my netbook (running Lubuntu 11.04) I extracted the files into a folder (/home/kyle/wiring), double clicked the "wiring" script, it asked me if i wanted to display or execute, I chose execute, and it launched without issue.

I wanted to try it out on my desktop, I copied the same .tar.gz folder to the same directory (/home/kyle/wiring) and clicking the same "wiring" file. I was asked the same question about if I wanted to display or run, I chose "run", and... it does absolutely nothing.  

It just wont open or run on my desktop.


I tried using the terminal to open the script, and this is what I got:

> ~$ /home/kyle/wiring/wiring
~$ Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/kyle/wiring/java/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
   at java.lang.ClassLoader$NativeLibrary.load(Native Method)
   at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1803)
   at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1699)
   at java.lang.Runtime.load0(Runtime.java:770)
   at java.lang.System.load(System.java:1003)
   at java.lang.ClassLoader$NativeLibrary.load(Native Method)
   at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1803)
   at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1720)
   at java.lang.Runtime.loadLibrary0(Runtime.java:823)
   at java.lang.System.loadLibrary(System.java:1028)
   at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
   at java.security.AccessController.doPrivileged(Native Method)
   at java.awt.Toolkit.loadLibraries(Toolkit.java:1605)
   at java.awt.Toolkit.<clinit>(Toolkit.java:1627)
   at processing.app.Base.<clinit>(Base.java:427)
Could not find the main class: processing.app.Base.  Program will exit.

Don't know if this helps point out the problem or not, but something tells me the issue *might* be related to Java...


Any help would be greatly appreciated.  I know it seems like a rather minor bug when the software will work on another computer, (just use that one!) but I would really like to understand why it wont run on this one.

---

### Post by Kevbo on 2012-03-26
I had something similar with a file a while back.  It would not run if I tried to copy the already extracted files to a different computer, but if I copied and then extracted the original .tar file on the second computer everything worked fine.  Just thinking out loud here.

---

### Post by theheadlessrabbit on 2012-03-26
> **Kevbo said:**
> I had something similar with a file a while back.  It would not run if I tried to copy the already extracted files to a different computer, but if I copied and then extracted the original .tar file on the second computer everything worked fine.  Just thinking out loud here.

Sorry, bad wording on my part.  I didn't extract on one machine and copy all the files over to another. 

I copied the same Tar.gz file to each computer, then extracted the files from the copy of that Tar.gz file that was sent to that machine.

---

### Post by theheadlessrabbit on 2012-03-26
From the Wiring script:

> # If no JDK was installed with Processing then the script tries to use 
# the preferred Java version of the machine, i.e. what is executed 
# by the "java" console command. This must be a Sun JDK (for details, see
# [http://processing.org/reference/environment/platforms.html#java](http://processing.org/reference/environment/platforms.html#java)).

# In order to run Processing with an already installed JDK that is *not* 
# the preferred Java version of the machine, create a symlink named "java" 
# in the Processing installation directory that points to the JDK home
# directory.

# Thanks to Ferdinand Kasper for this build script. [fry]


# JARs required from JDK (anywhere in/below the JDK home directory)
JDKLIBS="rt.jar tools.jar"


Ubuntu does not have a Sun Java JDK in the repos, only OpenJDK, I've since installed SunJava, but I'm still having no luck.

There is a /java folder that came with the wiring software, is there somewhere I should be moving this folder?

I wonder why this isn't working in ubuntu, despite working out of the box in Lubuntu.

A little help would be good, as I am stumped.

---

### Post by theheadlessrabbit on 2012-03-28
I've been doing some more research into this issue.

Apparently, this same problem is very common with "processing", as well as wiring.  

According to various message boards, The issue seems to be that ubuntu 11.04 defaults to 32-bit java on a 64-bit system, and this leads to problems. (does that sound right?)

To test out this idea, I installed processing, and low and behold, I had the exact same issue with it failing to launch in Ubuntu 11.10

So I opened up the terminal and navigated over to my processing directory, and typed this:


> rm -Rf java
ln -sfn /opt/jdk1.6.0_29 java

And processing now works perfectly!

So I navigated over to the /wiring directory and typed the same thing into the terminal.

Now whenever I click on the "Wiring" script, I get a message asking me where it wants to save my sketches to, (Just like the first time using processing).  After selecting a location, nothing happens.  Wiring still wont load.

I do think I'm moving in a direction on this, (not sure if it's the right one or not...), but I really could use some guidance here. 

Anything I can post up here to give you guys some more info that might be helpful to sorting all this out?

---

