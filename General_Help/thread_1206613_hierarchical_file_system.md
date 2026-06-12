---
title: "hierarchical file system"
date: 2009-07-07
forum: General Help
---

### Post by munky99999 on 2009-07-07
Anyone know a way of customising the hierarchical file system. The whole bin-boot-usr-lib-var-home idea.

Perhaps being able to customise the names to something more explanatory.

then having still full compatibility with .deb installers and all the rest.

---

### Post by sshannin on 2009-07-07
You can make a bunch of directories with your desired names and then symlink back to the original ones.
ln -s -T target_path name_of_link

---

### Post by munky99999 on 2009-07-07
> **sshannin said:**
> You can make a bunch of directories with your desired names and then symlink back to the original ones.
ln -s -T target_path name_of_link

I dont really want to bloat it; literally replacing the names so say Bin is no longer named Bin.

---

### Post by starcraft.man on 2009-07-07
> **munky99999 said:**
> Anyone know a way of customising the hierarchical file system. The whole bin-boot-usr-lib-var-home idea.

Perhaps being able to customise the names to something more explanatory.

then having still full compatibility with .deb installers and all the rest.

[Link.]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

No, you can't physically modify them (i.e. change their naming). The hierarchy is a standard now part of the UNIX standard, it's the same across all *NIX compliant systems to ensure compatibility. Why would you want to rename them instead of just learning what goes in them? It's not like Windows has the Windows directory sorted much better.

As noted by han, you can use symbolic links to them and then rename the links. I don't really see how that helps much though.

---

### Post by c0mput3r_n3rD on 2009-07-07
The names ARE very descriptive as to their contents inside.  
ex:
    bin = binary files
    dev = devices
    boot = boot files
    usr = user files
    lib = library files

---

### Post by munky99999 on 2009-07-07
> Why would you want to rename them instead of just learning what goes in them? It's not like Windows has the Windows directory sorted much better.
The _freedom_ of being able to.

I'm not new to linux. Just wondering if it was possible.

I essentially dont want to change the hierarchy in where things are and what is in them. I simply want to change the name.

Also yes I do know where most things are. I occasionally have to look them up for some unusual placements; ex. the apt cache of debs.

It's all about the **freedom.**

---

### Post by michy99 on 2009-07-07
> **c0mput3r_n3rD said:**
> The names ARE very descriptive as to their contents inside.  
ex:
    bin = binary files
    dev = devices
    boot = boot files
    usr = user files
    lib = library files

4 out of 5 ain't bad. usr = unix system resources

---

### Post by wojox on 2009-07-07
munkey why must you reinvent the wheel?

---

### Post by munky99999 on 2009-07-07
> **wojox said:**
> munkey why must you reinvent the wheel?

Why shouldnt i have the freedom to change "bin" to "binaries" for example.

I just am wondering why this customisation isnt possible.

Even in a more elaborate use. The file system could build in a flag system or something which gives the logical standard. Allowing any name to be used.

---

### Post by wojox on 2009-07-07
You can have the freedom to do anything you want munky. I would suggest reading the link starcraft provided. The HFS hasn't always existed. 

They created when Linux distro's first came out little munkys wanted to name things their own way. There wasn't any structure.

---

### Post by munky99999 on 2009-07-07
> **wojox said:**
> You can have the freedom to do anything you want munky. I would suggest reading the link starcraft provided. The HFS hasn't always existed. 

They created when Linux distro's first came out little munkys wanted to name things their own way. There wasn't any structure.

The problem is that you say I have the freedom to do anything; but starcraft clearly says **No, you can't physically modify them (i.e. change their naming). **

Now I'm certainly not a massive open source only kind of person. I've used proprietary stuff. However in that light... such a basic thing doesnt seem to be open for change. Obviously you cant just simply rename the folders. So why isnt there freedom in this case?

Originally in the post... I was thinking of a sort of tool or simply a way of going into conf files and change it to make it work. With little or no expectation of a gui.

---

### Post by michy99 on 2009-07-07
It's like this. Programs expect to find things in certain directories. If you go changing the names of those directories, you will have to somehow tell every single program that uses something in any of those directories that the paths have changed. In other words, you would have to change almost every program on your system.

---

### Post by sisco311 on 2009-07-07
> **munky99999 said:**
> So why isnt there freedom in this case?


You can recompile all the applications with the new paths. :)

Also you can rewrite the ls, cp ... commands to display the names of directories as you want. 

You can rewrite your file manager as well. 

You can use symbolic links ...


The implementation is not easy, but you are free to do it.

---

### Post by lukeiamyourfather on 2009-07-07
Its certainly possible and nobody is taking that freedom away from you, just saying its probably not worth the effort. The easiest way would be to use symbolic links like already mentioned. If you don't like that then you can edit the source and recompile virtually everything on the system to make it happen. That's the beauty of it all.

Why do you really care though? That's like someone wanting to rename the Windows folder. It doesn't matter, it could be called purplemonkeydishwasher and it would still work. Personally I kind of like of like the directory structure of Linux. I'm glad there's no folders on the root of the drive called "Whatever Recent Game 1.22.7" or "Program Files (x86)", that **** doesn't help anyone. Cheers!

---

### Post by sisco311 on 2009-07-07
If you don't like the "traditional" Filesystem Hierarchy then maybe you will like [GoboLinux]("http://www.gobolinux.org/").

---

