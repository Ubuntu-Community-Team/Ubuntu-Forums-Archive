---
title: "Execute in Terminal"
date: 2011-12-17
forum: General Help
---

### Post by Dr. Claw on 2011-12-17
I am trying to execute a script by double clicking it, it is set to executable, but when I can choose to execute or execute in a terminal, execute just runs it with no way of interacting with it, and execute in terminal does nothing.
I need a terminal window to be able to interact with the program the script runs, but don't want to have to open a terminal window every time I have to run the script.

---

### Post by scorchgeek on 2011-12-17
Can you run it from the terminal with ./scriptname?

Is the first line of the script
```
#!/bin/bash
```

(or, if it's a Python, Perl, Ruby, etc script, the appropriate interpreter)?

If all that is right, can you post the output of 
```
ls -l
```

in the directory of the script?

---

### Post by Dr. Claw on 2011-12-17
The script runs fine when I use ./scriptname in the terminal, I can interact with the program then.

Output of ls -l:
```
$ ls -l
total 192128
-rw-rw-r-- 1 user user         0 2011-12-18 14:41 banned-ips.txt
-rw-rw-r-- 1 user user         0 2011-12-18 14:41 banned-players.txt
-rw-rw-r-- 1 user user       935 2011-12-18 14:41 bukkit.yml
-rwxrwxrwx 1 user user   9818144 2011-12-18 13:43 craftbukkit-1.0.1-R1.jar
-rwxrwxrwx 1 user user    747345 2011-11-29 12:13 minecraft_server.jar
-rwxrwxr-x 1 user user       124 2011-04-20 10:51 Minecraft Server makego.sh~
-rwxrwxr-x 1 user user       119 2011-12-18 14:29 MinecraftServermakego.sh
-rw-rw-r-- 1 user user         8 2011-12-18 14:41 ops.txt
-rw-rw-r-- 1 user user         0 2011-09-14 21:09 ops.txt~
-rw-rw-r-- 1 user user         0 2011-12-18 13:57 permissions.yml
drwxrwxr-x 4 user user      4096 2011-12-18 13:55 plugins
-rw-rw-r-- 1 user user    916291 2011-12-18 14:42 server.log
-rw-rw-r-- 1 user user       413 2011-11-19 16:56 server.properties
-rw-rw-r-- 1 user user       356 2011-09-14 21:20 server.properties~
drwxrwxr-x 6 user user      4096 2011-12-18 14:42 Valhallas
drwxrwxr-x 5 user user      4096 2011-12-18 14:42 Valhallas_nether
-rwxrwxr-x 1 user user  73168718 2011-12-03 17:06 Valhallas.rar
-rw-rw-r-- 1 user user 112035840 2011-12-03 16:20 Valhallas.tar
drwxrwxr-x 5 user user      4096 2011-12-18 14:42 Valhallas_the_end
-rw-rw-r-- 1 user user         0 2011-12-18 14:41 white-list.txt

```

Script is:
```
#! /bin/bash
BINDIR="$(dirname "$(readlink -fn "$0")")"
cd "$BINDIR"
java -Xincgc -Xmx1G -jar craftbukkit-1.0.1-R1.jar

```

Changed to /bin/bash as it was /bin/sh but still doesn't work.

---

