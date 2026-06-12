---
title: "installing java"
date: 2009-07-04
forum: General Help
---

### Post by asliyanage on 2009-07-04
i have installed java using 
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts

and i edit the this file also.
sudo gedit /etc/environment

now my file is look like this
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/local/Java/jdk1.5.0_07"
CLASSPATH="/usr/local/Java/jdk1.5.0_07/lib:."

now if i type which java in terminal it gives this

asliyanage@2006cs119:~$ which java
/usr/bin/java
asliyanage@2006cs119:~$ 



but still if i type javac in my terminal it gives this

asliyanage@2006cs119:~$ javac
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.3
 * java-gcj-compat-dev
 * gcj-4.2
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found
asliyanage@2006cs119:~$

---

### Post by michy99 on 2009-07-04
What is the output of this command?```
sudo find / -name 'javac'
```

---

### Post by asliyanage on 2009-07-04
/media/disk/Program Files/Java/jdk1.6.0/sample/javac

---

### Post by michy99 on 2009-07-04
It looks like you have java5 and java6 both installed. The link at /usr/bin/java is pointing at java5. You probably don't have the jdk installed for java5, which is why it can't find javac. There are several ways to fix this, but the best might be to uninstall all java and then install java6 again.

Edit: I just realized that the javac you found with the find command is probably on your Windows partition. So I am not sure that java6 even is installed on your Ubuntu system.

---

### Post by kpkeerthi on 2009-07-04
> **asliyanage said:**
> i have installed java using 
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts

and i edit the this file also.
sudo gedit /etc/environment

now my file is look like this
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/local/Java/jdk1.5.0_07"
CLASSPATH="/usr/local/Java/jdk1.5.0_07/lib:."

now if i type which java in terminal it gives this

asliyanage@2006cs119:~$ which java
/usr/bin/java
asliyanage@2006cs119:~$ 



but still if i type javac in my terminal it gives this

asliyanage@2006cs119:~$ javac
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.3
 * java-gcj-compat-dev
 * gcj-4.2
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found
asliyanage@2006cs119:~$

You have choose the default JDK and activate it. See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) for instructions.

---

### Post by asliyanage on 2009-07-04
how to uninstall jdk 1.6

---

### Post by asliyanage on 2009-07-04
but when i type this it gives thie
sudo update-java-alternatives -l

"


asliyanage@2006cs119:~$ sudo update-java-alternatives -l
[sudo] password for asliyanage: 
java-6-sun 63 /usr/lib/jvm/java-6-sun
asliyanage@2006cs119:~$ 

"
what should i doooooo.still javac not working?

---

### Post by txcrackers on 2009-07-04
First, undo whatever editing you did to add "CLASSPATH" and "JAVA_HOME" to your environment. CLASSPATH hasn't been required for general Java usage since 1.3 and JAVA_HOME is only required for those applications that need to compile Java on the fly (i.e. Tomcat) -- and there's better ways of managing that instead of mucking up the system environment.

Secondly, remove ALL packages that even mention Java. Don't worry about other programs, like the OpenOffice integration, getting removed. Just make a note of them so you can re-install them. Now, install *sun-java6-plugin sun-java6-jdk sun-java6-fonts* and you shouldn't have to use the **update-alternatives** at all because that's the only Java you have on your system. (Note that there is **not** a system reboot or even a logout in these hints.)

You shouldn't need to install Java 5 as all Java versions are (technically) backwards-compatible with previous versions.

---

### Post by asliyanage on 2009-07-04
can you tell me how to remove packages related java?actually i don't know how to rmove?

---

### Post by credobyte on 2009-07-05
```
sudo apt-get remove --purge sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
```

---

### Post by asliyanage on 2009-07-05
i rmove java.here are the what i did

"
asliyanage@2006cs119:~$ sudo apt-get remove --purge sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
[sudo] password for asliyanage: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not installed, so not removed
Package sun-java6-fonts is not installed, so not removed
The following packages were automatically installed and are no longer required:
  java-common unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sun-java6-bin* sun-java6-jre* sun-java6-plugin*
0 upgraded, 0 newly installed, 3 to remove and 143 not upgraded.
After this operation, 99.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104638 files and directories currently installed.)
Removing sun-java6-plugin ...
Removing sun-java6-bin ...
Purging configuration files for sun-java6-bin ...
Removing sun-java6-jre ...
Purging configuration files for sun-java6-jre ...
Processing triggers for shared-mime-info ...
asliyanage@2006cs119:~$ 

"

---

### Post by credobyte on 2009-07-05
```
Package sun-java6-jdk is not installed, so not removed
Package sun-java6-fonts is not installed, so not removed
```

Wait ! You said you installed JDK ?

Open terminal and paste in this command :
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk
```
Afterwards, post the output here !

---

### Post by asliyanage on 2009-07-05
you told to install these.
 sun-java6-plugin sun-java6-jdk sun-java6-fonts 

[COLOR="Red"]is it ok to without jre[/COLOR]

---

### Post by credobyte on 2009-07-05
> **asliyanage said:**
> you told to install these.
 sun-java6-plugin sun-java6-jdk sun-java6-fonts 

[COLOR=Red]is it ok to without jre[/COLOR]

Take a look at my previous post again and please, post the output so we could verify your installation process ( as it looks like your previous JDK installation failed ).

---

### Post by asliyanage on 2009-07-05
here are the what i did.it asking  some are mising
"


asliyanage@2006cs119:~$ sudo apt-get install  sun-java6-plugin sun-java6-jdk sun-java6-fonts 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-demo sun-java6-doc sun-java6-source
The following NEW packages will be installed:
  sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
0 upgraded, 5 newly installed, 0 to remove and 143 not upgraded.
Need to get 17.5MB/52.2MB of archives.
After this operation, 156MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) jaunty/multiverse sun-java6-jdk 6-13-1
  Could not resolve 'lk.archive.ubuntu.com'
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) jaunty/multiverse sun-java6-fonts 6-13-1
  Could not resolve 'lk.archive.ubuntu.com'
Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jdk_6-13-1_i386.deb](http://lk.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jdk_6-13-1_i386.deb)  Could not resolve 'lk.archive.ubuntu.com'
Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-fonts_6-13-1_all.deb](http://lk.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-fonts_6-13-1_all.deb)  Could not resolve 'lk.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


"

---

### Post by credobyte on 2009-07-05
```
System -> Administration -> Software Sources

```
Change the server to something else ( Main would be the best choice, IMO ) and try installing java again.

---

### Post by asliyanage on 2009-07-05
in default Adminiistration->software resource and ubuntu software tab Download from is selected for "S[COLOR="Red"]erver from sri lanka[/COLOR]".
is it the error

---

### Post by credobyte on 2009-07-05
> **asliyanage said:**
> in default Adminiistration->software resource and ubuntu software tab Download from is selected for "S[COLOR=Red]erver from sri lanka[/COLOR]".
is it the error

Change it to something more obvious ( USA, UK, France .. ) - no need to do experiments when you are trying to solve a problem :)

---

### Post by asliyanage on 2009-07-05
[COLOR="Blue"]Thanks macnang,it is working

"
is it need to set class path and path variables or not?[/COLOR]

asliyanage@2006cs119:~$ javac
Usage: javac <options> <source files>
where possible options include:
  -g                         Generate all debugging info
  -g:none                    Generate no debugging info
  -g:{lines,vars,source}     Generate only some debugging info
  -nowarn                    Generate no warnings
  -verbose                   Output messages about what the compiler is doing
  -deprecation               Output source locations where deprecated APIs are used
  -classpath <path>          Specify where to find user class files and annotation processors
  -cp <path>                 Specify where to find user class files and annotation processors
  -sourcepath <path>         Specify where to find input source files
  -bootclasspath <path>      Override location of bootstrap class files
  -extdirs <dirs>            Override location of installed extensions
  -endorseddirs <dirs>       Override location of endorsed standards path
  -proc:{none,only}          Control whether annotation processing and/or compilation is done.
  -processor <class1>[,<class2>,<class3>...]Names of the annotation processors to run; bypasses default discovery process
  -processorpath <path>      Specify where to find annotation processors
  -d <directory>             Specify where to place generated class files
  -s <directory>             Specify where to place generated source files
  -implicit:{none,class}     Specify whether or not to generate class files for implicitly referenced files 
  -encoding <encoding>       Specify character encoding used by source files
  -source <release>          Provide source compatibility with specified release
  -target <release>          Generate class files for specific VM version
  -version                   Version information
  -help                      Print a synopsis of standard options
  -Akey[=value]              Options to pass to annotation processors
  -X                         Print a synopsis of nonstandard options
  -J<flag>                   Pass <flag> directly to the runtime system

"

---

### Post by credobyte on 2009-07-05
You don't need to set environment tables ( like on Windows XP ) ! They should be available through [COLOR=Blue]/usr/bin/env java[/COLOR] ( [COLOR=Blue]/usr/bin/env javac[/COLOR] ) !
Compile with javac ( man javac if you need some help ) and you'll be fine ;)

---

### Post by asliyanage on 2009-07-05
machang i was tring to open that file using 
 sudo gedit  /usr/bin/env java 

but is says 
[COLOR="Red"]"
Could not open the file /user/bin/java

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
"[/COLOR]

the current selected character encoding is CURRENT LOCAL UTF-8

---

### Post by asliyanage on 2009-07-05
but if i use vi to open that it gives this

"

^@^@Usage: %s [OPTION]... [-] [NAME=VALUE]... [COMMAND [ARG]...]
^@^@^@Set each NAME to VALUE in the environment and run COMMAND.

  -i, --ignore-environment   start with an empty environment
  -u, --unset=NAME           remove variable from the environment
^@      --help     display this help and exit
^@^@^@^@      --version  output version information and exit
^@^@^@
A mere - implies -i.  If no COMMAND, print the resulting environment.
^@
Report bugs to <%s>.
^@bug-coreutils@gnu.org^@/usr/share/locale^@David MacKenzie^@Richard Mlynarik^@6.10^@GNU coreutils^@env^@+iu:^@ignore-environment^@unset^@help^@version^@^@^@¸Î^D^H^@^@^@^@^@^@^@^@i^@^@^@ËÎ^D^H^A^@^@^@^@^@^@^@u^@^@^@ÑÎ^D^H^@^@^@^@^@^@^@^@~ÿÿÿÖÎ^D^H^@^@^@^@^@^@^@^@}ÿÿÿ^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@%s (%s) %s
^@%s %s
^@(C)^@Written by %s.
^@Written by %s and %s.
^@Written by %s, %s, and %s.
^@^@^@
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

^@^@^@Written by %s, %s, %s,
and %s.
^@Written by %s, %s, %s,
%s, and %s.
^@Written by %s, %s, %s,
%s, %s, and %s.
^@Written by %s, %s, %s,
%s, %s, %s, and %s.
^@Written by %s, %s, %s,
%s, %s, %s, %s,
and %s.
^@Written by %s, %s, %s,
%s, %s, %s, %s,
%s, and %s.
^@Written by %s, %s, %s,
"

---

### Post by credobyte on 2009-07-05
Why you want to open it ? /usr/bin/env is not a file ;)

java & javac commands can be used without any additional configuration ! If you have a program where you need to set Java path, set it to [COLOR=Blue]/usr/bin/env java[/COLOR] ( or [COLOR=Blue]/usr/bin/env javac[/COLOR] if you need a compiler ).
And again - you don't need to modify anything .. everything is up and running :)

---

