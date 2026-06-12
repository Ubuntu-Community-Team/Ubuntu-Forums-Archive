---
title: "Synaptic Package Manager: An error occurred"
date: 2009-09-30
forum: General Help
---

### Post by Habboblob on 2009-09-30
I have Ubuntu 9.04 JJ 32-Bit - Running off a bootable USB Persistently

I recieve this error when I start up Synaptic Package Manager and it just closes.

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Ubuntu%209.04%20%5fJaunty%20Jackalope%5f%20-%20Release%20i386%20(20090420.1)_dists_jaunty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I have also tried sudo apt-get install -f but receive this message
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Ubuntu%209.04%20%5fJaunty%20Jackalope%5f%20-%20Release%20i386%20(20090420.1)_dists_jaunty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$ 

```

Also, when I try to click on Applications > Add/Remove.. it also gives me this error
```
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

Someone please help, and also, I am running Ubuntu Persistently off a USB.

---

### Post by mac9416 on 2009-09-30
Hey, Habboblob,

Looks like that Package list file has a weird file name. Let's try emptying out the index file cache and reloading it...

```
$ sudo rm /var/lib/apt/lists/*_Packages
```

Then

```
$ sudo apt-get update
```

Then try opening Synaptic again.

Let me know how that works!
-mac

---

### Post by qianshiming on 2009-11-09
> **mac9416 said:**
> Hey, Habboblob,

Looks like that Package list file has a weird file name. Let's try emptying out the index file cache and reloading it...

```
$ sudo rm /var/lib/apt/lists/*_Packages
```Then

```
$ sudo apt-get update
```Then try opening Synaptic again.

Let me know how that works!
-mac
I have try it like you said,but it still can't synaptic!:mad:

---

### Post by mac9416 on 2009-11-09
Strike one. Now try this. If it doesn't fix things, please post the output of the commands.

```
$ sudo rm /var/lib/apt/lists/*
$ sudo apt-get update
```

Good luck!

---

### Post by habanany on 2013-04-15
:popcorn:thanks, it worked for me

---

### Post by oldos2er on 2013-04-15
Old thread closed.

---

