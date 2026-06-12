---
title: "problem installing netbeans"
date: 2009-12-14
forum: General Help
---

### Post by ankit singh on 2009-12-14
I cannot install netneans 6.7. I ran the following command-

ankit@ankit-desktop:~$ chmod +x netbeans-6.7-ml-linux.sh
ankit@ankit-desktop:~$ ./netbeans-6.7-ml-linux.sh
bash: ./netbeans-6.7-ml-linux.sh: /bin/sh^M: bad interpreter: No such file or directory


after this i tried

ankit@ankit-desktop:~$ sh netbeans-6.7-ml-linux.sh
: not found7-ml-linux.sh: 37: 
: not found7-ml-linux.sh: 50: 
: not found7-ml-linux.sh: 74: 
: not found7-ml-linux.sh: 78: 
: not found7-ml-linux.sh: 86: 
: not found7-ml-linux.sh: 90: 
: not found7-ml-linux.sh: 108: 
: not found7-ml-linux.sh: 110: 
netbeans-6.7-ml-linux.sh: 112: initSymlinkArgument: not found
netbeans-6.7-ml-linux.sh: 115: parseCommandLineArguments: not found
netbeans-6.7-ml-linux.sh: 116: initializeVariables: not found
netbeans-6.7-ml-linux.sh: 117: setLauncherLocale: not found
netbeans-6.7-ml-linux.sh: 118: debugLauncherArguments: not found
netbeans-6.7-ml-linux.sh: 161: Syntax error: word unexpected (expecting "in")

:( help :(

---

### Post by lewisforlife on 2009-12-14
Forget the file you downloaded.  Try:
 
```
 
sudo apt-get install netbeans

```

---

### Post by cormano on 2009-12-14
6.8 is out. Repos only have 6.7, but anyway i've never had any trouble installing from the sh files in the official site. I just installed 6.8 actually, no problems at all.
I assume you have a working jvm in your path..?

---

### Post by piojunbabia on 2009-12-15
i donwloaded 6.8 and was sucessfully installed.. however later. it was removed when i tried to installed compizconfiguration-settings-manager. and i reinstalled again but this time not the 6.8 its 6.7.1.. but 6.8 is also working. Now i have 2 netbeans available to run, 6.8 and 6.7.1

just try that code, i believe its ready for karmic:
```
 sudo apt-get install netbeans
```

---

### Post by ankit singh on 2009-12-15
> **cormano said:**
> 6.8 is out. Repos only have 6.7, but anyway i've never had any trouble installing from the sh files in the official site. I just installed 6.8 actually, no problems at all.
I assume you have a working jvm in your path..?


I have a working jvm .

ankit@ankit-desktop:~$ which javac
/usr/bin/javac
ankit@ankit-desktop:~$ which java
/usr/bin/java

is there any way this problem can be solved?

---

### Post by lewisforlife on 2009-12-15
Is there a reason that you want to install the file that you downloaded and not just install netbeans from the repos?

---

