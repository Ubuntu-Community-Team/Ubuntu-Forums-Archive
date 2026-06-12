---
title: "java help"
date: 2006-05-02
forum: General Help
---

### Post by sethcode on 2006-05-02
I just installed ubuntu(breezy badger). I downloaded some packages myself, but then used AUTOMATIX to download the rest. I am trying to set up java's jdk 5.0 to learn to program a little before I start school. I have it installed on my windows partition fine, but I heard programing in linux was more fun. I downloaded the correct package from SUNS website. It saved to the desktop, then I moved it to my /home/ directory. I got execute permissions using the:
chmod +x jdk-1_5_0_06-linux-i586.bin command. Then I used the: ./(filename) to unpack it(if thats what it does). It unpacked to a folder jdk1.5.0_06 that looks right. I think now I need to set a PATH, but I cant figure out how. I have a version of java installed on my machine, when I type java -version, it responds with version info on java-1.4.2-gcj-4.0-1.4.2.0 witch I found in my usr/lib/jvm/ directory. I dont think I can compile with it, because when I try there is no "javac" found.  I tried to navigate to differant directories, and I tried to copy the jdk folder into the /usr/lib/jvm folder but didnt have write permissions. I have been reading forums and googleing now for a while and cant find anything. I think it has something do do with just setting a path variable, but any help would be greatly appreciated.

---

### Post by ZylGadis on 2006-05-02
You need to create a .deb out of the java installation files, and then install it. There is a guide somewhere around, I'll post here when I find it. In the meantime, you can call the java stuff you have installed simply by including the full path to the binaries; for example,

```
/home/myusername/jdk1.5.0_06/bin/javac MyClass.java
```

You also need to set the JAVA_HOME environment variable:

```
export JAVA_HOME=/home/myusername/jdk1.5.0_06/
echo $JAVA_HOME
```

Hope that helps.

---

### Post by ZylGadis on 2006-05-02
Right, here's the link:
[http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part](http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part)
:)

---

### Post by sethcode on 2006-05-02
thanks for the reply.

---

