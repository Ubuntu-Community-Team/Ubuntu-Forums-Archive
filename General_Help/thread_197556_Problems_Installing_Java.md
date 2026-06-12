---
title: "Problems Installing Java"
date: 2006-06-15
forum: General Help
---

### Post by rsulli55 on 2006-06-15
Hey guys I having some problems installing the sun-java5 packages.  I tried to install sun-java5-bin, sun-java5-jre and sun-java5-plugin, but I get these errors.
Any help is appreciated.  Thanks

```
After unpacking 83.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 88497 files and directories currently installed.)
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-06-1_i386.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by CameronCalver on 2006-06-16
Well i did it from apt-get and it did not work either so this is how to  do it

1 enable multiverse and universe repos if you dont no how just ask me

2 search sun-j and dowload the sun-j2re 1.5 if that does not work  download the next one which is the bin 
Reply back plz if it works or if it doesnt

---

### Post by mravik on 2006-06-16
[QUOTE=CameronCalver]enable multiverse and universe repos if you dont no how just ask me
[/QUOTE]

Well, I have enabled multi- + universe, but I still dont get sun-java or sun-j when searching with synaptic. Any help appreciated!


SOLVED! --> Multiverse was not enabled yet!

---

### Post by CameronCalver on 2006-06-16
Everthing working then for you see that was easyer then the other way wasnt it lol

---

### Post by rsulli55 on 2006-06-17
Thanks for the replies.  I fixed it by following this howto [http://jdk-distros.dev.java.net/ubuntu.html]("http://jdk-distros.dev.java.net/ubuntu.html")

Now, I have another problem.  When I try to run Frostwire, I get these errors.
```
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```
If anyone knows how to fix these I would be very grateful.  Thanks in advance.

---

### Post by scxtt on 2006-06-17
looks like it can't find Java in any of the "normal" directories - you can see it trying ...

type:
[indent]$:> whereis java[/indent]into a terminal and see what you get ...

here's what i get, but i haven't installed java (on my own):```
:> whereis java
java: /usr/bin/java /etc/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz
```

---

### Post by rsulli55 on 2006-06-17
This is what I get 
```
whereis java
java: /usr/bin/java /etc/java /usr/lib/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz

```

---

### Post by scxtt on 2006-06-17
not sure what the prob is ...

---

### Post by dcstar on 2006-06-17
[QUOTE=rsulli55]Hey guys I having some problems installing the sun-java5 packages.  I tried to install sun-java5-bin, sun-java5-jre and sun-java5-plugin, but I get these errors.
Any help is appreciated.  Thanks

```
After unpacking 83.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 88497 files and directories currently installed.)
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
.......

```[/QUOTE]
[http://ubuntuforums.org/showpost.php?p=1127663&postcount=4](http://ubuntuforums.org/showpost.php?p=1127663&postcount=4)

---

### Post by rsulli55 on 2006-06-18
Thanks for the reply, now does anyone know how to fix the Frostwire problem?

---

### Post by beameup on 2006-06-18
Might be a dumb question but was there a problem installing it from Add/Remove? :confused:

---

### Post by rsulli55 on 2006-06-18
[QUOTE=beameup]Might be a dumb question but was there a problem installing it from Add/Remove? :confused:[/QUOTE]

No, it worked, because I am able to view web pages that need java.  I tried installing blackdown java, and frostwire ran, but I don't think I should need to have two java packages on my computer. (I went to the web sites before installing blackdown, and also again after removing it, so it was the Sun Java working.)

---

### Post by beameup on 2006-06-22
OK, That's about where I'm at. I have Sun Java, The GNU version, and v1.5.0_04 that Moneydance installs.

---

