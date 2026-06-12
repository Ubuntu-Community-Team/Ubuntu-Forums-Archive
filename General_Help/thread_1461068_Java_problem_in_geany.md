---
title: "Java problem in geany"
date: 2010-04-23
forum: General Help
---

### Post by geekster1987 on 2010-04-23
Hi
I'm not sure if i'm posting this in the correct place. I am trying to compile a .java in Geany but i keep getting the message: 
Compilation Failed
/bin/sh: javac:not Found
I am aware its a problem with the pathway to the java file but I am unsure how to solve it. I am using Jolicloud to run Geany also. Any help would be great.
Thanks

---

### Post by thebigob on 2010-04-23
DO you have java installed?

in a terminal type:

```

java -version

```

if not then 
```

sudo apt-get install sun-java6-jre

```

---

### Post by geekster1987 on 2010-04-23
I do have java installed. I think its just a path problem.

---

### Post by GregBrannon on 2010-04-23
You may want to try asking in an area frequented either by people using your operating system or in the Programming Talk forum.

I can suggest verifying that you have either Sun's Java Development Kit (JDK) which includes the Java Runtime Environment (JRE) or the preferred (by Ubuntans) Open JDK installed as a first step.  I don't know how to do that on your OS.

Good luck!

---

### Post by QIII on 2010-04-23
javac is the java compiler and is found in the jdk.

Did you install Java through Synaptic or in the CLI?

If you did, then you want to use the repos for the jdk as well.

```
sudo apt-get install sun-java6-jdk
```If you are currently running Lucid, be sure to enable the partner repo.

If you are running a previous version, be aware that the Java Update  version is a bit old and has some security issues.

If you installed from Sun's website, this should still work ... I think.

---

### Post by geekster1987 on 2010-04-23
I installed it in command line using 
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
I am not sure what lucid is which makes me assume i'm not using it. not really sure what you mean by repo's. 
Thanks

---

### Post by geekster1987 on 2010-04-23
Solved the problem by running the above suggested command line statement.
Thank you very much for the help.

---

