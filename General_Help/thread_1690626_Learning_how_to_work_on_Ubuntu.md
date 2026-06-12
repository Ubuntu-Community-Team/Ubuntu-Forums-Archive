---
title: "Learning how to work on Ubuntu"
date: 2011-02-18
forum: General Help
---

### Post by SigepLinux on 2011-02-18
Hey all, I'm a newly converted Linux user. I am pretty proficient with windows but when it comes down to learning Linux I'm somewhat stumped at the moment. I'm having issues learning how to install programs such as gmote, updated versions of java, and general software besides those in the software center. I cant seem to make a .sh file work to install gmote and for the first time in a while I feel like a complete noob with computers. Any help would be much appreciated. I am Familiar with dos and such so the terminal is different but somewhat familiar.

---

### Post by Habeouscorpus on 2011-02-18
good news! You don't really need a shell script to get things installed! 

unless you want to, but that's your business. 

try this: 

```
 sudo apt-get install [program] 
```

If you have a .tar.gz, then extract the files, then type 

```
 cd /path/to/files
./configure && make && sudo make install 
```

And they should be installed! 

for more info, check out [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

good luck, and have fun with ubuntu!

(sorry about the lack of capitalization, this computer doesn't have sticky keys enabled.)

---

### Post by oldos2er on 2011-02-18
For Java, see [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

To run a .sh file, open a terminal, "cd" to the folder where the file is, make it executable **chmod +x foo.sh** , then run it **./foo.sh** . If the program needs to be installed system-wide and not just in your /home folder (and assuming you trust the site from where it came), use sudo: **sudo ./foo.sh**

Since programs in Linux can be downloaded in different forms (i.e. source code, precompiled binaries, deb or some other type of package) it helps to give specific info about what you're trying to install. It helps if you're new just to stick to the repositories til you've gained a little experience.

---

