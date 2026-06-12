---
title: "need to convert a .bat script to a .sh script"
date: 2010-09-07
forum: General Help
---

### Post by linuxed on 2010-09-07
I'm attempting to compile a java application but the only script provided in the source is a .bat file.  I would greatly appreciate it if someone could post a .sh script that would accomplish the same tasks defined in the .bat script.  I only have limited experience with bash scripts so I'm unable to convert every line in the script below.  Thanks in advance.
```

@Echo Off
    If Not %1'==' Goto Begin
    Echo Manage the configuration of Japag
    Echo.
    Echo [CALL] JAPAG_MAKE command
    Echo.
    Echo        commands:
    Echo               /C - Compile sources only (default)
    Echo               /D - make javaDoc only
    Echo	       /A - compile + make javadoc (All)
    Echo	       /J - make a Jar
    Echo               /R - Run
    Echo               /L - cLean
    Goto End
   :Begin
    set JAVA=e:\programs\j2sdk1.4.1_01\bin\java
    set JAR=e:\programs\j2sdk1.4.1_01\bin\jar
    If %1'==' Goto Compile
    If %1'==/A' Goto Compile
    If %1'==/a' Goto Compile
    If %1'==/C' Goto Compile
    If %1'==/c' Goto Compile
    If %1'==/D' Goto Doc
    If %1'==/d' Goto Doc
    If %1'==/J' Goto Jar
    If %1'==/j' Goto Jar
    If %1'==/R' Goto Run
    If %1'==/r' Goto Run
    If %1'==/S' Goto Src
    If %1'==/s' Goto Src
    If %1'==/l' Goto Clean
    If %1'==/L' Goto Clean
    Goto End
   :Run
    If %2'==' Goto Test
    Echo RUN Japag ON %2
    %JAVA% -classpath e:\programs\javalibs\nanoxml-2.2.3.jar;. Japag.JapagXML %2
    Goto End
   :Test
    Echo RUN Japag ON test:japag_config.xml
    %JAVA% -classpath e:\programs\javalibs\nanoxml-2.2.3.jar;. Japag.JapagXML japag_config.xml japag.gif
    Goto End
   :Compile
    Echo COMPILATION
    %JAVA%c -classpath e:\programs\javalibs\nanoxml-2.2.3.jar Japag/args/*.java Japag/*.java
 
    If %1'==/A' Goto Doc
    If %1'==/a' Goto Doc
    Goto End
   :Doc
    Echo JAVADOC
    %JAVA%doc -overview JapagWP/japag_overview.html -classpath e:\programs\javalibs\nanoxml-2.2.3.jar -d JapagDoc Japag/*.java Japag/args/*.java
    Goto End
   :Jar
    Echo JARIFICATION
    %JAR% -cvf japag%2.jar Japag JapagDoc config JapagWP japag_make.bat japag_config.xml japag.gif japag.png japag.eps
    Goto End
   :Src
    Echo JARIFICATION OF SOURCES
    %JAR% -cvf japag%2-src.jar Japag/*.java Japag/*.gif Japag/args/*.java config japag_make.bat japag_config.xml
    Goto End
   :Clean
    Echo CLEAN
    del Japag\args\*.class Japag\args\*.java~	
    del Japag\*.class Japag\*.java~
    del config\*.*~
    del *.*~
    Goto End
   :End

```
**Edit**
There are a number of instances in the .bat script where it references a file at the location e:\programs\javalibs\nanoxml-2.2.3.jar.  Before the compilation begins the script should probably check for the existence of /usr/share/java/nanoxml2-2.2.3.jar and then echo an error message if it's missing.
```

if [ ! -e /usr/share/java/nanoxml2-2.2.3.jar ]; then
  echo "Package libnanoxml2-java is not installed"
  exit 1
fi

```

---

### Post by ender4 on 2010-09-07
I believe this should work:
```
JAVA=/usr/bin/java #may need to change this to directory of java binary
JAR=/usr/bin/jar   #may need to change this to directory of jar binary
JAVAC=/usr/bin/javac #may need to change this to directory of javac binary
JAVADOC=/usr/bin/javadoc #may need to change this to path of javadoc binary
NANOXMLPATH=/usr/share/java/nanoxml12-2.2.3.jar  #or whatever the path is for nanoxml
if [ ! -e /usr/share/java/nanoxml2-2.2.3.jar ]; then
  echo "Package libnanoxml2-java is not installed"
  exit 1
fi
function my_begin {
        
        case $1 in
                -A|-a|-C|-c) my_compile ;;
                -D|-d) my_doc ;;
                -J|-j) my_jar ;;
                -R|-r) my_run ;;
                -S|-s) my_src ;;
                -l|-L) my_Clean ;;
        esac
        exit
}
function my_run {
        if (( $# < 2 )) 
        then
        my_test
        fi
        echo RUN Japag ON $2
        $JAVA -classpath $NANOXMLPATH Japag.JapagXML $2 
}
function my_test {
        echo RUN Japag ON test:japag_config.xml
        $JAVA -classpath $NANOXMLPATH Japag.JapagXML japag_config.xml japag.gif
}
function my_compile {
        echo COMPILATION
        $JAVAC -classpath $NANOXMLPATH Japag/args/*.java Japag/*.java
        if [[ $1 == '-A' || $1 == '-a' ]]
        then
        my_doc
        fi
}
function my_doc {
        echo JAVADOC
        $JAVADOC -overview JapagWP/japag_overview.html -classpath $NANOXMLPATH -d JapagDoc Japag/*.java Japag/args/*.java
}
function my_jar {
        echo JARIFICATON
        $JAR -cvf japag"$2".jar Japag JapagDoc config JapagWP japag_make.bash japag_config.xml japag.gif japag.png japag.eps
}
function my_src {
        echo JARIFICATION OF   SOURCES
        $JAR -cvf japag$2-src.jar Japag/*.java Japag/*.gif Japag/args/*.java config japag_make.bash japag_config.xml 
}
function my_clean {
        echo CLEAN
        rm Japag/args/*.class Japag/args/*.java~
        rm Japag/*.class Japag/*.java~
        rm config/*.*~
        rm *.*~
}
if (( $# > 0 )) 
then
my_begin
fi
echo 'Manage the configuration of Japag

 [CALL] JAPAG_MAKE command

        commands:
              -C - Compile sources only (default)
              -D - make javaDoc only
	      -A - compile + make javadoc (All)
	      -J - make a Jar
              -R - Run
              -L - cLean'
exit

                
```

---

### Post by linuxed on 2010-09-07
Thanks for posting the script.  Unfortunately I seem to be having trouble getting it to work with command line parameters.  I corrected a few typos (NANOXMLPATH and added quotes around the echo commands) but it still isn't working right.  If I run the script as ./test.sh then it successfully outputs the help message.  If I add a parameter to the command it doesn't output anything.  ./test.sh -c just returns to the command line, it doesn't even output the "COMPILATION" string.
```

#!/bin/bash

JAVA=/usr/bin/java #may need to change this to directory of java binary
JAR=/usr/bin/jar   #may need to change this to directory of jar binary
JAVAC=/usr/bin/javac #may need to change this to directory of javac binary
JAVADOC=/usr/bin/javadoc #may need to change this to path of javadoc binary
NANOXMLPATH=/usr/share/java/nanoxml2-2.2.3.jar  #or whatever the path is for nanoxml
if [ ! -e $NANOXMLPATH ]; then
  echo "Package libnanoxml2-java is not installed"
  exit 1
fi

function my_begin {
        
        case $1 in
                -A|-a|-C|-c) my_compile ;;
                -D|-d) my_doc ;;
                -J|-j) my_jar ;;
                -R|-r) my_run ;;
                -S|-s) my_src ;;
                -l|-L) my_Clean ;;
        esac
        exit
}
function my_run {
        if (( $# < 2 )) 
        then
        my_test
        fi
        echo "RUN Japag ON $2"
        $JAVA -classpath $NANOXMLPATH Japag.JapagXML $2 
}
function my_test {
        echo "RUN Japag ON test:japag_config.xml"
        $JAVA -classpath $NANOXMLPATH Japag.JapagXML japag_config.xml japag.gif
}
function my_compile {
        echo "COMPILATION"
        $JAVAC -classpath $NANOXMLPATH Japag/args/*.java Japag/*.java
        if [[ $1 == '-A' || $1 == '-a' ]]
        then
        my_doc
        fi
}
function my_doc {
        echo "JAVADOC"
        $JAVADOC -overview JapagWP/japag_overview.html -classpath $NANOXMLPATH -d JapagDoc Japag/*.java Japag/args/*.java
}
function my_jar {
        echo "JARIFICATON"
        $JAR -cvf japag"$2".jar Japag JapagDoc config JapagWP japag_make.bash japag_config.xml japag.gif japag.png japag.eps
}
function my_src {
        echo "JARIFICATION OF SOURCES"
        $JAR -cvf japag$2-src.jar Japag/*.java Japag/*.gif Japag/args/*.java config japag_make.bash japag_config.xml 
}
function my_clean {
        echo "CLEAN"
        rm Japag/args/*.class Japag/args/*.java~
        rm Japag/*.class Japag/*.java~
        rm config/*.*~
        rm *.*~
}
if (( $# > 0 )) 
then
my_begin
fi
echo "Manage the configuration of Japag

 [CALL] JAPAG_MAKE command

        commands:
              -C - Compile sources only (default)
              -D - make javaDoc only
	      -A - compile + make javadoc (All)
	      -J - make a Jar
              -R - Run
              -L - cLean"
exit

```

---

