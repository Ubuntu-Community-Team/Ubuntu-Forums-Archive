---
title: "Lots of errors when executing a .sh file"
date: 2010-05-30
forum: General Help
---

### Post by IRLegend on 2010-05-30
Hey everyone. I'm hosting a game server on my computer, but when I run the .sh files I get command not found errors.
Here are the errors:
```

blah@vps:~/Blah/Blah# bash launch_world.sh
': not a valid identifierexport: `CLASSPATH
Error occurred during initialization of VM
Could not reserve enough space for object heap
Could not create the Java Virtual Machine
launch_world.sh: line 5: -Dnet.sf.odinms.sendops=config\sendops.properties: command not found
launch_world.sh: line 6: -Dnet.sf.odinms.wzpath=wz: command not found
launch_world.sh: line 7: -Djavax.net.ssl.keyStore=filename.keystore: command not found
launch_world.sh: line 8: -Djavax.net.ssl.keyStorePassword=passwd: command not found
launch_world.sh: line 9: -Djavax.net.ssl.trustStore=filename.keystore: command not found
launch_world.sh: line 10 -Djavax.net.ssl.trustStorePassword=passwd: command not found
launch_world.sh: line 11 -Xmx150M: command not found
launch_world.sh: line 12 net.sf.odinms.net.world.WorldServer: command not found
```

I used the command bash launch_world.sh and got all these errors.
I'm new to Linux so I need help on this. How do I define these commands or something? And how do I fix the first few errors?

Thanks!

---

### Post by Onisutra on 2010-05-30
> **IRLegend said:**
> Hey everyone. I'm hosting a game server on my computer, but when I run the .sh files I get command not found errors.
Here are the errors:
```

blah@vps:~/Blah/Blah# bash launch_world.sh
': not a valid identifierexport: `CLASSPATH
Error occurred during initialization of VM
Could not reserve enough space for object heap
Could not create the Java Virtual Machine
launch_world.sh: line 5: -Dnet.sf.odinms.sendops=config\sendops.properties: command not found
launch_world.sh: line 6: -Dnet.sf.odinms.wzpath=wz: command not found
launch_world.sh: line 7: -Djavax.net.ssl.keyStore=filename.keystore: command not found
launch_world.sh: line 8: -Djavax.net.ssl.keyStorePassword=passwd: command not found
launch_world.sh: line 9: -Djavax.net.ssl.trustStore=filename.keystore: command not found
launch_world.sh: line 10 -Djavax.net.ssl.trustStorePassword=passwd: command not found
launch_world.sh: line 11 -Xmx150M: command not found
launch_world.sh: line 12 net.sf.odinms.net.world.WorldServer: command not found
```

I used the command bash launch_world.sh and got all these errors.
I'm new to Linux so I need help on this. How do I define these commands or something? And how do I fix the first few errors?

Thanks!

It could be a few problems. It could be an issue with the script itself. It might also be that you don't have the correct tools needed to run it. You might need to run the program as root. I might also be that you need to chmod the file to be executable..who knows. 

Try "sudo sh launch_world.sh"

---

### Post by IRLegend on 2010-05-30
Here's the file:
```

#!/bin/sh
CLASSPATH=".:dist/blah.jar:dist/mina-core.jar:dist/slf4j-api.jar:dist/slf4j-jdk14.jar:dist/mysql-connector-java-bin.jar"
export CLASSPATH
java -Darberms.recvops=config\recvops.properties \
-Dnet.sf.odinms.sendops=config\sendops.properties \
-Dnet.sf.odinms.wzpath=wz \
-Djavax.net.ssl.keyStore=filename.keystore \
-Djavax.net.ssl.keyStorePassword=passwd \
-Djavax.net.ssl.trustStore=filename.keystore \
-Djavax.net.ssl.trustStorePassword=passwd \
-Xmx150M \
net.sf.odinms.net.world.WorldServer
```

And when I try "sudo sh launch_world.sh" it says:
"bad variable NameH".

I followed a guide to installing this and I did everything as told.

---

### Post by geirha on 2010-05-30
Those two backslashes in config\recvops.properties and config\sendops.properties gets removed by the shell before it's executed. It should probably have been /-es.

---

### Post by IRLegend on 2010-05-30
Again, I'm pretty new to this stuff. Could you show me how it should be?

---

### Post by sedawk on 2010-05-30
And also check if all the backslashes are really the last character
in the line - your errors looks like there is a space or a dos-like
line break.
Normally every line is a command and only a backslash at the end of
the line tells the shell to read a multi line command. If there
is a (funny non-printable) character behind the backslash you are
in trouble.

When using vi you can see invisible characters like tabs with
":set list" and turn it of with ":nolist" again.
(When entering the colon cursor should jump to the last line of
 the screen, If the colon is inserted in the normal text you
 are in editing mode, not in command mode. Press ESC to toggle
 from edit mode back to command mode. Use i for insert to 
 switch from command mode to edit mode).

---

### Post by IRLegend on 2010-05-30
Okay thanks for the help!
I managed to fix the command not found errors.
Now I have these left:
```

Error occurred during initialization of VM
Could not reserve enough space for object heap
Could not create the Java Virtual Machine
```
Any idea on how to fix them?

---

### Post by IRLegend on 2010-05-31
Could anyone help me fix these errors?

```

Error occurred during initialization of VM
Could not reserve enough space for object heap
Could not create the Java Virtual Machine
```

---

### Post by ks07 on 2010-05-31
Just done some searches on those error messages, Java seems to be complaining about not enough RAM. How much memory does your PC have? It might not meet the minimum requirements to run the server (don't know what game you're trying to host, so can't advise there).

Also, try modifying the script to if you can to try adding some of the flags mentioned in this thread about the same error message. For example, if your script contained ```
java ./game-server
``` you might try changing it to something like ```
java -Xms64m -Xmx512m ./game-server
```

Don't know how much help that'll be, but at least it's a start. :)

---

### Post by IRLegend on 2010-05-31
Hmm, I tried adding it to the script, but it didn't work either.
It's a VPS, and 1GB Ram.

---

### Post by ks07 on 2010-05-31
Sorry, completely forgot to link to the page I was referring to. [Find it here]("http://forums.sun.com/thread.jspa?threadID=632411"). I don't really have any more ideas, other than maybe tweaking the numbers and/or changing the flags to start with -J-X.... For example: ```
java -J-Xms64m -J-Xmx512m ./game-server
```

After that, I'm all out of ideas. Maybe you could contact the script's developer to ask for some help?

---

### Post by IRLegend on 2010-05-31
This basically fixed the first 2 errors. Now there's a new error -

```

Unrecognized option: -J-Xms64m
Could not create the java virtual machine

```
Can you fix those?

---

### Post by ks07 on 2010-05-31
> **IRLegend said:**
> This basically fixed the first 2 errors. Now there's a new error -

```

Unrecognized option: -J-Xms64m
Could not create the java virtual machine

```Can you fix those?
The first error seems easy enough - just remove that option from the script. As for the second error, was that the only information given? Can't really help you much with that without anything else to look for. Perhaps there is a log file in the directory with more details?

---

### Post by IRLegend on 2010-05-31
After removing it, I'm back to where I started :(

---

### Post by ks07 on 2010-05-31
> **IRLegend said:**
> After removing it, I'm back to where I started :(
Ah, I should have been more clear. I only meant for you to remove the one that gave the error, specifically "-J-Xms64m". Otherwise putting both back to how they were shouldn't harm the script (see the examples below). If Java doesn't recognize the option, it should just ignore it (apart from the warning message).

So, you want to try this first:
```
java -J-Xmx512m ./game-server
```If it gets rid of error message #1, good. If it takes you back to those three original messages, revert the line to something like
```
java -J-Xms64m -J-Xmx512m ./game-server
```

Now, I'm stuck with the 2nd message "Could not create the Java virtual machine". Any number of things could cause that, so without any more detailed error messages or an error log, there's not much I can do. Anybody with some more experience care to lend a hand?

---

### Post by IRLegend on 2010-05-31
It didn't work either.

Thanks for your help anyways. :(

---

### Post by blissfulpenguin on 2010-10-13
hey,

this may not be the right answer, but i don't see it quoted anywhere, hope it helps:

got the same output, trying to compile some Droid, and i figured it had something to do with the version of java being used.  first tried to manually install jre-1.5 from the oracle website.  bad idea!  too difficult manually installing each symlink into update-alternatives, which would have been my next step. but, on a whim, i decided to make sure and switch all java-things to sun-java-6, with a ```
update-alternatives --all <CR>
```

Tedious, but not so much as manually installing the sun5 I'd extracted that wasn't showing up.  So far, no fatal errors!  Will report if this is wrong...in about 2 hours.  And, yep, I used the -j2 switch, lol.

Best of luck.

---

