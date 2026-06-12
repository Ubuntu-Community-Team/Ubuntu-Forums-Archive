---
title: "minecraft help"
date: 2011-10-10
forum: General Help
---

### Post by ninja8889 on 2011-10-10
ok so im trying to get minecraft working on my computer ive downloaded java and installed it but when i try to run the minecraft.jar file i get a bunch of errors im using kubuntu 11.04. ive tried a couple different clients but none of them work either. whenever i try to run it in konsole i get this error.
 
bash: /home/user/minecraft/minecraft.jar: cannot execute binary file
 
 
and when i try a client i get
 
/home/user/minecraft/MinecraftSP.jar: line 1: $'pk\003\004': command not found
/home/user/minecraft/MinecraftSP.jar: line 2: $'z\220t=': command not found
/home/user/minecraft/MinecraftSP.jar: line 3: y?T=?rb??META-INF/MANIFEST.MFManifest-version::no such file or directory
/home/user/minecraft/MinecraftSP.jar: line 4: Ant-version:: command not found
/home/user/minecraft/MinecraftSP.jar: line 5: syntax error near unexpected token`('
/home/user/minecraft/MinecraftSP.jar: line 5:`created-by: 16.3-bo1-279 (Apple Inc.)
 
any help would be apreaciated

---

### Post by papibe on 2011-10-10
Hi ninja8889, Welcome to the forums!

I'm not very competent on minecraft, but here's a few pointers:
- It is build using Java.
- You have to install Java to use it.
- To run it you run it as an argument of a Java call.

Here's a [thread]("http://ubuntuforums.org/showthread.php?t=1840956&highlight=minecraft") that have more information.

Regards.

---

### Post by ninja8889 on 2011-10-10
ive got java how to i run it as an argument of java

---

### Post by papibe on 2011-10-10
Did you check the thread I linked?

This is from that thread:
```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```
Regards.

---

### Post by ninja8889 on 2011-10-10
okay then i get 
 
the program 'java' can be found in the following packages:
gcj-4.4-jre-headless
gcj-4.5-jre-headless
openjdk-6-jre-headless
 
which one should i use

---

### Post by papibe on 2011-10-10
Then you don't Java installed. To install it do this:

Enable the partner's repository:
```
sudo add-apt-repository "deb http://archive.canonical.com/ natty partner"
```
Update your sources:
```
sudo apt-get update
```
And then install the java packages:
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk sun-java6-plugin sun-java6-fonts
```
Hope that helps,
Regards.

---

