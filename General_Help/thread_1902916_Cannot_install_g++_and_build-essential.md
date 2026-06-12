---
title: "Cannot install g++ and build-essential"
date: 2012-01-01
forum: General Help
---

### Post by erelsgl on 2012-01-01
I don't have g++:
  ```
erelsgl@ubuntu:/etc/apt$ which g++ 

erelsgl@ubuntu:/etc/apt$   

erelsgl@ubuntu:/etc/apt$ g++ 

The program 'g++' can be found in the following packages:
  * g++
  * pentium-builder 
Try: sudo apt-get install <selected package>

```So I try to install it:

 ```

erelsgl@ubuntu:~/srilm$ sudo apt-get install g++ 

...



Setting up g++ (4:4.4.3-1ubuntu1) ...
update-alternatives: error: alternative path /usr/bin/g++ doesn't exist.
dpkg: error processing g++ (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 g++
E: Sub-process /usr/bin/dpkg returned an error code (1)


```I also try to install build-essential, and get the same results.

I also try to complete the configuration manually by:
```
sudo dpkg --configure -a 
```and get the same results.

I also tried "sudo apt-get update" and "dpkg --purge g++", but it didn't help.

Here is my apt-cache:

```
erelsgl@ubuntu:~/srilm$ apt-cache policy g++ build-essential
g++:
  Installed: 4:4.4.3-1ubuntu1
  Candidate: 4:4.4.3-1ubuntu1
  Version table:
 *** 4:4.4.3-1ubuntu1 0
        500 http://il.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
build-essential:
  Installed: (none)
  Candidate: 11.4build1
  Version table:
     11.4build1 0
        500 http://il.archive.ubuntu.com/ubuntu/ lucid/main Packages

```Can you help me?

---

### Post by rsvancara on 2012-01-01
What is your /etc/apt/sources configured for the download mirror?

---

