---
title: "Change java version for specific programs?"
date: 2010-02-01
forum: General Help
---

### Post by bmfc187 on 2010-02-01
Hi, i have a question about java...

I have been toying around with Android development, and the android build system requires jdk5.0 to build.  which is fine.  i have it setup correctly and working.  no problems there.  

Now i also use a multi-site torrent search application called Cloudburst.  Cloudburst does not like java 5.  it depends on java 6 and will only run on java 6.  

so my problem is that if i want to use cloudburst i hafta do 

```
java update-alternatives -s [whatever-java6-is]
```and it all works fine on java 6, but then if i wanna go do my Android thing, then i hafta reset it back to java5 again and its TIRING...

is there ANY way for me to set the java version for cloudburst to use independently from everything else?  or to set it to java5 ONLY for the Android Build System?  either way...i just dont know of any other way to switch the version and i dont even know if i CAN set program-specific java versions...just kinda hoping.  any ideas? thanks in advance...

-BMFC

---

### Post by ratcheer on 2010-02-01
You could try wrapping your invocation of the app that needs a special Java version in a bash script that resets the PATH environment variable to prepend the special JAVA_HOME/bin. Then, when you finished using that app and exited, your PATH would go back to its normal setting, pointing to the other JAVA_HOME/bin.

Or, something like that. Hope this helps.

Tim

---

### Post by bmfc187 on 2010-02-01
ok well the program is a jar file (cloudburst.jar) and thats the way it comes so you hafta invoke it thru terminal with 

```
java -jar cloudburst.jar
```and i made an executable file called cloudburst and said

```
cd cloudburst
java -jar cloudburst.jar
```so i can add the program to the applications menu. 

EDIT:  i added to the beginning of the file:

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.16/bin/java
```

it didnt work.  so what? did i do it wrong or gotta do it differently?  thanks...

-BMFC

---

### Post by bmfc187 on 2010-02-01
bump..

anybody? nobody knows the command to make one separate program run on java6 while all others run on java5?

-BMFC

---

### Post by bmfc187 on 2010-02-01
bump...

-BMFC

---

### Post by ratcheer on 2010-02-02
It doesn't matter what JAVA_HOME is, just what is in your PATH.

Take out the export JAVA_HOME. Put in:

```
PATH=/usr/lib/jvm/java-6-sun-1.6.0.16/bin:$PATH
```

(Assuming that is the correct Java path). Then call your program.

Tim

---

