---
title: "Terminal Problems"
date: 2009-09-06
forum: General Help
---

### Post by Hosmion on 2009-09-06
Hello everyone, I'm Hosmion and I have a question about the Terminal..

I downloaded something..  Used the apt-get install (name) command.. Then, when trying to open it up, by saying :

```
./(name of program)
```It will not open, it says :

```
bash: ./rsbot: No such file or directory
```

Thanks you guys!

UBUNTU ROCKS!!!

---

### Post by falconindy on 2009-09-06
You only need ./ to execute a program in the directory that you're in. A program installed via synaptic or apt-get should be available via your $PATH. Just use `rsbot` to execute it.

---

### Post by carlosgs91 on 2009-09-06
.

---

### Post by Hosmion on 2009-09-06
I am in my default directory :
```

tommy@ubuntu:~$
```Can I still open it if I do :

```
tommy@ubuntu:~$ ./rsbot 
```?

Thanks :D

And also, this is where I downloaded it, so you guys tell me if I did it correctly :...

[http://www.sythe.org/showthread.php?t=574222](http://www.sythe.org/showthread.php?t=574222)

I'm not advertising..  I am just curious..

Thanks you guys :D

---

### Post by carlosgs91 on 2009-09-06
.

---

### Post by falconindy on 2009-09-06
edit: Looked up what rsbot is. Not interested in helping someone cheat at a game. Shame on you.

---

### Post by orlox on 2009-09-06
Just as they mentioned above, you use ./ to refer to an executable contained in your current folder. If you open up a terminal, you start located at your home folder, ./rsboot will only work if rsbot is located at your home folder.

Now, to begin with...I cant open the instructions you sent, but I guess it involved adding certain repository because rsboot is not in the standard repositories. Are you sure the program was even installed???

Try typing this on your terminal, and post the output:

```

sudo apt-get install rsbot

```

If needed in this command, replace rsboot with whatever thing you used when you used apt-get. This will tell if the application is actually installed.

---

### Post by defacto on 2009-09-06
```
./<application>

```

When you use it in this way, you are referring to something that should be in your current directory. Since rsbot can not be found in your home directory, you get an error.
You can launch applications by simply entering their name ( without ./ ).

---

### Post by orlox on 2009-09-06
Are the instructions you followed similar to these:

[http://runeattack.com/forum/showthread.php?tid=15](http://runeattack.com/forum/showthread.php?tid=15)

If so, then perhaps you screwed something on the way. That thing DOES NOT use apt-get to install rsbot, there, apt-get is used to install some dependencies needed, not the program itself!

Now, if you followed those instruction, then the executable is located at the trunk folder in your home folder...so, in theory, if you did all that stuff right, you could run this thing by opening up a new terminal, and running the following two commands:

```

cd trunk
./rsbot

```

---

### Post by Hosmion on 2009-09-06
In response to all of your posts :

I had downloaded the entire way I was supposed to download it ([HERE]("http://www.sythe.org/showthread.php?t=574222") is the link on how-to.  I downloaded it exactly the way I was supposed to)

This is what I did :

tommy@ubuntu:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
sThe following packages were automatically installed and are no longer required:
  avidemux toolame phonon linux-headers-2.6.28-11-generic
  linux-headers-2.6.28-11 avidemux-common conkeror-spawn-process-helper
  galeon-common
Use 'apt-get autoremove' to remove them.
u0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tommy@ubuntu:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
  avidemux toolame phonon linux-headers-2.6.28-11-generic
  linux-headers-2.6.28-11 avidemux-common conkeror-spawn-process-helper
  galeon-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tommy@ubuntu:~$ svn co [http://rsbotsvn.googlecode.com/svn/trunk](http://rsbotsvn.googlecode.com/svn/trunk)
**(components)**
Checked out revision 1075.
tommy@ubuntu:~$ /home/tommy/trunk
bash: /home/tommy/trunk: is a directory
tommy@ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
tommy@ubuntu:~$ /home/tommy/trunk
bash: /home/tommy/trunk: is a directory
tommy@ubuntu:~$ cd /home/tommy/trunk
tommy@ubuntu:~/trunk$ make
if [ ! -d "bin" ]; then mkdir "bin"; fi
"javac"  -d "bin" `find "src" -name "*.java"`
if [ -e scripts/*.class ]; then rm -R scripts/*.class; fi
"javac"  -cp "bin" scripts/*.java
if [ -e "RSBot-`cat "resources/version.txt"`.jar" ]; then rm "RSBot-`cat "resources/version.txt"`.jar"; fi
if [ -e "temp.txt" ]; then rm "temp.txt"; fi
cp "resources/Manifest.txt" "temp.txt"
echo "Specification-Version: \"`cat "resources/version.txt"`\"" >> "temp.txt"
echo "Implementation-Version: \"`cat "resources/version.txt"`\"" >> "temp.txt"
if [ -d "lib/rs.jar!" ]; then rm -R "lib/rs.jar!"; fi
mkdir "lib/rs.jar!"
`cd "lib/rs.jar!"; jar xf "/home/tommy/trunk/lib/rs.jar"`
jar cfm "RSBot-`cat "resources/version.txt"`.jar" "temp.txt" -C "bin" . scripts/*.class "lib/rs.jar!" "resources/version.txt" resources/images/*.png resources/*.bat resources/*.sh
rm "temp.txt"
rm -R "lib/rs.jar!"
tommy@ubuntu:~/trunk$ ./rsbot
**bash: ./rsbot: No such file or directory**
tommy@ubuntu:~/trunk$ rsbot
[B]bash: rsbot: Not a command

[/B]And when I downloaded the whole thing..  I  did not get anything..  I think the game I play patched it over or something or the recent update really screwed it up..

Someone can close this..

Thanks so much you guys.

---

### Post by defacto on 2009-09-06
What's the output of the following command ?
```
cd $HOME/trunk && ls -al

```

---

### Post by Hosmion on 2009-09-06
drwxr-xr-x  8 tommy tommy    4096 2009-09-06 15:44 .
drwxr-xr-x 62 tommy tommy    4096 2009-09-06 15:43 ..
drwxr-xr-x  3 tommy tommy    4096 2009-09-06 15:44 bin
-rw-r--r--  1 tommy tommy     339 2009-09-06 15:44 .classpath
-rw-r--r--  1 tommy tommy    1511 2009-09-06 15:44 Compile.bat
-rw-r--r--  1 tommy tommy      65 2009-09-06 15:44 .gitignore
drwxr-xr-x  3 tommy tommy    4096 2009-09-06 15:44 lib
-rw-r--r--  1 tommy tommy   35821 2009-09-06 15:44 license.txt
-rw-r--r--  1 tommy tommy    1170 2009-09-06 15:44 Makefile
-rw-r--r--  1 tommy tommy     381 2009-09-06 15:44 .project
drwxr-xr-x  4 tommy tommy    4096 2009-09-06 15:44 resources
-rw-r--r--  1 tommy tommy 1786246 2009-09-06 15:44 RSBot-554.12.jar
drwxr-xr-x  3 tommy tommy   20480 2009-09-06 15:44 scripts
drwxr-xr-x  4 tommy tommy    4096 2009-09-06 15:43 src
drwxr-xr-x  6 tommy tommy    4096 2009-09-06 15:44 .svn

---

### Post by defacto on 2009-09-06
Try:
```
cd $HOME/trunk && java -jar ./RSBot-554.12.jar
```

---

### Post by Hosmion on 2009-09-06
Unable to access jarfile .RSBot-554.12.jar

That is the response.

---

### Post by orlox on 2009-09-06
This problem is not a server related problem. I tried to compile rsbot on my computer and it doesnt generate the executable. However, an older version can be compiled, and to get that sources, you have to replace the svn command with this:

```
svn co http://rsbotsvn.googlecode.com/svn/trunk/ -r 800
```

However, the executtable produced by this throws an error, saying that its too old...So it doesnt work. In the end, this seems just to be a problem with the rsbot program, not with runescape servers...

---

### Post by Hosmion on 2009-09-06
Ok...

Thanks so much for helping..

Runescape launched a major update, patching graphics and different things.  So I guess the bot is not able to be used, so they just automatically removed the actual client while they update it.

Thanks for the help you guys :D

---

### Post by orlox on 2009-09-06
Just to close this thing up...

It seems that the most recent versions of rsbot, that are needed cause you cant run old ones, are compiled using a bat script, "Compile.bat". This is a windows script, and thus, it seems it turns the program OS dependant and incompatible with linux, unless you can find a correct way to compile it by your own.

I wouldnt say that rsbot no longer works, but I think that its no longer easy to compile on linux.

---

