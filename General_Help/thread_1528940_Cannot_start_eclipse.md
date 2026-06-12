---
title: "Cannot start eclipse"
date: 2010-07-11
forum: General Help
---

### Post by outleradam on 2010-07-11
I was attempting to add repositories to java from the java website and from the Synaptic Package Manger with an emphasis on using a serial port in java.  Something went horribly wrong.

Eclipse will not start.  I dropped to the command line and did this:
```
adam@adam-desktop:/usr/local/jdk1.1.7/bin$ eclipse
dirname: invalid option -- 'p'
Try `dirname --help' for more information.
dirname: invalid option -- 'p'
Try `dirname --help' for more information.
java was not found in /usr/local/jdk1.1.7/bin/x86_64/green_threads/java
```Then I did some reading and found this:
```
adam@adam-desktop:/usr/local/jdk1.1.7/bin$ eclipse -vm /usr/bin/java
```But when eclipse does start it is inoperable. It states "Could not open the editor: No editor descriptor for id org.eclipse.jdt.ui.CompilationUnitEditor" and I have no project sidebar.

I really need help.  I don't know what to do!

---

### Post by bumanie on 2010-07-11
Looks as though something has gone terribly wrong with the downloading of eclipse. To get rid of the eclipse package and its configuration files, use this in terminal> sudo apt-get --purge remove eclipse and then try to download eclipse again.

---

### Post by outleradam on 2010-07-11
I tried that just now.  It did not work.  apt-get purge eclipse, apt-get install eclipse did nothing to the problem.

Ok, apparently the problem is in my JAVA_HOME="/usr/local/jdk1.6.0"  variable.    Eclipse is looking for /usr/local/jdk1.1.7/bin/x86_64/green_threads/java but that folder does not exist.

I have ```
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 appletviewer -> .java_wrapper
-rwxr-xr-x 1 root root 6429 2010-07-10 23:54 checkVersions
lrwxrwxrwx 1 root root    4 2010-07-10 23:54 i386 -> i686
lrwxrwxrwx 1 root root    4 2010-07-10 23:54 i486 -> i686
lrwxrwxrwx 1 root root    4 2010-07-10 23:54 i586 -> i686
drwxr-xr-x 4 root root 4096 2010-07-10 23:54 i686
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 jar -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 java -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javac -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javac_g -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javadoc -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 java_g -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javah -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javah_g -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javakey -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javap -> .java_wrapper
-r-xr-xr-x 1 root root 1612 2010-07-10 23:54 java-rmi.cgi
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javaverify -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 javaverify_g -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 jdb -> .java_wrapper
-r-xr-xr-x 1 root root 1943 2010-07-10 23:54 jre
lrwxrwxrwx 1 root root    3 2010-07-10 23:54 jre_g -> jre
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 native2ascii -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 rmic -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 rmiregistry -> .java_wrapper
lrwxrwxrwx 1 root root   13 2010-07-10 23:54 serialver -> .java_wrapper

```

so I did ```
adam@adam-desktop:/usr/local/jdk1.1.7/bin$ sudo ln -s i686 x86_64 

```

but eclipse still would not start up

```
adam@adam-desktop:/usr/local/jdk1.1.7/bin/x86_64/green_threads$ eclipse
dirname: invalid option -- 'p'
Try `dirname --help' for more information.
dirname: invalid option -- 'p'
Try `dirname --help' for more information.
/usr/local/jdk1.1.7/bin/x86_64/green_threads/java: error while loading shared libraries: libjava.so: cannot open shared object file: No such file or directory

```

What else can I try?  Eclipse will not start.

---

### Post by outleradam on 2010-07-11
I was able to get it running by typing

```
eclipse -vm /usr/bin
```  but how to get it working like it did before?

---

### Post by outleradam on 2010-07-11
I'm sure this will help me 

```

fakeroot make-jpkg jdk-1_4_2-linux-i586.bin
sudo dpkg -i sun-j2sdk1.4.2.15_i386.deb 
sudo update-alternatives --config java  
```

---

### Post by outleradam on 2010-08-04
I'm still having this problem

I would really like some help  the command 2 posts up is no longer working.  There is a problem with permissions somewhere
sudo eclipse works
eclipse does not work


still the same problem

```
adam@adam-desktop:/usr/lib/jvm/java-6-sun/lib$ eclipse
dirname: invalid option -- 'p'
Try `dirname --help' for more information.
dirname: invalid option -- 'p'
Try `dirname --help' for more information.
/usr/local/jdk1.1.7/bin/x86_64/green_threads/java: error while loading shared libraries: libjava.so: cannot open shared object file: No such file or directory

```

---

### Post by outleradam on 2010-08-04
it even works when I type

```
sudo -u adam eclipse
```

It has to be the elevated permissions.   What could be the problem?

---

### Post by outleradam on 2010-08-05
PATH=/usr/lib/jvm/java-6-sun-1.6.0.20/bin:$PATH

---

