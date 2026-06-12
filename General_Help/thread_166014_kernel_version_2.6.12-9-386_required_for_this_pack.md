---
title: "kernel version 2.6.12-9-386 required for this package"
date: 2006-04-25
forum: General Help
---

### Post by medya on 2006-04-25
I had installed truecrypt by a .Deb file, (it is a program to make encrypt drives)
it used to work well , for days, today I tried to run the program , it told me that it cant load kernel or something that I dont remember.

I tried to un-install the package . and re-install it 

> while I do Reinstall I still get another error about kernel.
fred@ubuntu:~$ cd Desktop
fred@ubuntu:~/Desktop$ sudo dpkg -i truecrypt_4.2-0_i386.deb
(Reading database ... 81075 files and directories currently installed.)
Unpacking truecrypt (from truecrypt_4.2-0_i386.deb) ...
[B]ERROR: Default Linux kernel version 2.6.12-9-386 required for this package.
dpkg: error processing truecrypt_4.2-0_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 truecrypt_4.2-0_i386.deb
[/B]fred@ubuntu:~/Desktop$




[I]+ by the way I have another strange problem with apt-get command, which hasnt been solved yet. it is here
[http://ubuntuforums.org/showthread.php?t=164898](http://ubuntuforums.org/showthread.php?t=164898)
it may be related to this problem.[/I]

---

### Post by medya on 2006-04-26
plz somebody help. i need my encryption program so much.

---

### Post by medya on 2006-04-27
hey I found out in my boot menu I can ask ubuntu to boot from 2.6.12.9.386
while it was loading from Kernel 2.6.12.10.686
and now my program works fine...

anybody knows what is this kernel ? is 2.6.12.10 686 kernel newer than 2.6.12.9 386  ?
would I loose much things if I load linux from 2.62.12.9 386  instead of that one?

 I would appericate more info about what this kernel is and what are those 383 686 ...blah blahs

---

### Post by Qrk on 2006-04-27
The 386 and 686 correspond to the type of processor the kernel was compiled for. i686 is a pentium II or higher and i386 is for lower processors. (the i386 of the 80's that started the computer revolution)

The 686 kernel isn't newer than the 386, but 2.6.12.10 is newer than 2.6.12.9.

---

### Post by medya on 2006-04-30
my cpy is celeron 2000 ,   should I use 686 ?  (my program truecrypts doesnt work in version 10 )

---

### Post by Cleaner on 2006-04-30
The truecrypt Ubuntu package from the website only fits systems with kernel 2.6.12-9-386. So if you updated your kernel (what is definitely a good thing to do) you have to compile truecrypt for your kernel.

What you have to do in short (for more info search the forums or have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=114225&page=2") which is summarized here):

1. Compile kernel modules (in this example for kernel 2.6.12-10-686):
  sudo apt-get install build-essential gcc-3.4 linux-headers-2.6.12-10-686 linux-source-2.6.12
  cd /usr/src/
  sudo tar xvjf linux-source-2.6.12.tar.bz2
  sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
// the following line prevents that you have to answer hundrets of config questions
  sudo cp /boot/config-2.6.12-10-686 /usr/src/linux/.config
  sudo make -C /usr/src/linux-source-2.6.12 modules

At this point you can grab a cup of coffee. This will take a while. ;)

2. Get the truecrypt sourcecode package and extract it

3. Build truecrypt
  cd ./Linux
  ./build.sh

4. Install truecrypt
  sudo ./Linux/install.sh
  Answer the upcoming questions as follows:
    Install binaries to [/usr/local/bin]: <Return>
    Install man page to [/usr/local/man]: /usr/share/man
    Allow non-admin users to run TrueCrypt [y/N]: y


Good luck :)

Flo

---

### Post by medya on 2006-05-02
> **Cleaner]The truecrypt Ubuntu package from the website only fits systems with kernel 2.6.12-9-386. So if you updated your kernel (what is definitely a good thing to do) you have to compile truecrypt for your kernel.

What you have to do in short (for more info search the forums or have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=114225&page=2") which is summarized here):

1. Compile kernel modules (in this example for kernel 2.6.12-10-686):
  sudo apt-get install build-essential gcc-3.4 linux-headers-2.6.12-10-686 linux-source-2.6.12
  cd /usr/src/
  sudo tar xvjf linux-source-2.6.12.tar.bz2
  sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
// the following line prevents that you have to answer hundrets of config questions
  sudo cp /boot/config-2.6.12-10-686 /usr/src/linux/.config
  sudo make -C /usr/src/linux-source-2.6.12 modules

At this point you can grab a cup of coffee. This will take a while.  said:**
> : <Return>
    Install man page to [/usr/local/man]: /usr/share/man
    Allow non-admin users to run TrueCrypt [y/N]: y


Good luck :)

Flo

I did all you said  in step 3 I got this error .

fred@ubuntu:~/Desktop/truecrypt-4.2$ ./Linux/build.sh
Checking build requirements...
Error: Administrator (root) privileges required for kernel source configuration.fred@ubuntu:~/Desktop/truecrypt-4.2$ sudo ./Linux/build.sh
Password:
Checking build requirements...
Building kernel module... ./Linux/build.sh: line 110: cd: Kernel: No such file or directory
Error: Failed to build kernel module
fred@ubuntu:~/Desktop/truecrypt-4.2$

---

### Post by medya on 2006-05-02
iI re runed .build.sh and it worked this time, STRANGE .

---

### Post by Cleaner on 2006-05-29
From what you're saying I now assume that it's necessary to run build.sh in the Linux directory. I will change that in the "manual".

---

