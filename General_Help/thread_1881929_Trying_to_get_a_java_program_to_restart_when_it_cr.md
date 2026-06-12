---
title: "Trying to get a java program to restart when it crashes"
date: 2011-11-16
forum: General Help
---

### Post by kenji_03 on 2011-11-16
Thanks in advance for your reply.

I'm relatively new to Linux and am trying to run a Minecraft server.  I got the server running just fine but the recent pre-release is a bit unstable.  As such, it crashes often.

I [read that]("http://ubuntuforums.org/showthread.php?t=1448952") there are ways to get Ubuntu to run something called a "BashScript" (I'm guessing it's like a .bin on ***dows) to automatically check if a program is running, and to start that program if it is not running.  The problem is that I can't make heads or tails of the code...

Can anyone help me code this out?

---

### Post by kenji_03 on 2011-11-19
Figured it out :guitar:

It's more complicated than just typing some text in terminal unfortunately, so follow the instructions:

> [LIST=1]
[*]Create a document with the following code (anywhere on your machien)
```
#!/bin/bash

while true
do
if [ ! `pgrep java` ] ; then
/usr/bin/minecraft.sh
fi
sleep 30
done
```
[*]Create another document in your Minecraft Server folder and title it "Start server.sh" with the following code
```
**[COLOR="Red"]cd /home/Kenji_03/games/MinecraftServer[/COLOR]**
java -Xms1G -Xmx1G -jar minecraft_server.jar
```
[*]**<Important>** you must change the "change directory" (**[COLOR="Red"]cd[/COLOR]**) portion to direct terminal to your minecraft server folder
[*]_Make a link_ to your "Start server.sh"
[*]Copy it
[*]Go to your /usr/bin as a root user (you can use Terminal's "sudo nautilus" browser to do this with a GUI).
[*]Paste the link and rename it "minecraft.sh" (case sensitive)
[/LIST]

Fair warning, this code depends on the server being the only java app running on your computer.  So you won't be able to use any other java app while this is running -- sorry!

---

### Post by dave0109 on 2011-11-19
How about setting up a symlink to the java binary and invoking that to run the classes?

```

$ cd /home/Kenji_03/games/MinecraftServer
$ ln -s /usr/bin/java minecraft
$ cat > start_server.sh << _EOF
#!/bin/bash
cd /home/Kenji_03/games/MinecraftServer
minecraft -Xms1G -Xmx1G -jar minecraft_server.jar
_EOF

```

Then you can do `pgrep minecraft` and run other java processes using the java binary as normal.

---

### Post by kenji_03 on 2011-11-19
> **dave0109 said:**
> How about setting up a symlink to the java binary and invoking that to run the classes?

```

$ cd /home/Kenji_03/games/MinecraftServer
$ ln -s /usr/bin/java minecraft
$ cat > start_server.sh << _EOF
#!/bin/bash
cd /home/Kenji_03/games/MinecraftServer
minecraft -Xms1G -Xmx1G -jar minecraft_server.jar
_EOF

```

Then you can do `pgrep minecraft` and run other java processes using the java binary as normal.

That looks like a perfect plan, but can you explain a little bit about what you did?  I'd like to understand the code I'm putting into my machine.

---

### Post by dave0109 on 2011-11-20
Sure thing, good idea...

```

$ cd /home/Kenji_03/games/MinecraftServer
$ ln -s /usr/bin/java minecraft

```
This creates a symbolic link called "minecraft", a link is a reference to another file, directory, socket, etc without being an actual copy.  They take up a small number of bytes compared to copying the whole file.  Windows copied the idea with their 'shortcut' option, but links are even better. :)  You can then reference the original thing via the link.  If the link were pointing to a directory, you could cd to it.  If a text file, you could open it.  In this case it's a link to a program which allows you then to run the program by another name.

```

$ cat > start_server.sh << _EOF
#!/bin/bash
cd /home/Kenji_03/games/MinecraftServer
minecraft -Xms1G -Xmx1G -jar minecraft_server.jar
_EOF

```
This says con**cat**onate output redirecting the output into a file called "start_server.sh" until it reads the input of "_EOF".  This is a way of saying 'put this text into a file'.  So the following 3 lines are put into the file, and the _EOF stops the cat program adding anything more.

Obviously the contents of the file are taken from what you originally posted, expect now, we can call the java binary via the minecraft symlink.

Hope this helps.

---

