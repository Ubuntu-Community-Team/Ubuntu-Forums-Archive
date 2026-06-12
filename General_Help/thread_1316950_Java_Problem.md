---
title: "Java Problem"
date: 2009-11-06
forum: General Help
---

### Post by Hosmion on 2009-11-06
When I use the command "make", I get an error as follows :

```
make
if [ ! -d "bin" ]; then mkdir "bin"; fi
"javac"  -d "bin" `find "src" -name "*.java"`
/bin/sh: javac: not found
make: *** [Bot] Error 127
```

How do I fix this?

---

### Post by Hosmion on 2009-11-06
Sorry to bump so soon but I need an answer really soon.

---

### Post by cariboo on 2009-11-06
What is that you are trying to do? If your are trying to compile a java app, this may be better off in the Programming Talk sub-forum.

---

### Post by Hosmion on 2009-11-06
I am using the command make in Terminal to access a file.  But it comes up with that error, what do I do?

---

### Post by cariboo on 2009-11-06
The only time you need the **make** command is if you are trying to compile a program.

---

### Post by Hosmion on 2009-11-06
Ok, then I need to compile a program :D..  So..  How do I fix it?

---

### Post by sugarat on 2009-11-06
The shell is saying that the java compiler 'javac' is not found. You need to add it to your $PATH

---

### Post by cariboo on 2009-11-06
It would make things a lot easier if you told us what program you are trying to run.

---

### Post by albandy on 2009-11-06
sudo apt-get install sun-java6-jdk

---

### Post by Hosmion on 2009-11-06
> **albandy said:**
> sudo apt-get install sun-java6-jdk
```
The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages
```


Downloading: RSBot

---

### Post by Hosmion on 2009-11-06
Bump

---

### Post by varun.s.murthy on 2009-11-06
I have the same problem as well..

Had Java6 JDK installed on 9.04,then upgraded to 9.10 and java seems to be broken..:(

When i try to mark sun java6 JDK for installaton in Synaptic, I get the following error:

sun-java6-jdk:
  Depends: sun-java6-bin (=6-15-1) but 6-16-0ubuntu1.9.04 is to be installed

PS: Hope this post wont be considered as a thread-hijack. Please pardon me if so..

---

### Post by darshana on 2009-11-06
you are getting that error, because you may not set the right pet repositories. pls add those[1] repositories and try again.
[1]: 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse

---

### Post by Hosmion on 2009-11-07
> **darshana said:**
> you are getting that error, because you may not set the right pet repositories. pls add those[1] repositories and try again.
[1]: 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse


Software --> Authentication?  There?

---

### Post by Hosmion on 2009-11-07
Bump

---

### Post by scouser73 on 2009-11-07
How-to for 32 bit Ubuntu 9.04 & 9.10

Remove the old version

First you'll want to remove the old version. If it's installed from the repositories, do it like this:

**System** - **Administration** - **Synaptic Package Manager**

Query: sun java

Tick all installed packages and choose complete removal.

If it's installed manually in **/opt/java**, simply delete the folder **/opt/java**. If you don't know how to do that, see the bottom of this page (under the header Removal).


Get JRE

Get the right file from the Java website: [[COLOR="Red"]**Get Java**[/COLOR]]("http://www.java.com")

For 32 bit you want Linux (self-extracting file). Not Linux RPM, because RPM is not built for Ubuntu, but for other Linux distro's.

Store the file in your home folder.

Note: the terminal commands in this how-to possibly refer to an older version of JRE. When there's a newer version, you can simply adapt the file names in the terminal commands.


Install JRE (32-bit)

1. Go to the folder opt, with the following command:

**Applications** - **Accessories** - **Terminal**

**cd /opt**

Press Enter.


2. Create a new subfolder, with the following command line.

**sudo mkdir java**

Press Enter.

3. Go to the new folder, with the following command.

**cd java**

Press Enter.


4. Create a new subfolder, with the following command.

**sudo mkdir 32**

Press Enter.


5. Move the JRE file that you just downloaded, into this newest folder, with the following command.

s**udo mv ~/jre-6u17-linux-i586.bin /opt/java/32**

Press Enter.


6. Make the file executable, with the following command.

**sudo chmod 755 /opt/java/32/jre-6u17-linux-i586.bin**

Press Enter.

Now you're going to install JRE, by executing this file.


7. First, go to the new folder, with the following command.

**cd /opt/java/32**

Press Enter.


8. Execute the file, with the following command.

**sudo ./jre-6u17-linux-i586.bin**

Press Enter.

Now the license agreement appears.
Press as many times on the space bar, until you see the following text:
Do you agree to the above license terms? [yes or no]

Type:
yes

Press Enter.


Make the new JRE the default

9. Now you'll want to tell the system, that there's a new Java version available.

Copy & paste:

**sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_17/bin/java" 1**

Press Enter.

Note: are you updating from a previous Java version, which you have removed manually? Then you'll need to execute the above command twice, because you'll get an error message the first time.


10. Tell the system, that the new Java must be the default:


**sudo update-alternatives --set java /opt/java/32/jre1.6.0_17/bin/java**

Press Enter.


Installing the Firefox plugin

11. Installing the Firefox plugin is simple. First execute the following command, in order to create a certain folder (if it doesn't exist already).

**mkdir ~/.mozilla/plugins**

Press Enter.

If it exists already, you'll see a notification of that.


12. Now remove the IcedTea plugin, if it has been installed.

**sudo apt-get remove icedtea-gcjwebplugin**

Press Enter.


13. Remove a former version of the Java plugin.

**rm ~/.mozilla/plugins/libjavaplugin_oji.so**

Press Enter.


14. Now you can install the plugin, by creating a symbolic link (you tell Firefox, where the plugin is located).

**ln -s /opt/java/32/jre1.6.0_17/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/**

Press Enter.

---

### Post by Hosmion on 2009-11-08
I'm 64-bit though..  Will all of this work for 64-bit?

---

### Post by Hosmion on 2009-11-08
Bump

---

### Post by scouser73 on 2009-11-08
You should follow the instructions here for installing on a 64 bit PC.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Rayve on 2009-11-09
scouser73,

This worked perfectly for me in 32-bit 9.04!!  Thanks!!

---

### Post by scouser73 on 2009-11-09
Glad to help mate.

---

### Post by Hosmion on 2009-11-09
OMG!  Your the best!

---

