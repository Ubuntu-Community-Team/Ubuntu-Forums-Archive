---
title: "How Do I Install .tar.gz Files???"
date: 2011-11-13
forum: General Help
---

### Post by Uchiha_Kori on 2011-11-13
I tried to install the Java JDK for Linux ([http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u1-download-513651.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u1-download-513651.html)) 

How do I install a .tar.gz file?

---

### Post by leugi101 on 2011-11-13
I believe you can just install java using the ubuntu software center, type in java, find the one you want and install

---

### Post by Uchiha_Kori on 2011-11-13
I tried downloading it off the web site because I couldn't get Software Center to install it for me. It installs, then abruptly stops, giving an error message.

So again, how can I install .tar.gz files?

---

### Post by Frogs Hair on 2011-11-13
You could look at this link , it was easy to find , so I'm sure there are others . I think the software center is a better option so , you mat want to try again .  [http://www.twm-kd.com/linux/install-oracle-java-sdk-in-ubuntu-11-10/](http://www.twm-kd.com/linux/install-oracle-java-sdk-in-ubuntu-11-10/)  

Here is a general instruction . [http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

---

### Post by alphacrucis2 on 2011-11-13
> **Uchiha_Kori said:**
> I tried downloading it off the web site because I couldn't get Software Center to install it for me. It installs, then abruptly stops, giving an error message.

So again, how can I install .tar.gz files?

.tar.gz is just a compressed archive. It is like a zip file on Windows. How you install depends on what is contained in the archive. Looking at the link you specified suggests that you have downloaded the java devleopment kit. Does it contain a readme file?

---

### Post by haqking on 2011-11-13
First of all always search in the Software Centre or Synaptic Package manager to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)

You can also use Gdebi package installer or look at dpkg.

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set 

Have fun

Regards

haqking

---

### Post by galvatron408 on 2011-11-13
you don't install a tar.gz file. I think you meant, how do you extract a tar.gz file...

Simple....

tar zxvf file.tar.gz

z means use gzip or gunzip ( depending on whether you are creating or extracting )
x means extract ( get files out of the tar )
v means verbose ( show you what is happening )
f means forceful ( don't prompt )

Once you extract the java archive, you just have to set JAVA_HOME to use it. There isn't really any installation required.

---

### Post by 3Miro on 2011-11-14
If Software is available in the Software Center, then this is the one that you should use. The preferred methods are: 

1. Software Center
2. Unofficial PPA
3. a .deb package
4. source or other binary in .tar file

If you are having trouble with the Software Center, then give us the error message so we can solve that problem.

---

### Post by Uchiha_Kori on 2011-11-14
Thanks for all the replies, I appretiate them all. I had an issue with the software center, but it corrected itself somehow. I restarted the computer, and that was all it took it looks like. Thanks for all the help. :)

---

