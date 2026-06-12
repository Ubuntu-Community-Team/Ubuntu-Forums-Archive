---
title: "Installing Java jdk tar"
date: 2012-07-03
forum: General Help
---

### Post by vizhang on 2012-07-03
Hi guys,

I'm trying to install java, and what I thought you do is just to extract the binaries/files from the .tar  , and move it to the binaries folder in /usr/bin  .I've scoured the forums and have found this similar post to the problem I'm having: [http://ubuntuforums.org/showthread.php?t=1724227]("http://ubuntuforums.org/showthread.php?t=1724227").

When I do #java -version, I get *" java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory "*

Unlike the previous post, I am on a more basic linux kernel than the Ubunutu build (so I don't have the sudo update-alternatives --install) option. **What do I do to install it? :(**

Thanks for any help!

---

### Post by msammels on 2012-07-03
Try this:

```
sudo apt-get install openjdk-7-jre
sudo apt-get install icedtea6-plugin
```

---

### Post by vizhang on 2012-07-04
So actually, the kernel is not ubunutu but a very basic version so I don't have apt-get commands :O

Was wondering if you knew how to install java using the tar file!

---

### Post by vizhang on 2012-07-04
From the read-me file, the instructions seem so simple:
----------------------------------------------------------------
[SIZE="1"]This procedure installs the Java Development Kit (JDK) for 64-bit Linux, using an archive binary file (.tar.gz).

These instructions use the following file:

    jdk-7u<version>-linux-x64.tar.gz
1. Download the file. Before the file can be downloaded, you must accept the license agreement. The archive binary can be installed by anyone (not only root users), in any location that you can write to. However, only the root user can install the JDK into the system location.

2. Change directory to the location where you would like the JDK to be installed. Move the .tar.gz archive binary to the current directory.

3. Unpack the tarball and install the JDK.

    % tar zxvf jdk-7u<version>-linux-x64.tar.gz
The Java Development Kit files are installed in a directory called jdk1.7.0_<version> in the current directory.

4. Delete the .tar.gz file if you want to save disk space.[/SIZE]
--------------------------------------------------------------------------------

But at step 3, it just says "install the JDK"... what does that entail?

---

