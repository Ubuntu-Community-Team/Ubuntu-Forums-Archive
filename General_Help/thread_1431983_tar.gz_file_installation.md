---
title: "tar.gz file installation"
date: 2010-03-17
forum: General Help
---

### Post by rdema19403 on 2010-03-17
I downloaded a tar.gz file I opened it up in the terminal with the tar -zxvf command but how do you install it
here is a screen shot of the file 
rd@rd-laptop:~$ tar -zxvf /home/rd/Desktop/FacebookPlugIn-1.0.3.tar.gz 
FacebookPlugIn-1.0.3/ 
FacebookPlugIn-1.0.3/README.tr 
tar: FacebookPlugIn-1.0.3/README.tr: Cannot open: File exists 
FacebookPlugIn-1.0.3/README.jp 
tar: FacebookPlugIn-1.0.3/README.jp: Cannot open: File exists 
FacebookPlugIn-1.0.3/FacebookPlugIn_Install.sh 
tar: FacebookPlugIn-1.0.3/FacebookPlugIn_Install.sh: Cannot open: File exists 
FacebookPlugIn-1.0.3/README.de 
tar: FacebookPlugIn-1.0.3/README.de: Cannot open: File exists 
FacebookPlugIn-1.0.3/README 
tar: FacebookPlugIn-1.0.3/README: Cannot open: File exists 
FacebookPlugIn-1.0.3/README.es 
tar: FacebookPlugIn-1.0.3/README.es: Cannot open: File exists 
FacebookPlugIn-1.0.3/README.it 
tar: FacebookPlugIn-1.0.3/README.it: Cannot open: File exists 
FacebookPlugIn-1.0.3/README.tw 
tar: FacebookPlugIn-1.0.3/README.tw: Cannot open: File exists 
FacebookPlugIn-1.0.3/LICENSE 
tar: FacebookPlugIn-1.0.3/LICENSE: Cannot open: File exists 
FacebookPlugIn-1.0.3/README.cn 
tar: FacebookPlugIn-1.0.3/README.cn: Cannot open: File exists 
FacebookPlugIn-1.0.3/README.fr 
tar: FacebookPlugIn-1.0.3/README.fr: Cannot open: File exists 
FacebookPlugIn-1.0.3/libnpfbook_1_0_3.so 
tar: FacebookPlugIn-1.0.3/libnpfbook_1_0_3.so: Cannot open: File exists 
tar: FacebookPlugIn-1.0.3: Cannot utime: Operation not permitted 
tar: Error exit delayed from previous errors 
rd@rd-laptop:~$ 
iam not sure how to install it
I think you have to navigate to the file but I donot know the terminal command to find it
i am running ubuntu 9.04 desktop edition
Thanks in advance

---

### Post by jtprince on 2010-03-17
typically:

```
## unzip the archive (this will usually create the directory "file")
tar -xzvf file.tar.gz
## cd=change directory into "file"
cd file
## read the README or INSTALL file for instructions
gedit README
## each language will likely have its own method for installation
## C/C++ type programs will typically install like this (should be in README)
./configure
make
sudo make install
## other types will have their own method for installation
```

---

### Post by oldos2er on 2010-03-17
If there's an English README, read it. It looks like there are two *so files to be installed by running FacebookPlugIn_Install.sh.

---

### Post by n0dix on 2010-03-17
> **rdema19403 said:**
> 
I think you have to navigate to the file but I donot know the terminal command to find it
i am running ubuntu 9.04 desktop edition
Thanks in advance

To look the folders and files in a directory do: ls
To move to a directory do: cd.
Look in Google there are thousands of pages with information.

---

### Post by km0r3 on 2010-03-17
> **jtprince said:**
> typically:

```
## unzip the archive (this will usually create the directory "file")
tar -xzvf file.tar.gz
## cd=change directory into "file"
cd file
## read the README or INSTALL file for instructions
gedit README
## each language will likely have its own method for installation
## C/C++ type programs will typically install like this (should be in README)
./configure
make
sudo make install
## other types will have their own method for installation
```

+1 

This is the usually sufficient way to do the job.

---

