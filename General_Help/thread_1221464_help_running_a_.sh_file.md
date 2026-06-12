---
title: "help running a .sh file"
date: 2009-07-23
forum: General Help
---

### Post by matt12345 on 2009-07-23
Hi, I just tried to run a .sh file witch is converted from a .bat file. I gave it the permission to execute. 

```
matthew@matthew-desktop:~/Desktop/6$ ./launch-program.sh
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
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
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
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
./launch-program.sh: 2: Theme.jar: not found
matthew@matthew-desktop:~/Desktop/6$ 

```

---

### Post by doas777 on 2009-07-23
I think the problem is within your script (invoking something using the command 'java'). can you post the contents?

---

### Post by Q345 on 2009-07-23
Post the script.  Looks like the script is calling java but passing java the wrong parameters.  You'd get the same output if you made a script called test with the following inside:

tar

Assuming the executable permission is set, the script will run, but when it runs the tar line tar will complain that you haven't given the right options:

tar: You must specify one of the `-Acdtrux' options
Try `tar --help' or `tar --usage' for more information.

---

