---
title: "Is there an inbuilt log?"
date: 2011-02-23
forum: General Help
---

### Post by jezzyjez on 2011-02-23
I was wondering whether there is an inbuilt logging system in UNIX?

I ran and installation and the program opened up automatically but I can't find the program executable.

If I could find a log then I could locate this file.

Thanks in advance Jez

---

### Post by Frogs Hair on 2011-02-23
I'm not sure what you me by " in Unix" , but Ubuntu log file viewer  can be found in System > Administration > Log file Viewer.

---

### Post by wiggly81 on 2011-02-23
look in /usr/bin/ its where i find most things i install.

---

### Post by jezzyjez on 2011-02-23
Ok well the application doesn't appear in usr as I installed it directly to my home folder. (no reason why just seemed easiest)

And i've looked through the logs and can't find an instance of opening an executable file.

I may reinstall it to the usr directory, would that make sense. If so which folder specifically should I choose as the root.

I know that these may be different depending on setup, but what is 'the norm' basically the equivalent of 'program files' in windows

---

### Post by trivialpackets on 2011-02-23
You could search for it, from the command line...

```
find path -name executablename
```

So to find all instances of say lzma in the /usr directory, I would enter this:

```
find /usr -name lzma
```

---

### Post by Wtower on 2011-02-23
> **jezzyjez said:**
> Ok well the application doesn't appear in usr as I installed it directly to my home folder. (no reason why just seemed easiest)

And i've looked through the logs and can't find an instance of opening an executable file.

I may reinstall it to the usr directory, would that make sense. If so which folder specifically should I choose as the root.

I know that these may be different depending on setup, but what is 'the norm' basically the equivalent of 'program files' in windows

This may be helpful:

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by mcduck on 2011-02-23
> **jezzyjez said:**
> Ok well the application doesn't appear in usr as I installed it directly to my home folder. (no reason why just seemed easiest)

And i've looked through the logs and can't find an instance of opening an executable file.

I may reinstall it to the usr directory, would that make sense. If so which folder specifically should I choose as the root.

I know that these may be different depending on setup, but what is 'the norm' basically the equivalent of 'program files' in windows

There is no equivalent of "Program Files"-directory. Applications installed through the package management are installed by placing each separate place in different place, depending on the file's purpose. The main executable file will usually be in /usr/bin, setting files in /etc, icons and images in /usr/share/icons & /us&share/pixmaps, socumentation in  /usr/share/doc and so on.

When you install something outside of the package management, the normal places to install to would either be your own home directory (if installing for the current user only), or inside /opt (if you want to install the program for every user of the system).

---

### Post by jezzyjez on 2011-02-23
Ok Wtower thanks for the link spells a few things out.


> here is no equivalent of "Program Files"-directory. Applications installed through the package management are installed by placing each separate place in different place, depending on the file's purpose. The main executable file will usually be in /usr/bin, setting files in /etc, icons and images in /usr/share/icons & /us&share/pixmaps, socumentation in /usr/share/doc and so on.

When you install something outside of the package management, the normal places to install to would either be your own home directory (if installing for the current user only), or inside /opt (if you want to install the program for every user of the system).

Ok so I have installed the program in my user dir as its just for myself and is not a supported package. But I still cant find the executable amongst the 5 Gig of program files. The program started correctly once at the end of installation but I dont know the name or file type of the executable???

Is there an easy way to find this (searching for common file extensions in program files maybe?)

Jez

---

### Post by mcduck on 2011-02-23
I don't know what is this "Program Files" where you are searching your program executable from.... Like I said there's no such thing on Linux. :D

If the program was installed into your home directory, you'll also find it's executable somewhere in your home directory. Where, that depends on how exactly you installed the program, and if it had a installer script where that script happens to put the executable file.

The best approach would simply be checking whatever documentation that came with the program. That should tell you not only the name of the executable, but also where to find it and how to run it...

---

### Post by jezzyjez on 2011-02-23
> I don't know what is this "Program Files" where you are searching your program executable from.... Like I said there's no such thing on Linux. 

sorry in that instance I meant the folder I installed the program into.

I'll have a trawl through the documentation and see whether I can pick anything up

---

### Post by trivialpackets on 2011-02-23
Usually, if you can't see it, I would try looking in ~ and do an ls -a to see if maybe it's in a hidden folder?  Not sure really.  What is the application?

---

