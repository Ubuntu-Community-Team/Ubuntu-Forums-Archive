---
title: "Need help in running Java command...."
date: 2011-11-22
forum: General Help
---

### Post by MaquinaX on 2011-11-22
Hello Everyone,
      Ok, this one is for the Java gurus. I'm in the process of making a full change-over from W$N to ubuntu. Currently running Xubuntu, but this should not matter when running the java command, I'm assuming ;).
My company developed a java based program to keep track of our hardware based inventory. When running this through windows, the folder resides directly on C: drive, and from what I can tell, it then call out to start Java, and then indicates the java.jar packages that it's calling for....
Here is the .bat file info:

"start java -classpath lib\techdata.jar;lib\cloudscape.jar;lib\cloudclient.jar;lib\classes12.zip com.companyname.techdata.ui.JMainFrame"

I tried running the same command through terminal, but just calling java, and then removing the lib\.... as lib is just a folder withing the original folder. This is what I get:

jc@XubTechx:~/TechData/lib$ java -classpath techdata.jar;cloudscape.jar;cloudclient.jar;classes12.zip com.companyname.techdata.ui.JMainFrame
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32	  use a 32-bit data model if available
    -d64	  use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -jamvm	  to select the "jamvm" VM
    -cacao	  to select the "cacao" VM
    -zero	  to select the "zero" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
    -shark	  is a synonym for the "zero" VM  [deprecated]
                  The default VM is server,
                  because you are running on a server-class machine.


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
See [http://java.sun.com/javase/reference](http://java.sun.com/javase/reference) for more details.
cloudscape.jar: command not found
cloudclient.jar: command not found
classes12.zip: command not found

How can I modify the command so that it runs properly through linux terminal?? Thanx in advance.


JC

---

### Post by Azdour on 2011-11-22
Hi,

The classpath on Linux is separated by the ':' character not the ';' character and paths use the '/' separator. Try this in the TechData directory not the lib directory, and hopefully it should work:

```
java -classpath ./lib/techdata.jar:./lib/cloudscape.jar:./lib/cloudclient.jar:./lib/classes12.zip com.companyname.techdata.ui.JMainFrame
```

---

