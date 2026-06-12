---
title: "ubuntu 9.04 can't install .bin file"
date: 2009-07-04
forum: General Help
---

### Post by the_who on 2009-07-04
i'm download file postgresql-8.4.0-1-linux.bin from postgres site
when i'm trying to install it
usually i use command :

#./postgresql-8.4.0-1-linux.bin

and then the installation goes it self
but this happen in ubuntu 9.04 server :

bash: ./postgresql-8.4.0-1-linux.bin: No such file or directory

anyone have any solusion..because this thing very urgent

sory for my bad english

---

### Post by wojox on 2009-07-04
Try

```
chmod 755 postgresql-8.4.0-1-linux.bin
```

Then

```
./postgresql-8.4.0-1-linux.bin
```

---

### Post by the_who on 2009-07-04
ofcourse i have do that..but the result still same 
please help me...
anyone have try this thing?

thank

---

### Post by geirha on 2009-07-04
Are you sure you need postgresql 8.4? There's 8.3 in the repositories, which is much easier to install. [https://help.ubuntu.com/9.04/serverguide/C/postgresql.html](https://help.ubuntu.com/9.04/serverguide/C/postgresql.html)

---

### Post by the_who on 2009-07-04
thant doesn't matter which postgres version i will install

the problem is why ubuntu 9.04 can't install bin file
and i there's something i need to do when i'm installing from source not using apt-get

thank

---

### Post by geirha on 2009-07-04
Well, the error message «No such file or directory» usually means you are trying to run a file that does not exist. In your case, there's no file by that name in the current working directory (./) . Are you sure you are in the right directory? Where did you download it?

---

### Post by the_who on 2009-07-04
the problem comes different when i'm trying to install 
jdk-6u14-linux-i586.bin

installation likes goin well but just until "license agreement" 
and then appear :

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./jdk-6u14-linux-i586.bin: 475: ./install.sfx.14921: not found
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.

i'm really sure the problem not comes from file installation because installation success when i try on ubuntu 8.10

please help me

thank

---

### Post by the_who on 2009-07-04
i hope this think proof that i'm really sure i't not the wrong directory :

root@adil:/u01/source# ls
apache-tomcat-6.0.20.tar.gz  postgresql-8.4.0
jdk-6u14-linux-i586.bin      postgresql-8.4.0-1-linux.bin
jre-6u14-linux-i586.bin      postgresql-8.4.0(2).tar.gz
mod_mono-2.4.2.tar.bz2       xsp-2.4.2.tar.bz2
mono-2.4.2.tar.bz2
root@adil:/u01/source# chmod 755 postgresql-8.4.0-1-linux.bin
root@adil:/u01/source# ./postgresql-8.4.0-1-linux.bin
bash: ./postgresql-8.4.0-1-linux.bin: No such file or directory
root@adil:/u01/source#

and when i'm type " ./postgresql-8.4.0-1-linux.bin ", i'm just type " ./post "+"tab"+" ./postgresql-8.4.0- "+"tab" that proof the file is on that folder

thank

---

### Post by geirha on 2009-07-04
Indeed, you are certainly in the right dir, so my previous assumption is wrong.The only other thing I can think of is that maybe the binary is 32-bit while your system is 64-bit, or vice versa?

---

### Post by wojox on 2009-07-04
Try this

```
./postgresql-8.4.0-1-linux.bin --mode text
```

---

### Post by the_who on 2009-07-04
aha.. thats what i'm forgot


thankyu for your help
thankyu for your fast reply
thankyu very much

):P

---

### Post by wojox on 2009-07-04
Your Welcome
):P

---

