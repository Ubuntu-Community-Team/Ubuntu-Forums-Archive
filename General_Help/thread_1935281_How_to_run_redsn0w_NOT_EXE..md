---
title: "How to run redsn0w NOT EXE."
date: 2012-03-04
forum: General Help
---

### Post by 4042966262 on 2012-03-04
how do i make it tun!!
redsn0w file (linux) downloaded from [HERE]("http://www.iphoneworld.ca/news/2009/07/09/download-redsn0w-v08-linux-mac-windows-firmware-v30-iphone-2g-3g-3gs-itouch-jailbreak-unlock-tool/")
sitting in downloads, on desktop (extracted and un) and the redsn0w file on desktop.
now.. terminal fun
***everything must be explained clearly! im a noob who loves linux!!***

**Attempt 1**
coffeegulpers@coffeegulpers:~$ cd ~/Desktop/redsn0w-linux_0.8
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ chmod a+x redsn0w
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ redsn0w
redsn0w: command not found
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
\coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$  ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ su

[B]Attempt 2:
[/B]coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ cd Desktop
bash: cd: Desktop: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ cd
coffeegulpers@coffeegulpers:~$ cd Desktop
coffeegulpers@coffeegulpers:~/Desktop$ chmod +x redsn0w
coffeegulpers@coffeegulpers:~/Desktop$ su
Password: 
su: Authentication failure
coffeegulpers@coffeegulpers:~/Desktop$ su
Password: 
su: Authentication failure
coffeegulpers@coffeegulpers:~/Desktop$ su
Password: 
su: Authentication failure
coffeegulpers@coffeegulpers:~/Desktop$ su
Password: 
su: Authentication failure
coffeegulpers@coffeegulpers:~/Desktop$ su
Password: 
su: Authentication failure
coffeegulpers@coffeegulpers:~/Desktop$ sudo su
[sudo] password for coffeegulpers: 
root@coffeegulpers:/home/coffeegulpers/Desktop# ./ redsn0w
bash: ./: Is a directory
root@coffeegulpers:/home/coffeegulpers/Desktop# ^C
root@coffeegulpers:/home/coffeegulpers/Desktop# [B]

How do i get redsn0w to run?!:confused:

[/B]

---

### Post by CharlesA on 2012-03-04
There is no space between ./ and the file name.

It also looks like you are missing some dependencies, but I don't know what packages include them.

---

### Post by duncan12 on 2012-03-04
In Ubuntu, run ```
sudo -s
``` not ```
su
```

---

### Post by 4042966262 on 2012-03-04
> **CharlesA said:**
> There is no space between ./ and the file name.

It also looks like you are missing some dependencies, but I don't know what packages include them.

```
root@coffeegulpers:/home/coffeegulpers/Desktop# ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
root@coffeegulpers:/home/coffeegulpers/Desktop# 

```

tried with and without space.

---

### Post by 3rdalbum on 2012-03-04
Your first attempt was correct, but you are missing the "libwx-gtk2" library. You should be able to search and find it in the technical items in Software Center.

---

### Post by 4042966262 on 2012-03-04
> **3rdalbum said:**
> Your first attempt was correct, but you are missing the "libwx-gtk2" library. You should be able to search and find it in the technical items in Software Center.
insalled both libwx-gtk2 options..

```
coffeegulpers@coffeegulpers:~$ cd ~/Desktop/redsn0w-linux_0.8
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ~/Desktop/redsn0w-linux_0.8$ chmod a+x redsn0w
bash: /home/coffeegulpers/Desktop/redsn0w-linux_0.8$: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ chmod a+x redsn0w
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$  ./redsn0w
./redsn0w: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ 
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ 

```

**what in the buttered popcorn?! :popcorn:**

---

### Post by 4042966262 on 2012-03-04
**Attempt 5**
```
coffeegulpers@coffeegulpers:~$ cd ~/Desktop/redsn0w-linux_0.8
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ chmod a+x redsn0w
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./redsn0w
./redsn0w: error while loading shared libraries:  libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such  file or directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ ./ redsn0w
bash: ./: Is a directory
coffeegulpers@coffeegulpers:~/Desktop/redsn0w-linux_0.8$ 

```
**GRRRR... how do i run it?**

---

