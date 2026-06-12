---
title: "Can't get java to work properly"
date: 2012-06-02
forum: General Help
---

### Post by feathre on 2012-06-02
Hey guys,

I can't get java to work.  I just installed Ubuntu 12.04 today and I tried to install the oracle jre from their website.  I followed this guide EXACTLY

[http://www.liberiangeek.net/2012/04/install-oracle-java-runtime-jre-7-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-oracle-java-runtime-jre-7-in-ubuntu-12-04-precise-pangolin/)

If you are familiar with minecraft, I can launch MinecraftLauncher.jar when I type the appropriate command (java -jar MinecraftLauncher.jar) but once I "log in" it just disappears and does not load the appropriate jarfile to play the game. However, when I go to the main jarfile ../minecraft/bin/minecraft.jar and attempt to launch it, it says "Error: Invalid or corrupt jarfile minecraft.jar."  I don't see how it could be corrupt.  I think this is just the computer giving me a problem I don't know how to solve.  Was hoping someone may be able to help me.

Thank you!

---

### Post by linuxman94 on 2012-06-02
Assuming you are using the new launcher, try using the force update option to get a fresh jar.  It is quite possible that it got corrupted.

---

### Post by pbrane on 2012-06-02
FWIW, Minecraft runs perfectly fine on Openjdk 7. Also the proper command line for minecraft is 
```

java -Xms512M -Xmx1G -cp minecraft.jar net.minecraft.LauncherFrame

```
You can change the memory options if you like. Where did you get the launcher from? If you got it from [http://www.minecraft.net/download]("http://www.minecraft.net/download") then the launcher should be named *minecraft.jar*.

---

### Post by feathre on 2012-06-02
> **pbrane said:**
> FWIW, Minecraft runs perfectly fine on Openjdk 7. Also the proper command line for minecraft is 
```

java -Xms512M -Xmx1G -cp minecraft.jar net.minecraft.LauncherFrame

```You can change the memory options if you like. Where did you get the launcher from? If you got it from [http://www.minecraft.net/download](http://www.minecraft.net/download) then the launcher should be named *minecraft.jar*.

It's a special launcher for mods and whatnot.  Is nice to have but I  just want to get the game running at this point, so I tried your command  and here is what I got:

```
kevin@destroyerofworlds:~/minecraft/bin$ java -Xms512M -Xmx1G -cp minecraft.jar net.minecraft.LauncherFrame
Error: Could not find or load main class net.minecraft.LauncherFrame

```How do I force update to get a fresh jar?  I only copied the minecraft folder from my XP computer's Application Data folder and pasted it on this linux computer so I could play it.

Thanks guys

Edit:  Also, I tried OpenJDK before I installed Oracle's JRE and it would not work on my computer.  I was getting so many error messages while installing it and everytime I would fix one error there would be another one waiting behind it, and I just got sick of it... at least I know one JAR file is working.  Maybe this file is corrupted after all.  I'm gonna try to download a fresh copy of minecraft in the meantime and see if that does anything.

---

### Post by feathre on 2012-06-02
I am not sure if this is related?  I was just on wine's website and suddenly this error message popped up having to do with java.

[IMG]http://www1.picturepush.com/photo/a/8397199/img/8397199.png

---

### Post by QIII on 2012-06-03
I love Liberiangeek, but for future reference the middle link in my signature is much, much easier and will give you updates as Oracle releases them.

---

### Post by feathre on 2012-06-03
> **QIII said:**
> I love Liberiangeek, but for future reference the middle link in my signature is much, much easier and will give you updates as Oracle releases them.

Followed your instructions, everything was working fine until the install part.

```
kevin@destroyerofworlds:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  nvidia-settings
Use 'apt-get autoremove' to remove them.
Suggested packages:
  visualvm ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
The following packages will be upgraded:
  oracle-java7-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/14.8 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-02 23:54:48--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 64.145.89.17, 64.145.89.43
Connecting to download.oracle.com (download.oracle.com)|64.145.89.17|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-06-02 23:54:48--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 72.247.138.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|72.247.138.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-06-02 23:54:49--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|64.145.89.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 7.64M=0.001s

2012-06-02 23:54:49 (7.64 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by pbrane on 2012-06-03
It's much easier to use Openjdk 7 unless you REALLY have to use Oracle for some reason. Minecraft is not a good reason. If you get this **Error: Could not find or load main class net.minecraft.LauncherFrame** then most likely you are not running the original minecraft launcher. Also make sure you use the correct path to the launcher in that command.

Openjdk 7 is the opensource version of java, according to Oracle it's the new Java SE 7 Reference Implementation.

[http://lxnews.org/2011/09/05/oracle-stops-shipping-java/]("http://lxnews.org/2011/09/05/oracle-stops-shipping-java/")

---

### Post by feathre on 2012-06-03
> **pbrane said:**
> It's much easier to use Openjdk 7 unless you REALLY have to use Oracle for some reason. Minecraft is not a good reason. If you get this **Error: Could not find or load main class net.minecraft.LauncherFrame** then most likely you are not running the original minecraft launcher. Also make sure you use the correct path to the launcher in that command.

Openjdk 7 is the opensource version of java, according to Oracle it's the new Java SE 7 Reference Implementation.

[http://lxnews.org/2011/09/05/oracle-stops-shipping-java/](http://lxnews.org/2011/09/05/oracle-stops-shipping-java/)

Yes, but as I stated previously I was not able to install OpenJDK.  It was my first choice and the first thing I tried installing.  Also minecraft isn't the only reason I would like java, lol.  Tons of software as well as other games are dependent on it, I mean it is the #1 programming language in the world, and none of them are installing because they say I don't have java and error out.  For example, the synaptic package manager program and the game Limbo were also failures when I tried installing, all having error messages related to java not being implemented.

---

### Post by pbrane on 2012-06-03
Perhaps you could post the errors you receive when trying to install openjdk-7. And what Ubuntu version are you running? It sounds like you may be having issues other than just java. You should be able to install openjdk from the repos without errors.
Actually you should have been able to install Oracle java using QIII's link.

@QIII your links to webupd8 are messed up. There is a trailing **[/URL** for some reason.

---

### Post by QIII on 2012-06-03
Links fixed.

---

### Post by linuxman94 on 2012-06-03
> **feathre said:**
> It's a special launcher for mods and whatnot.  Is nice to have but I  just want to get the game running at this point, so I tried your command  and here is what I got:

```
kevin@destroyerofworlds:~/minecraft/bin$ java -Xms512M -Xmx1G -cp minecraft.jar net.minecraft.LauncherFrame
Error: Could not find or load main class net.minecraft.LauncherFrame

```How do I force update to get a fresh jar? ** I only copied the minecraft folder from my XP computer's Application Data folder and pasted it on this linux computer so I could play it.**

Thanks guys

Edit:  Also, I tried OpenJDK before I installed Oracle's JRE and it would not work on my computer.  I was getting so many error messages while installing it and everytime I would fix one error there would be another one waiting behind it, and I just got sick of it... at least I know one JAR file is working.  Maybe this file is corrupted after all.  I'm gonna try to download a fresh copy of minecraft in the meantime and see if that does anything.

The bold text is your issue.  You can't copy the entire folder from XP to Linux and expect it to work because the files in the bin/natives are for windows.  If you want to keep your saves, make a copy of the saves folder and delete the entire .minecraft.  Then you can launch the games through the launcher (you should just be able to double click on the file) and it will download the correct files.  After that, you can move your saves back.

I also suggest you use OpenJDK because it is far easier to keep updated and it is fully supported by Oracle as an open source implementation of Java.

---

### Post by QIII on 2012-06-03
I also recommend OpenJDK in my post.  However, it is not always recognized by the entire world -- even though it is the reference implementation of Oracle Java and Oracle recognizes it.

@feathre

In my post I mention that the Eugene San PPA has been troublesome for some users. Uninstall Oracle Java 7 *and  *OpenJDK, remove the Eugene San PPA from your sources list and follow the directions for webupd8 if you want to use the Oracle version or install OpenJDK from the repo.   I am going to remove the reference to Eugene San in my post for now.

---

### Post by feathre on 2012-06-03
> **pbrane said:**
> Perhaps you could post the errors you receive  when trying to install openjdk-7. And what Ubuntu version are you  running? It sounds like you may be having issues other than just java.  You should be able to install openjdk from the repos without errors.
Actually you should have been able to install Oracle java using QIII's link.

@QIII your links to webupd8 are messed up. There is a trailing **[/URL** for some reason.

Ubuntu 12.04.  The newest version...I said in first post.  Idk what this unity thing is but I can't even use desktop effects anymore.  It's like all the customizability has been stripped from Ubuntu.

Here is what happens when I try to install openjdk.

Message:
Package operation failed
The installation or removal of a software package failed.
Details >>
```
installArchives() failed: Selecting previously unselected package openjdk-7-jre. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 175349 files and directories currently installed.) 
Unpacking openjdk-7-jre (from .../openjdk-7-jre_7~u3-2.1.1~pre1-1ubuntu3_amd64.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Processing triggers for hicolor-icon-theme ... 
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ... 
Downloading... 
--2012-06-03 18:46:38--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz 
Resolving download.oracle.com (download.oracle.com)... 96.17.70.49, 96.17.70.56 
Connecting to download.oracle.com (download.oracle.com)|96.17.70.49|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following] 
--2012-06-03 18:46:38--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 72.247.138.174 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|72.247.138.174|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: http://download.oracle.com/errors/download-fail-1505220.html [following] 
--2012-06-03 18:46:39--  http://download.oracle.com/errors/download-fail-1505220.html 
Connecting to download.oracle.com (download.oracle.com)|96.17.70.49|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 5307 (5.2K) [text/html] 
Saving to: `./jdk-7u3-linux-x64.tar.gz' 
 
     0K .....                                                 100% 7.41M=0.001s 
 
2012-06-03 18:46:39 (7.41 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307] 
 
Download done. 
sha256sum mismatch jdk-7u3-linux-x64.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up openjdk-7-jre (7~u3-2.1.1~pre1-1ubuntu3) ... 
Errors were encountered while processing: 
 oracle-java7-installer 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 

```I don't even know why it has a message about oracle when I'm installing open JDK...

---

### Post by linuxman94 on 2012-06-03
[COLOR=black]The error you are getting is a result of the Eugene San PPA.  I suggest purging the PPA from your system.  You can use a command called ppa-purge[/COLOR] which will remove the PPA and all packages associated with it.  First you'll have to install the package ppa-purge and then purge the Eugene San PPA with this command:

```
sudo ppa-purge ppa:eugenesan/ppa
```

OpenJDK installed properly, but the error occured because it is trying to configure a package from the Eugene San PPA.

---

