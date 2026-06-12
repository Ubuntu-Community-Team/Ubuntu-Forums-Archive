---
title: "File not there, but it is"
date: 2011-06-13
forum: General Help
---

### Post by Killer505225 on 2011-06-13
Alright, so I download and installed BYOND from [http://Byond.com](http://Byond.com)
I used Wget to download it, and used unzip to unzip it.
It now has its own file at
/root/byond

The thing I'm looking for is
/root/byond/bin
And inside that is a file called DreamDaemon and DreamDownload
I tried to find them using the terminal to see if I installed correctly, and I got this
root@ubuntu:~/byond/bin# /DreamDaemon
bash: /DreamDaemon: No such file or directory

I tried reinstalling, nothing helps!
It has Executable checked, it's a sh file, and I'm running a VPS, so it's not my home computer.

---

### Post by papibe on 2011-06-13
Try:
```
$ ./DreamDaemon 
```
Regards.

---

### Post by jonnyboysmithy on 2011-06-13
I'm pretty new to this stuff but maybe the downloaded file isn't right?
why would you put  root@ubuntu:~/byond/bin# /DreamDaemon
instead of this??   root@ubuntu:/byond/bin/DreamDaemon

---

### Post by idoitprone on 2011-06-14
> **jonnyboysmithy said:**
> I'm pretty new to this stuff but maybe the downloaded file isn't right?
why would you put  root@ubuntu:~/byond/bin# /DreamDaemon
instead of this??   root@ubuntu:/byond/bin/DreamDaemon

the op make an simple mistake of differentiating between relative and absolute paths

As papibe noted he forgot the period "." which represents the current directory

jonnboysmithy your path is correct and its an absolute path but the op want to save a few key presses and use relative paths

btw try to see if on /root/ or /home/byond/ makes whole lot of difference

---

