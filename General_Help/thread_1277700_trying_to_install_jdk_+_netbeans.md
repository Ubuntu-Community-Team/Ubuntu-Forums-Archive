---
title: "trying to install jdk + netbeans"
date: 2009-09-28
forum: General Help
---

### Post by maraudertank on 2009-09-28
hello, i'm trying to install the jdk + netbeans package which i downloaded from sun's site.

jdk-6u16-nb-6_7_1-linux-ml.sh

i changed the permissions so that the file could be executable, then opened up terminal, here's what i got:

```
@ubuntu:~/Desktop$ sudo ./jdk-6u16-nb-6_7_1-linux-ml.sh
Configuring the installer...
Searching for JVM on the system...
Preparing bundled JVM ...
eval: 1: /tmp/.nbi-1092802.tmp/jre-6u14-linux-i586.bin: not found
Cannot extract bundled JVM
```

i have no idea what that means :(

so thinking it needed java installed i did that through the add/remove programs but it made no difference.

---

### Post by Diabolis on 2009-09-28
[http://wiki.netbeans.org/NBIExitCodeValues](http://wiki.netbeans.org/NBIExitCodeValues)

You may have run out of space in your drive.

---

### Post by shaon3343 on 2009-09-28
[COLOR=SeaGreen][B]hi there,
   its showing because jre is not installed in your ubuntu . so you need to install jre. after that you can install this netbeans. so you have to open terminal and apply those command:[/B][/COLOR]
                                             [COLOR=Magenta]**for installing  jre: **   [COLOR=Red]***sudo apt-get install sun-java6-jre***[/COLOR]
                                                ** for installing jdk **:  [COLOR=Red]***sudo apt-get install sun-java6-jdk***[/COLOR][/COLOR]
                                                                                                                                                                       shaon

---

### Post by maraudertank on 2009-09-29
thank you both for the reply. 

im using the terminal commands shaon listed and its downloading the jdk now. got a couple more questions though

how do you guys know what these packages are called so you can use apt-get to download them? how come the files i downloaded off of sun's websites wont install with the ./ command? i downloaded both the jre and the jdk bundled with netbeans. its not a free space issue as diabolis suggested it may be, i certainly have enough of that.

---

### Post by shaon3343 on 2009-09-29
[COLOR=Red]**ya, we got those commands from searching net and from this forum or from some of my frineds. you should use the "sudo apt-get install  ..." command for it is more convenient then the " ./configure " . take care. **[/COLOR]

---

### Post by credobyte on 2009-09-29
The problem might be that you didn't had Java JRE installed, tough, not 100% sure about this.
Oh, and .. from what I see, no one mentioned sun-java6-plugin. You'll not be able to use Java through Firefox unless you'll have it :)

---

### Post by Mighty_Joe on 2009-09-29
> **maraudertank said:**
> 
how do you guys know what these packages are called so you can use apt-get to download them? 

```
apt-cache search java
```

---

