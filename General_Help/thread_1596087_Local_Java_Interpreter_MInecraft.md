---
title: "Local Java Interpreter? MInecraft?"
date: 2010-10-13
forum: General Help
---

### Post by hantechbl on 2010-10-13
I know I have java installed but I'm trying to run a script that requiers the Java interpreter in the code:
```
#!/bin/sh

JAVA=/System/Library/Frameworks/JavaVM.framework/Versions/1.6/Home/bin/java

DIR=`echo $0 | sed -E 's/\/[^\/]+$/\//'`
if [ "X$0" != "X$DIR" ]; then
	cd $DIR
fi

RUN=true
while [ $RUN == "true" ]; do
	$JAVA -classpath skin:lib/jinput.jar:lib/lwjgl.jar:lib/lwjgl_util.jar:lib/wom.jar:lib/minecraft.jar -Djava.library.path=native/macosx -Dsun.java2d.noddraw=true -Dsun.awt.noerasebackground=true -Dsun.java2d.d3d=false -Dsun.java2d.opengl=false -Dsun.java2d.pmoffscreen=false -Xmx800M Main
	if [ $? -ne 10 ]; then RUN=false; fi
done


```
This is World of minecraft wrapper and I"m wondering how to get this mac osx script working in linux.  It says I just need to change java path.....

---

### Post by man-man on 2010-12-04
I got as far as finding the java executable (in /usr/lib/jvm/java-6-openjdk/jre/bin), and editing that into the script, but it's not doing much of anything.

Bumping & subscribing... there has to be someone who's gotten this thing working, li'l help?

---

