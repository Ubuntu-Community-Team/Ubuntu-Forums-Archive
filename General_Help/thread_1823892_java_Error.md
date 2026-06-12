---
title: "java Error"
date: 2011-08-12
forum: General Help
---

### Post by mrdec on 2011-08-12
I'm trying to run the java IDE jgrasp and getting an error. I installed the java jdk from sun and verified with java -version. At first running the jgrasp executable I had to go to src dir and the readme said to sudo apt-get install libxt-dev and then ./configure and ./Make.sh. And then I ran the executable which gave me the error below.

java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
Java HotSpot(TM) Server VM (build 21.0-b17, mixed mode)



java.lang.UnsatisfiedLinkError: /usr/lib/jvm/jdk1.7.0/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1928)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)
	at java.lang.Runtime.load0(Runtime.java:792)
	at java.lang.System.load(System.java:1059)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1928)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1846)
	at java.lang.Runtime.loadLibrary0(Runtime.java:845)
	at java.lang.System.loadLibrary(System.java:1084)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1648)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1670)
	at java.awt.EventQueue.invokeLater(EventQueue.java:1192)
	at javax.swing.SwingUtilities.invokeLater(SwingUtilities.java:1287)
	at Grasp.a(Grasp.java:8)
	at Grasp.main(Grasp.java:123)

---

### Post by scottstensland on 2011-08-12
evidently your jdk is not installed correctly,

---- how to install java jdk 7 on ubuntu ----

java jdk 7 can be downloaded from

[http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html](http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html)

choose the linux compressed binary
Once download completes move to location :

mv /whereever/its/now/jdk1.7.0 /usr/lib/jvm/jdk1.7.0

issue this to see what you currently have installed :

sudo update-alternatives --config java

if you currently only have one jdk version installed it will say something like:

 sudo update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
Nothing to configure.

add your new jdk to its list by issuing :

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.7.0/jre/bin/java X

where that ending X will determine Priority (lower will get picked first)
say 100, as long as existing Priority numbers are larger

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.7.0/jre/bin/java 100

now issue :
                                                                                                                           
sudo update-alternatives --config java

and pick the Selection number matching your desired jdk
verify using

java -version

java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
Java HotSpot(TM) Server VM (build 21.0-b17, mixed mode)

Then I downloaded jgrasp (picking the linux zip)
Define following environment variable to whichever dir jgrasp lives in :

export JGRASP_HOME=~/src/jgrasp    # <-- update to your path to jgrasp

launch using

~/src/jgrasp/bin/linux/jgrasp

this works for me

---

### Post by lbarowski on 2011-08-13
You don't need to build the sources. Binaries are provided for both 32 and 64 bit Intel Linux. I see that we neglected to remove the note in the "bin" README file that tells you that you need to build on 64 bit Linux (which was true until recently). I'll fix that for the next release. Actually, in the latest version of jGRASP you don't need to build the native parts for any system, though it will run more smoothly if you do (better system for killing user programs, ability to open associated files from the OS, or open files from the command line).

Also, you should launch using the bin/jgrasp script as the "bin" README file instructs. This will self-locate jGRASP, so you don't need to set the JGRASP_HOME environment variable. It will also add Java's tool.jar to the classpath, which is necessary for the debugger, interactions, etc. to work.

---

### Post by mrdec on 2011-08-15
Okay, I decided to mess around on an old laptop and installed 10.04 LTS instead of the previous 64bit on my desktop which I originally was trying to install.

I downloaded the Sun JDK binary version as detailed and extracted it. I then moved it to /usr/lib/jvm/jdk1.7.0. Did a sudo update-alternatives --config java and received an no alternatives for java. error. Did some searching and found to add these to /etc/bash.bashrc
JAVA_HOME=/usr/lib/jvm/java
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

After rebooting I did java -version and get:
java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
Java HotSpot(TM) Client VM (build 21.0-b17, mixed mode)

But trying to run jGrasp from /home/name/Documents/jGrasp/bin executing ./jgrasp I get exec: 213 : ./linux/jgrasp: not found.

---

### Post by mrdec on 2011-08-15
okay, downloaded the jdk and mv to /usr/lib/jvm/jdk1.7.0 and was getting some errors.

Tried to install from the instructions here: [http://happy-coding.com/install-sun-java6-jdk-on-ubuntu-10-04-lucid/](http://happy-coding.com/install-sun-java6-jdk-on-ubuntu-10-04-lucid/)

sudo update-alternatives --config java returns

There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure.

And java -version returns
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Client VM (build 20.1-b02, mixed mode, sharing)

Trying to launch ./jgrasp from jgrasp/bin gives the error:
exec: 213: ./linux/jgrasp: not found

---

### Post by mrdec on 2011-08-15
Does this error mean I need to set jgrasp path? Or create a symlink? Not sure what to set for either so any help would be greatly appreciated.

---

### Post by lbarowski on 2011-08-16
I suspect that your previous attempt to build the sources has deleted bin/linux/jgrasp, so you need to reinstall jGRASP.

---

### Post by mrdec on 2011-08-16
Thanks for the response. The original post was from my 64bit desktop install and the responses from yesterday were all on my 32bit laptop fresh install of 10.04LTS. I haven't built any jGrasp and it's all a fresh install. It appears that running the jGrasp script from jGrasp/bin can't find the executable in jGrasp/bin/linux.

---

### Post by lbarowski on 2011-08-17
That is a strange error. It may not mean what it appears to mean.

To bypass the script and get full capability, from the "bin" directory you would do:

./linux/jgrasp -Icp jgrasp.jar:<java_home>/lib/tools.jar -Ij ..

where <java_home> is replaced by the root directory of the Java installation.

I'd like your help to find out what is going wrong with the script though (assuming it is the script). If the above command works, use "Help" / "Report a Bug" to send a bug report and include your email address, then I'll send you a debug version of the script. If you can't get it running at all, email the bug report address on the jgrasp.org website on the "Contact Us" page and ask for it to be forwarded to me (Larry).

---

### Post by lbarowski on 2011-08-29
It turns out the error is due to the runtime linker (soft link to the real runtime linker) expected by our excutables compiled under LSB (Linux Standard Base) not being present. The simplest solution is probably to install lsb-core.

You could also just create a soft link in /lib64 or /lib from ld-lsb-x86-64.so.3 or ld-lsb.so.3 to the actual linker.

We'll update the startup script in the next jGRASP release to check for the presence of the linker and give a useful message if it is missing.

---

