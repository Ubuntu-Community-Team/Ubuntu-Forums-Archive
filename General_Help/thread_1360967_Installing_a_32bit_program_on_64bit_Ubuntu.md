---
title: "Installing a 32bit program on 64bit Ubuntu"
date: 2009-12-21
forum: General Help
---

### Post by running_rabbit07 on 2009-12-21
I am trying to install Packet Tracer on my system, but it is a 32 bit program. How do I get this to install without using VBox?

Thanks

---

### Post by oldos2er on 2009-12-21
```
sudo dpkg -i --force-architecture <package name>
```

---

### Post by prem1er on 2009-12-21
Very sweet. I didn't know this existed. Thanks.

---

### Post by LuisGMarine on 2009-12-21
If this worked please don't forget to mark the thread as [SOLVED]!

---

### Post by running_rabbit07 on 2009-12-21
> **oldos2er said:**
> ```
sudo dpkg -i --force-architecture <package name>
```
Thanks. I tried it and this was the output. Any advice? Thanks for helping. ```
rabbit@rabbit-desktop:~$ sudo dpkg -i --force-architecture PacketTracer521_i386_no_tutorials_installer-deb.bin
[sudo] password for rabbit: 
dpkg-deb: `PacketTracer521_i386_no_tutorials_installer-deb.bin' is not a debian format archive
dpkg: error processing PacketTracer521_i386_no_tutorials_installer-deb.bin (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 PacketTracer521_i386_no_tutorials_installer-deb.bin
rabbit@rabbit-desktop:~$ 

```

---

### Post by howefield on 2009-12-21
> **running_rabbit07 said:**
> dpkg-deb: `PacketTracer521_i386_no_tutorials_installer-deb.bin' is not a debian format archive

The error is telling you what the prob is, it isn't a .deb file, is it ?

Looks like a .bin file.

---

### Post by running_rabbit07 on 2009-12-21
> **howefield said:**
> The error is telling you what the prob is, it isn't a .deb file, is it ?

Looks like a .bin file.

That's correct. I am asking for a way to get the program installed, if there is a way. 

I am trying to not have to boot a VBox every time I want to study.

---

### Post by stlsaint on 2009-12-21
> **running_rabbit07 said:**
> Thanks. I tried it and this was the output. Any advice? Thanks for helping. ```
rabbit@rabbit-desktop:~$ sudo dpkg -i --force-architecture PacketTracer521_i386_no_tutorials_installer-deb.bin
[sudo] password for rabbit: 
dpkg-deb: `PacketTracer521_i386_no_tutorials_installer-deb.bin' is not a debian format archive
dpkg: error processing PacketTracer521_i386_no_tutorials_installer-deb.bin (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 PacketTracer521_i386_no_tutorials_installer-deb.bin
rabbit@rabbit-desktop:~$ 

```



dpkg (as far as my knowlegde goes) is for .deb packages...whats the format of this Packet app your trying to use?

---

### Post by running_rabbit07 on 2009-12-21
> **stlsaint said:**
> dpkg (as far as my knowlegde goes) is for .deb packages...whats the format of this Packet app your trying to use?

.bin

---

### Post by prem1er on 2009-12-21
If it is a bin file you are trying to install (which is what it looks like to me). All you need to do is in the terminal migrate to the correct directory. Run 

```
chmod +x <filename>
```

then...

```
./<filename>
```

The thread was confusing because of the original post did not specify the file format and everyone assumed it was a .deb package.

---

### Post by running_rabbit07 on 2009-12-21
> **prem1er said:**
> If it is a bin file you are trying to install (which is what it looks like to me). All you need to do is in the terminal migrate to the correct directory. Run 

```
chmod +x <filename>
```then...

```
./<filename>
```

Doesn't work for install 32 bit program on 64 bit OS.

---

### Post by prem1er on 2009-12-21
> **running_rabbit07 said:**
> Doesn't work for install 32 bit program on 64 bit OS.

I'm sorry I completely forgot that was the original question :confused:. I hope someone has the answer for you!

---

### Post by running_rabbit07 on 2009-12-21
> **prem1er said:**
> I'm sorry I completely forgot that was the original question :confused:. I hope someone has the answer for you!

No problem. I hope so too.

---

### Post by bodhi.zazen on 2009-12-21
> **running_rabbit07 said:**
> Doesn't work for install 32 bit program on 64 bit OS.


What is the error message ? You might be able to install it by first installing the 32 bit lib and than any 32 bit dependencies.

But just telling us that it fails does not provide us with much to work with.

---

### Post by running_rabbit07 on 2009-12-21
> **bodhi.zazen said:**
> What is the error message ? You might be able to install it by first installing the 32 bit lib and than any 32 bit dependencies.

How do I do that? Thanks.

> **bodhi.zazen said:**
> But just telling us that it fails does not provide us with much to work with.

This is what I get when using the chmod +x and ./ ```
Attempting to install package now
dpkg: error processing PacketTracer-5.2.1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 PacketTracer-5.2.1.i386.deb
rabbit@rabbit-desktop:~$ 

```Thanks again for any help.

---

### Post by running_rabbit07 on 2009-12-21
```
root@rabbit-desktop:/home/rabbit# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@rabbit-desktop:/home/rabbit# chmod +x PacketTracer521_i386-deb.bin
root@rabbit-desktop:/home/rabbit# ./PacketTracer521_i386-deb.bin
Self extracting archive...
Do you accept the terms of this EULA? (Y)es/(N)o
y
You have accepted the terms to the EULA. Cisco Packet Tracer will now be installed.
Attempting to install package now
dpkg: error processing PacketTracer-5.2.1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 PacketTracer-5.2.1.i386.deb
root@rabbit-desktop:/home/rabbit# 

```

---

### Post by oldos2er on 2009-12-21
If you got this file from Cisco, I'd ask them how to install, or see if they have an actual .deb file you can use.

---

### Post by running_rabbit07 on 2009-12-21
> **oldos2er said:**
> If you got this file from Cisco, I'd ask them how to install, or see if they have an actual .deb file you can use.

I am waiting on them to return my email. The program installs easily on Ubuntu 32 bit with the .bin file. A DEB would be much nicer. I am a bit jealous that it installed without any problems on 64bit Windows 7 even though the exe version is also 32 bit. I think having a deb file for this would make installing much easier.

---

### Post by oldos2er on 2009-12-21
It's a long shot, but have you tried opening it with file-roller (Archive Manager)? If it's a deb file wrapped in a bin file, perhaps you can extract the deb.

---

### Post by running_rabbit07 on 2009-12-21
Solved. Installed Windows 7 for dual boot. Thanks everyone for the help.

---

### Post by steveneddy on 2009-12-21
> **running_rabbit07 said:**
> Solved. Installed Windows 7 for dual boot. Thanks everyone for the help.

I would think that you would prefer VirtualBox using the Seamless mode instead of a dual boot.

I think I use to use Packet Tracer in Wine when I took some networking classes.

This person solved the same issue:

[http://ubuntuforums.org/showthread.php?t=1292620](http://ubuntuforums.org/showthread.php?t=1292620)

Here's more about 32 on 64 bit stuff:

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by MaxIBoy on 2009-12-21
> **running_rabbit07 said:**
> ```
root@rabbit-desktop:/home/rabbit# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@rabbit-desktop:/home/rabbit# chmod +x PacketTracer521_i386-deb.bin
root@rabbit-desktop:/home/rabbit# ./PacketTracer521_i386-deb.bin
Self extracting archive...
Do you accept the terms of this EULA? (Y)es/(N)o
y
You have accepted the terms to the EULA. Cisco Packet Tracer will now be installed.
Attempting to install package now
dpkg: error processing PacketTracer-5.2.1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 PacketTracer-5.2.1.i386.deb
root@rabbit-desktop:/home/rabbit# 

```
Looks like its a self-extracting archive which contains a Debian package. See if there's any way to get the package from the binary. Maybe look in /tmp to see if it's being stored there. Then, use the dpkg command suggested earlier. 

Also, long shot, but try opening it with file-roller (AKA archive-manager.)

EDIT: Suppose it doesn't leave any deb files behind after you run it. If you want to be a 1337 h4x0r, you can run the binary with a debugger like GDB or DDD, install the debugging symbols for libc, and try setting it to break when it hits any call to [unlink](http://www.gnu.org/s/libc/manual/html_node/Deleting-Files.html), thus pausing it just before it deletes the file. If you don't know what any of that means, forget about it.

---

