---
title: "Creating a Linux Distro"
date: 2010-06-08
forum: General Help
---

### Post by Auzern on 2010-06-08
I have been using Linux OS since 4 years and I'm very interested to know how to create a Linux Distro. I have heard about LFS.
I would just like to know, what do I need to create a Linux Distro?
I'm not a programmer, if I have to create a Linux Distro, what programming languages do I need to know.
And also, how many people are required and how much time will it take to create a Linux Distro? Or Something like Ubuntu..

Thanks in Advance.

---

### Post by Sporkman on 2010-06-08
Build a working system from LFS first.

---

### Post by Auzern on 2010-06-08
> **Sporkman said:**
> Build a working system from LFS first.

Thank you for the reply. Do I need to know any programming language for that?

---

### Post by philinux on 2010-06-08
> **Auzern said:**
> I have been using Linux OS since 4 years and I'm very interested to know how to create a Linux Distro. I have heard about LFS.
I would just like to know, what do I need to create a Linux Distro?
I'm not a programmer, if I have to create a Linux Distro, what programming languages do I need to know.
And also, how many people are required and how much time will it take to create a Linux Distro? Or Something like Ubuntu..

Thanks in Advance.

Or could start with ubuntu minimal.

Moved to General Help.

---

### Post by kaldor on 2010-06-08
However long you're willing to put into it ;)

All about persistence. Linux distros are mainly just adding the right packages in the right places.

---

### Post by _khAttAm_ on 2010-06-08
> **Auzern said:**
> I have been using Linux OS since 4 years and I'm very interested to know how to create a Linux Distro. I have heard about LFS.
I would just like to know, what do I need to create a Linux Distro?
I'm not a programmer, if I have to create a Linux Distro, what programming languages do I need to know.
And also, how many people are required and how much time will it take to create a Linux Distro? Or Something like Ubuntu..

Thanks in Advance.

The base you would like to select depends upon what your linux distro will try to achieve.. LFS may not always be suitable for start...

Please share what kind of users you'd like to target it for...

---

### Post by Sporkman on 2010-06-08
> **Auzern said:**
> Thank you for the reply. Do I need to know any programming language for that?

No, but you do need to be familiar with using command-line tools & basic BASH-scripting.

---

### Post by Auzern on 2010-06-08
I thank you all very much for your replies! :)

> **_khAttAm_ said:**
> The base you would like to select depends upon what your linux distro will try to achieve.. LFS may not always be suitable for start...

Please share what kind of users you'd like to target it for...
Thank you, khAttAm.
The type of users I'm targeting are productive users. The ones who are more into work rather than just socializing and wasting time on the internet.

> **Sporkman said:**
> No, but you do need to be familiar with using command-line tools & basic BASH-scripting.

Alright so I just need to know command-line tools & BASH-scripting is it!? Well I will start learning them right away. Thank you Sporkman.

---

### Post by unmole on 2010-06-08
> **sporkman said:**
> build a working system from lfs first.
+1

---

### Post by Sporkman on 2010-06-08
> **Auzern said:**
> The type of users I'm targeting are productive users. The ones who are more into work rather than just socializing and wasting time on the internet.

You don't need to create a new distro for that - there are existing distros that are stable and "boring" - good for getting things done. Though internet connectivity is still necessary, as a lot of things need to be "googled" during the course of various types of work.

---

### Post by snowpine on 2010-06-08
"Creating your own customized Linux install for personal use" is easy using LFS, Ubuntu Minimal, Arch, etc.

"Creating your own Linux distro to share with the world" is mostly about marketing. You need to build community and convince your potential users that you know what you're doing and that your distro is superior to the other options available. Many wonderful distros have failed to achieve popularity, while "Debian with a brown wallpaper" became the #1 most popular distro due to incredible marketing efforts and being in the right place at the right time.

If you haven't already, check out distrowatch.com to see what else is out there. Working on an existing project will give you good experience for someday leading your own project. Good luck!

---

### Post by Auzern on 2010-06-08
Thanks to all of you again.

**snowpine**, +rep for you reply!! Thanks a lot!
I will help in the projects first and also learn about LFS.
Thanks again. :)

---

### Post by spiky001 on 2010-06-08
have you had a look at suse studio? it might not be what you are looking for, but just a thought

---

### Post by Auzern on 2010-06-08
> **spiky001 said:**
> have you had a look at suse studio? it might not be what you are looking for, but just a thought

Oh yes, I heard about that many days ago. Looks very simple and easy but I want to make something professional ;)

---

### Post by MCVenom on 2010-06-08
> **Auzern said:**
> Oh yes, I heard about that many days ago. Looks very simple and easy but I want to make something professional ;)
What about just OpenSUSE? Or CentOS? or Debian Lenny? They're nice and productive OSes.

The point is, there's already plenty of distros; what will make your distro different? What kind of professional are you talking about? And do you need to make a distro *from scratch*? Your distribution will need a package manager. Are you going to use repos straight from other distros (Like Mint uses Ubuntu repos) or base them off another distro's repos (Like Ubuntu bases its repos on Debian's, or Trisquel bases its on Ubuntu's, but without proprietary or binary only software) or assemble your own (that will mean **a lot** of work)? You might find it much easier and probably come up with a much more easily polished distro if you base it on an existing distro, like Fedora, Debian, Ubuntu, or OpenSUSE.

PS: Yes, before you plan to make your own distro, however you plan to do it, you should do the LFS thing; it will teach you a lot about Linux and how a distribution is put together.

---

### Post by Cypher2 on 2010-06-08
Personally, I just install Ubuntu and run a custom modification script after its done to purge whatever I do not need, install the necessary applications and modules/plugins missing and even set environment preferences via gconftool2...

I've also tried "building" my own distro.. but it takes way too long to achieve a stable result...

Another option would be to use the reconstructor online database and build your project through the downloadable engine.

---

### Post by Tlem on 2010-06-08
If I was looking for a distro that fit that bill.  I would look no further than Debian Stable.

---

### Post by Auzern on 2010-06-09
Thanks again for all you help.

Right now I'm going to work with a development team of an upcoming distro and then plan on making a unique distro with LFS ;)

---

