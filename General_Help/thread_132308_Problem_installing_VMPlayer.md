---
title: "Problem installing VMPlayer"
date: 2006-02-18
forum: General Help
---

### Post by szdavid on 2006-02-18
Hi,

I am trying to install VMplayer but I have this error : 

> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
The directory of kernel headers (version 2.6.12swsusp2) does not match your
running kernel (version 2.6.12-10-686).  Even if the module were to compile
successfully, it would not load into the running kernel.


I know where it comes from : i tried to compile a kernel and created 2.6.12swsusp2 but i do not use it (it crashes) and use 2.6.12-10-686 ; 

how to solve this problem ?

Thanks

---

### Post by kenweill on 2006-02-18
[https://wiki.ubuntu.com/InstallingVmPlayer](https://wiki.ubuntu.com/InstallingVmPlayer)

PS.
Everytime you update to the new kernel, you also have to install the equivalent linux-headers for the kernel. And reinstall VMware Player.
I have experienced this before. VMware Player player does't load on newly updated kernel. You have to install linux-headers for the updated kernel and reinstall VMware Player.
Don't worry, the .vmx file will not be harmed.

---

### Post by szdavid on 2006-02-18
ok, i had to restatrt the installation from start...

Thanks

---

### Post by kenweill on 2006-02-18
You're welcome.
I used to have that problem after updating the kernel.
The worst is that I can't connect to the internet without VMware Player installed. It has something to do with my internet connection which is Windows based only connection.

Anyway, if you have any problems, just post a question to this forum.
And enjoy using Ubuntu.

---

### Post by Dwayne on 2006-02-20
kenweill, I am REALLY a newbie and need help.  I got as far as the:  sudo apt-get install linux-headers-`uname -r`  Your direction says to use the version number from above but to a newbie there are multiple version numbers, i.e., version 2.6.12-9-386 and version 3.4.5 20050809.  It doesn't seem to matter which I use because I receive the error:  E: Command line option 'r' [from -r] is not known.


I suspect I am incorrect with my sytax and what is expected in your:  sudo apt-get install linux-headers-`uname -r`  command.  Could you give an example for a dummy!  :)

I would never stick with this Linux challenge were it not for you folks who know what is going on!

Dwayne

---

### Post by kenweill on 2006-02-21
[QUOTE=Dwayne]kenweill, I am REALLY a newbie and need help.  I got as far as the:  sudo apt-get install linux-headers-`uname -r`  Your direction says to use the version number from above but to a newbie there are multiple version numbers, i.e., version 2.6.12-9-386 and version 3.4.5 20050809.  It doesn't seem to matter which I use because I receive the error:  E: Command line option 'r' [from -r] is not known.


I suspect I am incorrect with my sytax and what is expected in your:  sudo apt-get install linux-headers-`uname -r`  command.  Could you give an example for a dummy!  :)

I would never stick with this Linux challenge were it not for you folks who know what is going on!

Dwayne[/QUOTE]

Replace 'uname -r' with your kernel version.

Example:
kenweill@server-lazi-cec:~$ uname -r
2.6.12-10-386

That is my kernel version, currently loaded.

Then type:
sudo apt-get install linux-headers-2.6.12-10-386
(Or you can install the linux-headers from synaptic)

Then continue with the steps provided with the manual.

---

### Post by Dwayne on 2006-02-21
Thanks.  With everything being so new to me it was a struggle but I got it!  :)

---

