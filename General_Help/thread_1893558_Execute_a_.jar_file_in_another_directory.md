---
title: "Execute a *.jar file in another directory?"
date: 2011-12-10
forum: General Help
---

### Post by Jabra91 on 2011-12-10
Hi,

I have a .jar file which I want to execute on boot.

If I'm in the correct directory, the following comand works perfect:

```
java -jar file.jar
```

But it has to use files, which are in the same directory. So if I start it from another directory, like this:

```
java -jar folder/file.jar
```

The Programm creates it's own files in the current directory I'm in and ignores the files in "folder".

So what I need, is a command, which I can put into my /etc/rc.local. Is there an option for java to do this or is there another way?

btw im using openjdk-6.

Thanks for your help

---

### Post by N00b-un-2 on 2011-12-10
you could always symlink to it from one of the /bin folders.  I do this for the Android Debug Bridge (ADB) so that instead of having to cd into '$HOME/android-sdk-linux_x86/Platform Tools/' I can just type 'adb' in the terminal to talk to my phone.  The ADB is essentially a java executable.

---

### Post by Jabra91 on 2011-12-10
> **N00b-un-2 said:**
> you could always symlink to it from one of the /bin folders.  I do this for the Android Debug Bridge (ADB) so that instead of having to cd into '$HOME/android-sdk-linux_x86/Platform Tools/' I can just type 'adb' in the terminal to talk to my phone.  The ADB is essentially a java executable.

can you explain it a bit more? how does your symlink looks like?

or is it possible to do it with cd in /etc/rc.local? and if, how does the command look like?

will this work?

```
cd /folder && java -jar file.jar
```

---

### Post by N00b-un-2 on 2011-12-10
for the adb it's 
```
sudo ln -s /home/ryan/android-sdk-linux_x86/platform-tools/adb /usr/bin/adb
sudo chmod o+x /usr/bin/adb
```

this creates a command that invokes the adb.  what you may want to do is first create a bash script file that looks like this 
```

#! /bin/bash
java -jar /path/to/file.jar
```
and save it as */home/user/something.sh*
the mark the bash script as executable (the o+x bit in the terminal)
```
sudo chmod o+x /home/user/something.sh
```

Test that the script works by executing it in the terminal
```
./something.sh
```

You should actually be able to add the script itself to your session (gnome-session-properties), or you can choose a unique name for it and symlink to it in /usr/bin or /usr/local/bin.

---

### Post by Jabra91 on 2011-12-10
ok, this is good, but not solving my problem with the jar file. With your help, I can execute the jar file with a single command, but it still executes in the current directory, so it's creating its own files and not using the files in "folder". So I think it's more a problem with the java command.

So, what about using cd? can I use cd in rc.local to execute a file in a special folder?

---

### Post by Jabra91 on 2011-12-10
ok, I just tried it with cd in the shell script. So it now looks like this:

```
#! /bin/bash

cd /folder && java -jar /folder/file.jar
```

and I put the symlink into my /etc/rc.local

```
programm &
```

Now everything is working fine, thanks for your help :-)

---

