---
title: "Java -Xms and -Xmx don't work"
date: 2010-12-24
forum: General Help
---

### Post by Drakmor on 2010-12-24
Hi, I'm trying to increase the size of my java heap. I've done some research and found that I need to use java -Xmx to change it. However, when I put in that command, I get the following.

```
$ java -Xmx800m
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32          use a 32-bit data model if available
    -d64          use a 64-bit data model if available
    -client       to select the "client" VM
    -server       to select the "server" VM
    -cacao        to select the "cacao" VM
    -zero         to select the "zero" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.

    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions with specified granularity
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions with specified granularity
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                  see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
See http://java.sun.com/javase/reference for more details.

```

Which makes me think I'm putting in the wrong command. Anyone have an idea about what's going on? I'm running Kubuntu 10.04. Thanks!

---

### Post by daredevil82 on 2010-12-24
You're not adding the class or jar to execute.  What you've written calls the java vm, allocates 800MB to it, but no program or arguments are passed onto the VM.

---

### Post by Drakmor on 2010-12-24
Ok, thanks! To make sure I understand what you mean, you're saying that what I need to do is go into the folder with the jar, then do the command with the name of the jar at the end?

---

### Post by Nytram on 2010-12-24
Yes you set the heap for each jar file you want to run, it's not a global setting.

Navigate to the directory containing the jar file and use something like this:

> 
java -Xmx800m -jar yourjarfile.jar


---

### Post by idi0tf0wl on 2010-12-27
> **Nytram said:**
> Yes you set the heap for each jar file you want to run, it's not a global setting.

Navigate to the directory containing the jar file and use something like this:
This is correct. If you don't want to type it out each time (i.e. you know you're gonna want to run that program with those settings every time) you can edit your ~/.bashrc to include the following lines (look for the section that has a few lines starting with the word alias):
```
alias command='java -jar -Xmx800m /pathto/file.jar'
```
where "command" is the single-word command with which you want to run the application and /pathto/file.jar is, well, the path to the jar file. Make sure the last bit there has the single-quote around it, or it will most assuredly do nothing at all.

Save your changes, log in again, and run the command you specified. Should do the trick for you. Cheers!

---

### Post by Drakmor on 2010-12-27
I've figured it out, thanks everyone! This can be closed now....

---

### Post by idi0tf0wl on 2010-12-27
> **Drakmor said:**
> I've figured it out, thanks everyone! This can be closed now....
Please just mark it as [SOLVED].

Glad to hear you got it worked out!

---

