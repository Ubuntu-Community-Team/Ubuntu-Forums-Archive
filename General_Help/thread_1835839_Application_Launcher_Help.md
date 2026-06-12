---
title: "Application Launcher Help"
date: 2011-08-30
forum: General Help
---

### Post by Kocrachon on 2011-08-30
Hello,

   Right now I have a program installed where I have to type a fairly long string in order to launch it


```
cd /home/kocrachon/Downloads/d20 && java -Xmx384m -Xss512k -XX:MaxPermSize=128m -Dsun.java2d.ddoffscreen=false -Dsun.java2d.noddraw -Dsun.java2d.d3d=false -jar d20Pro.jar
```

So I go and try to create a custom application launcher, and when I try to launch it, I get this error..

```
Failed to execute child process "cd" (No such file or directory)
```

Anyone able to help me out?

---

### Post by raja.genupula on 2011-08-30
```
cd ~/Downloads/d20 && java -Xmx384m -Xss512k -XX:MaxPermSize=128m -Dsun.java2d.ddoffscreen=false -Dsun.java2d.noddraw -Dsun.java2d.d3d=false -jar d20Pro.jar

```

change it & are you sure about that folder place in downloads ?

---

### Post by mcduck on 2011-08-30
> **Kocrachon said:**
> Hello,

   Right now I have a program installed where I have to type a fairly long string in order to launch it


```
cd /home/kocrachon/Downloads/d20 && java -Xmx384m -Xss512k -XX:MaxPermSize=128m -Dsun.java2d.ddoffscreen=false -Dsun.java2d.noddraw -Dsun.java2d.d3d=false -jar d20Pro.jar
```

So I go and try to create a custom application launcher, and when I try to launch it, I get this error..

```
Failed to execute child process "cd" (No such file or directory)
```

Anyone able to help me out?
Launcher's don't like long commmands, and don't really even work quite the same way as executing commands in a terminal does. Which is why it's complaining about the "cd " command. It's expecting a path to file to execute, not a shell command.

You should instead create a simple shell script to execute your command, and then point the launcher to that script.

---

### Post by fdrake on 2011-08-30
agreening with the previous poster's suggestion you should:

```

mkdir /home/kocrachon/Downloads/d20/myscripts
cat > /home/kocrachon/Downloads/d20/myscripts/script.sh
#!/bin/bash
java -Xmx384m -Xss512k -XX:MaxPermSize=128m -Dsun.java2d.ddoffscreen=false -Dsun.java2d.noddraw -Dsun.java2d.d3d=false -jar d20Pro.jar
<enter>
<press cntl+D>
chmod +x /home/kocrachon/Downloads/d20/myscripts/script.sh
```

launchers command:
```

/home/kocrachon/Downloads/d20/myscripts/script.sh

```

ps . i am not sure about the java command since a don;t know the language.

---

### Post by Kocrachon on 2011-09-01
issue I am running into now is it is saying I dont have permission...

---

### Post by fdrake on 2011-09-01
> **Kocrachon said:**
> issue I am running into now is it is saying I dont have permission...

i don't understand why you shouldn't have the permissions since that's your folder. what exactly the java command does? does it edit a file outside your home directory or a protected file/folder? is your user allowed to run java commands?
can you post the exact error message from the terminal.

---

### Post by 3rdalbum on 2011-09-01
> **Kocrachon said:**
> issue I am running into now is it is saying I dont have permission...

You need to give the script permission to execute. Right-click on the script and go to Properties. Go to the Permissions tab and click on "Allow file to run as a program" or something like that.

---

