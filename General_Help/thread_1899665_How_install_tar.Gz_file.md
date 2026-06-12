---
title: "How install tar.Gz file"
date: 2011-12-24
forum: General Help
---

### Post by Shafiq16 on 2011-12-24
How i install tar.Gz files in ubuntu i searched on google but i cant undrstand...How to
i download these files on pakages.Debian.Org
.Can any one help me plz..

---

### Post by elliotn on 2011-12-24
tar.gz are like zip, you have to untar it then read the read me file inside.

what software do u want to install ?

---

### Post by haqking on 2011-12-24
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

### Post by Shafiq16 on 2011-12-26
Thanks dear, but it is a source file i cant install it using the terminal.
Kindly just tell me the commands which r used in terminal to install a source file. I m a bigginner of ubuntu...

---

### Post by sirspazzolot on 2011-12-26
```
tar -xzvf package.tar.gz
cd package
./configure
make
make install
```

running those commands will ideally compile your package for you. if it complains about permission, precede the commands with sudo. in my (admittedly limited) experience, this process often does not work right away. if it doesn't work, read the output and look for a package that is missing. install that package and try again. HOWEVER, if you got it from the debian site it's most likely in the official repositories so USE THE SOFTWARE CENTRE or synaptic. or even apt-get. there's no reason to make this more complicated than it has to be.

EDIT: haqking's post is actually much better than mine, but it doesn't seem like you're interested in actually understanding what you're doing.

---

### Post by haqking on 2011-12-26
> **Shafiq16 said:**
> Thanks dear, but it is a source file i cant install it using the terminal.
Kindly just tell me the commands which r used in terminal to install a source file. I m a bigginner of ubuntu...

If you read my post and the links it explains about source files.

---

### Post by vsbp on 2012-05-08
> **elliotn said:**
> tar.gz are like zip, you have to untar it then read the read me file inside.

what software do u want to install ?
i have codeblocks_8.02-Oubuntu.deb.tar.gz in pendrive and how to install codeblocks in ubuntu .

---

### Post by Cheesemill on 2012-05-08
> i have codeblocks_8.02-Oubuntu.deb.tar.gz in pendrive and how to install codeblocks in ubuntu .
Don't use the file you have downloaded, install it from the software centre instead.

In fact the version in Software Centre is newer than the version you have downloaded.

---

