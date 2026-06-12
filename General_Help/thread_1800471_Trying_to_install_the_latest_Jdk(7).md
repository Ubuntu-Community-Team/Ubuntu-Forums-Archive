---
title: "Trying to install the latest Jdk(7)"
date: 2011-07-09
forum: General Help
---

### Post by p3aul on 2011-07-09
This is for Ubuntu 11.04
I have downloaded Netbeans 7.0 and it says it will work with Java 7 so I downloaded that too. The only problem... I don't know how to install it! This is the name of the file: **[COLOR=Red]jdk-6u26-linux-i586.bin [/COLOR]**[COLOR=Red][COLOR=Black]As you see it is a bin file and doubleclicking just brings up a dialog saying it can't open it. Does anyone have a clue how I can install it?
Thanks,
Paul
[/COLOR][/COLOR]

---

### Post by raja.genupula on 2011-07-09
Hey man do like this ```
sudo chmod 777 filenname.bin
``````
./filename.bin
```


there if your file is at home folder , those works . if file is at another location just at file name write that location .

---

### Post by p3aul on 2011-07-09
Thanks, Will give it a try!
Paul

---

### Post by linuxman94 on 2011-07-09
The file you downloaded is for java 6.  You need to get the java 7 preview release from here: [http://jdk7.java.net/download.html]("http://jdk7.java.net/download.html")

Once you have it downloaded, extract it to your home folder. (You can just use archive manager)

Next fire up the terminal and type:

```
sudo mv jdk1.7.0 /usr/lib/jvm
```

This moves the jdk folder to the default installation folder for java.

Next type this command and count the number of java version you have.  

```
sudo update-alternatives --config java
```

Once you have that number enter this command and change the number on the end of it to the number you just found plus one.
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.7.0/jre/bin/java **3**
```

Finally, run this command and type the number of the new installation then hit enter.

```
sudo update-alternatives --config java
```

To make sure everything worked, run this command.  It should output your version to be 1.7.0.

```
java -version
```

And that's it!  Let us know if you have problems with anything.

---

### Post by p3aul on 2011-07-09
Thanks! I realized my error and did download the prerelease. However I decided not to install the prerelease. I think I will install it after the bugs have been worked out! I will save your instructions though.
Paul

---

### Post by sob7y on 2011-07-31
> **linuxman94 said:**
> The file you downloaded is for java 6.  You need to get the java 7 preview release from here: [http://jdk7.java.net/download.html]("http://jdk7.java.net/download.html")

Once you have it downloaded, extract it to your home folder. (You can just use archive manager)

Next fire up the terminal and type:

```
sudo mv jdk1.7.0 /usr/lib/jvm
```

This moves the jdk folder to the default installation folder for java.

Next type this command and count the number of java version you have.  

```
sudo update-alternatives --config java
```

Once you have that number enter this command and change the number on the end of it to the number you just found plus one.
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.7.0/jre/bin/java **3**
```

Finally, run this command and type the number of the new installation then hit enter.

```
sudo update-alternatives --config java
```

To make sure everything worked, run this command.  It should output your version to be 1.7.0.

```
java -version
```

And that's it!  Let us know if you have problems with anything.

How to make all binaries in the jdk1.7.0 directory available. This method appears to only replace (or add if it's the first install) the java binary not javac,jdb and so on.
Should I put the path of this directory in the PATH variable?

---

