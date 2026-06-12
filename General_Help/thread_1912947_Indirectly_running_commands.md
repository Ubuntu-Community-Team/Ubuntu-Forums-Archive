---
title: "Indirectly running commands"
date: 2012-01-21
forum: General Help
---

### Post by dms489 on 2012-01-21
I have two problems I believe to be related:
1. if I execute a cd command from a terminal like "cd ../executable_files" it works fine, but if I write that in a shell script, the cd fails.  For example, the file "run.sh" contains this:
    cd ../executable_files
    java fobots.ui.NetSim free.log freespace
    cd ../batch_files
When I put "sh run.sh" in a terminal, I get this error:
can't cd to ../executable_files

2. if I have a C executable file called Fred, I can run it from a terminal by typing "./Fred"  However, I want to run this from a Java program using the following code:
   Process aProcess=Runtime.getRuntime().exec("./Fred");
Although the file Fred is in the appropriate directory for the Java program to find it, I get a java exception that essentially says it can't find or open the file Fred.

Any insight into either problem would be appreciated.

---

### Post by trikster_x on 2012-01-21
> **dms489 said:**
> I have two problems I believe to be related:
1. if I execute a cd command from a terminal like "cd ../executable_files" it works fine, but if I write that in a shell script, the cd fails.  For example, the file "run.sh" contains this:
    cd ../executable_files
    java fobots.ui.NetSim free.log freespace
    cd ../batch_files
When I put "sh run.sh" in a terminal, I get this error:
can't cd to ../executable_files

Try using the entire path in your cd command. Sometimes scripts don't like it when you use shortcuts.


> 2. if I have a C executable file called Fred, I can run it from a terminal by typing "./Fred"  However, I want to run this from a Java program using the following code:
   Process aProcess=Runtime.getRuntime().exec("./Fred");
Although the file Fred is in the appropriate directory for the Java program to find it, I get a java exception that essentially says it can't find or open the file Fred.

Any insight into either problem would be appreciated.

Without more info on your paths, the best I can offer here is that Fred is not actually in the right directory. If you do not have Fred with the rest of the java application, then you have to specify the exact path. If it is in the .jar you have made for your java application, then you should just be able to .exec(Fred). Most programming languages have a problem with file path shortcuts.

---

### Post by dms489 on 2012-01-22
> **trikster_x said:**
> Try using the entire path in your cd command. Sometimes scripts don't like it when you use shortcuts.



Without more info on your paths, the best I can offer here is that Fred is not actually in the right directory. If you do not have Fred with the rest of the java application, then you have to specify the exact path. If it is in the .jar you have made for your java application, then you should just be able to .exec(Fred). Most programming languages have a problem with file path shortcuts.

I have tried every combination of path definitions without success.  BTW, all this is happening under my /home/... directory

Fred is in the right place, but I hadn't thought of including it as a resource in the jar file.  I'll try that.  Thanks.

---

### Post by sudodus on 2012-01-22
> **dms489 said:**
> I have tried every combination of path definitions without success.  BTW, all this is happening under my /home/... directory

Fred is in the right place, but I hadn't thought of including it as a resource in the jar file.  I'll try that.  Thanks.

I have used cd commands in shellscripts many times, and I agree with *trikster_x* that you should use the full path in your cd command.

Another issue might be permissions or environment. How do you run the script? If you launch it manually yourself, you should have your own permissions and environment variables, but if you launch it automatically for example via cron, the situation will be different.

Another tip is to specify in the first line of the script, which shell interpreter to use (because some commands differ). I usually start my script with the following line (for bash)
```
#! /bin/bash
```

---

### Post by dms489 on 2012-01-23
> **sudodus said:**
> I have used cd commands in shellscripts many times, and I agree with *trikster_x* that you should use the full path in your cd command.

Another issue might be permissions or environment. How do you run the script? If you launch it manually yourself, you should have your own permissions and environment variables, but if you launch it automatically for example via cron, the situation will be different.

Another tip is to specify in the first line of the script, which shell interpreter to use (because some commands differ). I usually start my script with the following line (for bash)
```
#! /bin/bash
```
I don't want to be annoyingly persistent, but I would like to report one success and one continued frustration.
I solved the java thread execution problem by providing the full path to the executable file.  No surprise, just a significant loss in generality.
The cd .. problem in scripts continues to annoy.  The only band-aid that works is to move all the scripts to the executable directory and take out all cd's.  In general, this is really nasty, and I can't understand why this is a problem for Ubuntu.  Any unix system I have ever used lets me cd ../wherever in a shell script.  This thing doesn't work in the most benign environment:  my home directory; the directories 'wherever' and 'somewhereelse' are there. Permissions at 777, in the terminal, I can cd wherever, and c ../somewhereelse but in a script located in wherever containing cd ../somewhereelse fails.

---

### Post by sudodus on 2012-01-23
> **dms489 said:**
> I don't want to be annoyingly persistent, but I would like to report one success and one continued frustration.
I solved the java thread execution problem by providing the full path to the executable file.  No surprise, just a significant loss in generality.
The cd .. problem in scripts continues to annoy.  The only band-aid that works is to move all the scripts to the executable directory and take out all cd's.  In general, this is really nasty, and I can't understand why this is a problem for Ubuntu.  Any unix system I have ever used lets me cd ../wherever in a shell script.  This thing doesn't work in the most benign environment:  my home directory; the directories 'wherever' and 'somewhereelse' are there. Permissions at 777, in the terminal, I can cd wherever, and c ../somewhereelse but in a script located in wherever containing cd ../somewhereelse fails.
I understand your frustration. I have made scripts with such relative changes of directory in dos, unix and linux. And they work, at least when I start them manually from a terminal window (or a fullscreen terminal. How to you start your script? Or is there something else in the beginning of the script, that destroys things? If you don't want to publish your script you can send it in a message to me, so that I can try it in my computer.

---

### Post by dms489 on 2012-01-24
> **sudodus said:**
> I understand your frustration. I have made scripts with such relative changes of directory in dos, unix and linux. And they work, at least when I start them manually from a terminal window (or a fullscreen terminal. How to you start your script? Or is there something else in the beginning of the script, that destroys things? If you don't want to publish your script you can send it in a message to me, so that I can try it in my computer.
I'm fine with publishing the scripts - it's really simple.
after a cold boot of Ubuntu 10.11, I open a Terminal defaulting to my home directory.
I manually cd A ### a directory that exists. Directory B also exists
In A is a file fred.sh containing:
    cd ../B
    ###  some simple file copy command
    cd ../A
In the terminal now looking in A, I type:
>> sh fred.sh
The first cd fails with "can't cd ../B" or something like that
The file copy succeeds except the files are going into A instead of B
The second cd fails in the same way.

---

### Post by sudodus on 2012-01-24
> **dms489 said:**
> I'm fine with publishing the scripts - it's really simple.
after a cold boot of Ubuntu 10.11, I open a Terminal defaulting to my home directory.
I manually cd A ### a directory that exists. Directory B also exists
In A is a file fred.sh containing:
    cd ../B
    ###  some simple file copy command
    cd ../A
In the terminal now looking in A, I type:
>> sh fred.sh
The first cd fails with "can't cd ../B" or something like that
The file copy succeeds except the files are going into A instead of B
The second cd fails in the same way.

Have a look at the following script and the output of it!

```
me@cmp:~/test/A$ [COLOR=RoyalBlue]cat fred.sh[/COLOR]
#! /bin/sh

echo "start $0"
echo "$PWD"
cd ../B
echo "$PWD"
### some simple file copy command
cd ../A
echo "$PWD"
echo "normal termination"
me@cmp:~/test/A$ [COLOR=RoyalBlue]ls -l[/COLOR]
total 4
-rw-r--r-- 1 me me 141 2012-01-24 16:16 fred.sh
me@cmp:~/test/A$ [COLOR=RoyalBlue]chmod ugo+x fred.sh
[/COLOR]me@cmp:~/test/A$ [COLOR=RoyalBlue]ls -l[/COLOR]
total 4
-rwxr-xr-x 1 me me 141 2012-01-24 16:16 fred.sh
me@cmp:~/test/A$ [COLOR=RoyalBlue]./fred.sh[/COLOR]
start ./fred.sh
/home/me/test/A
/home/me/test/B
/home/me/test/A
normal termination
/home/me:~/test/A$ 

```
As you can see this script works. Try it yourself :-)

Please publish your complete script! There might be something in the commands not included that makes it fail.

---

### Post by carranty on 2012-01-24
Try running your script with a period.  For example if the script is *script.sh*, in a terminal write

```
. script.sh
```

---

### Post by efflandt on 2012-01-24
Your current working directory usually starts with the directory "you" are currently in (not necessarily where the script is), or that may be undetermined if you try to run it automatically from somewhere.  It would be best to have your script first cd to the full path of a specific directory before having it try to use relative paths.

Note that for personal scripts or binaries, create a **bin** directory in your home dir (~/bin), log out, log back in, and that bin should automatically be in your $PATH.  Then assuming each script there has execute permission for you, and proper shebang line (1st line for whatever should interpret it), you do not need to include a path when "you" run the script by just its name.

But if you automatically run things from cron or startup scripts, assume you don't know where you are with no environment, and specify full paths for everything.

---

