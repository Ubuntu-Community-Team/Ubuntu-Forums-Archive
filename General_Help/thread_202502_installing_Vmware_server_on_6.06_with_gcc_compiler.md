---
title: "installing Vmware server on 6.06 with gcc compiler"
date: 2006-06-23
forum: General Help
---

### Post by aarbear26 on 2006-06-23
I tried to install the VMware server package, and it has been going pretty well.  Everything worked fine and they told me to run the vmware-config.pl program.  I did and it gives me this message:

[I]None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)?

[/I]I answer yes, then it gives me this:

[I]Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

[/I]I have gcc installed, and it is in the /usr/bin directory.  (it is version 4.0)  But for the life of me i can't find any c header files or a directory even close to that one.  Obviously, I am not a programmer so i don't even know what a header file is.  I assume I have to run something in gcc to make these header files before i can do anything.  Any help even in the right direction would be very helpful.  I thank anyone ahead of time.

Aaron

---

### Post by aarbear26 on 2006-06-23
well, i found my own answer.  For others with this problem, you can see [here]("http://ubuntuforums.org/showthread.php?t=183209")

i had to run
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
i have no idea where that line comes from, but it worked

---

