---
title: "problem reporting pentaho"
date: 2012-09-24
forum: General Help
---

### Post by hendri2201 on 2012-09-24
hi sir...

currently i'm trying to install Pentaho Reports for OpenERP which is refer from
[https://github.com/WillowIT/Pentaho-...rver/build.xml](https://github.com/WillowIT/Pentaho-...rver/build.xml)

i ever installed on some laptops which is Windows Based and it's working,
but currently i'm trying on UBuntu 11.04 OS, it prompted me error like this
"error build.xml:18: failed to create task or type.."

below is the steps i did :
1. install java-6-openjdk
comment : "apt-get install java-6-openjdk"

2. then i set installed java jdk into java_home environment
command: "nano /etc/environment"
add environment with this new line : JAVA_HOME="/usr/lib/jvm/java-6-openjdk"

3. I install apache ant
command : "apt-get install ant"

4. followed by setting the evnironment
command: "nano /etc/environment"
add environment with this new line : ANT_HOME="/usr/share/ant"

5. try to check installation with command "ant"...
I get message like this:
Buildfile: build.xml does not exist!
Build failed

6. then download java server from
[https://github.com/WillowIT/Pentaho-...rver/build.xml](https://github.com/WillowIT/Pentaho-...rver/build.xml)
and then copied to Ubuntu share folder
and then on command form, i goto extracted path which is share folder
i mentioned
and executed command "ant war "
and i got error message :
BUILD FAILED
/share/java_server/build.xml:18: problem: failed to create task or
type antlibrg:apacge.ivy.ant:retrieve
cause: The name is undefined.
Action:Check the spelling.
Action:Check that any custom taks/types have been declared
Action:Check that any <presetdef>/<macrodef>declarations have taken place.
No types or taks have been defined in this namespace yet

This appears to be an antlib declaration.
Action:Check that the implementing library exists in one of:
-/usr/share/ant/lib
-/root/.ant/lib
-a directory added on the command line with the -lib argument

Total time:0 seconds



is there any compability issue?
or i miss out some steps?

i'm in the some project to rush with for reporting, so please help me
to solve this issue
i look forward to your corporation to help me solve this issue,
thanks a lot in advance

Thx
Best Regards,:confused:

---

### Post by hendri2201 on 2012-09-24
up....

---

### Post by cain071546 on 2012-09-25
bump

---

