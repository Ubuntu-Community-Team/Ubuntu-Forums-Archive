---
title: "Kernel Panic?! O_O HALP"
date: 2011-03-21
forum: General Help
---

### Post by khoraski on 2011-03-21
HELP. I found a SUPER old Windows ME, and I had to pull out a super old monitor in order to even use it. I finally got it on, and I decided to replace the OS with Ubuntu so it would be a lot better. 

I put in the CD (Ubuntu 10.04 LTS 32bit) and it brought me to that purple screen. But then all of the sudden it turned black and displayed this message:

```
kernel panic - not syncing: Out of memory and no killable processes...
```

Someone, please tell me what to do. I had to go through SO much to convince my dad to let me keep this computer. I thought I was going to put Ubuntu on it and make it better. But now, I can't. D:

Any help?

---

### Post by WorMzy on 2011-03-21
How much RAM does the machine have? At least 1GB is recommended for Ubuntu Desktop Edition.

If your machine doesn't have that, consider trying a lighter version, like Xubuntu (Recommended 256MB RAM), or Lubuntu (Doesn't have an official RAM requirement, but is probably less than Xubuntu)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by khoraski on 2011-03-21
> **WorMzy said:**
> How much RAM does the machine have? At least 1GB is recommended for Ubuntu Desktop Edition.

If your machine doesn't have that, consider trying a lighter version, like Xubuntu (Recommended 256MB RAM), or Lubuntu (Doesn't have an official RAM requirement, but is probably less than Xubuntu)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I have 63 MB of RAM...

I did see a tutorial for installing Ubuntu on computers with less than 64 MB of memory, but I DO NOT understand it at all. I also do not have internet. 

PLEASE HELP.

---

### Post by walt.smith1960 on 2011-03-21
It may be difficult to find more RAM for a machine that old.  If it's a brand name machine like Compaq or Gateway you might look at Crucial's web site.  You can select your machine and the site will tell you what kind and how much RAM it takes. If that doesn't work I wonder if memtest x86 would tell you how much RAM is installed? I installed Ubuntu desktop on a Thinkpad with 256 Mb. and it worked for web surfing and the like. I was able to find another 256 Mb. on Ebay for <$10.

---

### Post by WorMzy on 2011-03-21
> **khoraski said:**
> I have 63 MB of RAM...

I did see a tutorial for installing Ubuntu on computers with less than 64 MB of memory, but I DO NOT understand it at all. I also do not have internet. 

PLEASE HELP.

Take a look at this list of minimal Linux distos: [http://wiki.laptop.org/go/Minimal_Linux_distros](http://wiki.laptop.org/go/Minimal_Linux_distros)

With such a small amount of RAM, you're going to struggle to get anything working on it.

You may be able to run older versions of PuppyLinux (newer versions need 128MB, older versions 64MB). TinyCore will run on as little as 48MB, Microcore on 36MB. Feather Linux claims to run on 24MB of RAM.

If you can download them, give these a try.

---

### Post by khoraski on 2011-03-21
> **WorMzy said:**
> Take a look at this list of minimal Linux distos: [http://wiki.laptop.org/go/Minimal_Linux_distros](http://wiki.laptop.org/go/Minimal_Linux_distros)

With such a small amount of RAM, you're going to struggle to get anything working on it.

You may be able to run older versions of PuppyLinux (newer versions need 128MB, older versions 64MB). TinyCore will run on as little as 48MB, Microcore on 36MB. Feather Linux claims to run on 24MB of RAM.

If you can download them, give these a try.

Okay. I got PuppyLinux to work. But I don't have internet for this computer so I don't know how to get OpenOffice for it.

---

### Post by WorMzy on 2011-03-21
Because of your RAM limitation, I don't think you'll be able to run OOo; on my machine the word processor takes up 35MB of RAM right away.

I think Puppy comes with Abiword for word processing and Gnumeric for spreadsheets, give those a whirl and see if they'll do what you need.

---

### Post by khoraski on 2011-03-21
> **WorMzy said:**
> Because of your RAM limitation, I don't think you'll be able to run OOo; on my machine the word processor takes up 35MB of RAM right away.

I think Puppy comes with Abiword for word processing and Gnumeric for spreadsheets, give those a whirl and see if they'll do what you need.

Oh, thanks. It's actually not too bad. I just have a lot of trouble with Puppy. Things aren't obvious. Such as I can't find out how to disable the darn widget sidebar. 

It also takes forever to register a simple command, such as right-clicking something on the desktop. I can't highlight things, and it's a lot slower than Windows ME. 

I wish it was as flexible as Ubuntu. Like. I can't really find out if it's even possible to customize the taskbar either.

---

### Post by WorMzy on 2011-03-21
Unfortunately moving from one distribution to another will always take some getting used to. As for the delay, it may because you're pushing the RAM to it's limit; like I mentioned before, the older version of Puppy lists 64MB as the minimum amount of RAM, and your system doesn't quite reach that. If it gets to be too much of an annoyance, try out one of the others I mentioned, although I don't know if they come with the applications you need or not.

---

### Post by khoraski on 2011-03-21
> **WorMzy said:**
> Unfortunately moving from one distribution to another will always take some getting used to. As for the delay, it may because you're pushing the RAM to it's limit; like I mentioned before, the older version of Puppy lists 64MB as the minimum amount of RAM, and your system doesn't quite reach that. If it gets to be too much of an annoyance, try out one of the others I mentioned, although I don't know if they come with the applications you need or not.

I think I may just keep it as a Windows ME. 
Thanks for your help, though.
I may try Feather Linux, but I probably won't install it.

---

