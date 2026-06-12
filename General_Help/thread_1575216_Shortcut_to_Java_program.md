---
title: "Shortcut to Java program"
date: 2010-09-15
forum: General Help
---

### Post by MarekS on 2010-09-15
How to make a shortcut to a program?

It's a Java program started by a shell script
[FONT=Courier New]
#!bin/sh
java -jar LinShredder.jar

[FONT=Verdana]It starts okay in its original folder, but when I link to it from e.g. the desktop it doesn't work.[/FONT]
[/FONT]

---

### Post by krishnandu.sarkar on 2010-09-15
Java should work from anywhere. How did you installed it..??

---

### Post by endotherm on 2010-09-15
in what way specifically does it "not work"? 
are there messages? is the java command unable to find the jar, or is the jar starting with the wrong env var for $PATH?

---

### Post by MarekS on 2010-09-15
> **krishnandu.sarkar said:**
> Java should work from anywhere. How did you installed it..??

I installed it "manually" as its a commercial program. And it works fine, but I want to create a shortcut to it.

I suppose I need to add the precise location of the file, something like
[FONT=Courier New]
#!/bin/sh
java -jar /home/marek/Chess/Shredder12/LinShredder.jar[/FONT]

Except that it can't be that exactly, because it doesn't work.

---

### Post by endotherm on 2010-09-15
> **MarekS said:**
> I installed it "manually" as its a commercial program. And it works fine, but I want to create a shortcut to it.

I suppose I need to add the precise location of the file, something like
[FONT=Courier New]
#!/bin/sh
java -jar /home/marek/Chess/Shredder12/LinShredder.jar[/FONT]

Except that it can't be that exactly, because it doesn't work.
try testing it from a terminal. remember, paths in linux are case sensitive. 
also is this a script file or did you put both these lines into the command box for a launcher? usually in that case, it is best to write teh script seperately and just point the launcher to the script, which then launches the app.

---

### Post by MarekS on 2010-09-15
> **endotherm said:**
> in what way specifically does it "not work"? 
are there messages? is the java command unable to find the jar, or is the jar starting with the wrong env var for $PATH?

I make a link to the script, drag that to the desktop, double-click on it, press Run - but nothing happens. In the original folder I press Run and it starts fine. I haven't defined any paths.

---

### Post by Finalfantasykid on 2010-09-15
```
#!/bin/sh
cd ~/Chess/Shredder12/
java -jar LinShredder.jar
```

Try that.  It should make the shell script actually go to that directory, and then run the java program as if you were actually launching the script from that folder.

---

### Post by krishnandu.sarkar on 2010-09-15
Ya that's why it's not working as you have installed it manually. You need to set PATH. I don't know how to do this.

But you should have you sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

It would have done everything.

Anyway as you have already installed wait for other members to come in and guide how to add path.

---

### Post by MarekS on 2010-09-15
> **Finalfantasykid said:**
> ```
#!/bin/sh
cd ~/Chess/Shredder12/
java -jar LinShredder.jar
```Try that.  It should make the shell script actually go to that directory, and then run the java program as if you were actually launching the script from that folder.

Thanks! That did the trick.

One last question. How can I get it to skip the dialog "Do you want to run... or display its contents?"? I just want it to run.

---

### Post by Finalfantasykid on 2010-09-15
I think changing the permissions of the shell file so that it is executable will allow it to automatically run, although I am not 100% sure on that.

```
chmod +x shellScript.sh
```

Or you can right click on the shell script and go to the permissions tab and check "Allow executing file as program".

---

### Post by luigi_mb on 2010-09-15
Unless the program is just one .jar file and nothing else, in which case the suggestions in this thread apply, you should create a shell script, with something like

```

#! /bin/bash
cd [full-path-to-program-dir]
java -jar [program].jar

```

Another solution is to add "-cp ...." to the command line, as in

```

java -cp .... -jar [program].jar

```

replacing .... with the classes contained in the main jar.


/luigi

---

### Post by lykeion on 2010-09-16
Instead of hard-coding the path to program dir, you can have a more generic solution like this:
[PHP]#!/usr/bin/env bash
#resolve directory absolute path
SCRIPTPATH=$(echo $0 | sed s/.*\\///g)
if [ "$0" = "./$SCRIPTPATH" ];then
    ABSPATH=$(echo `pwd`/$0 | sed "s/\/$SCRIPTPATH//g" | sed 's/\/\.//g')
else
    ABSPATH=$(echo $0 | sed "s/\/$SCRIPTPATH//g")
fi
# change to absolute path
cd $ABSPATH

# then execute the java launcher line here:
java -jar [program].jar[/PHP]
And save the script in the same directory as [program].jar

---

