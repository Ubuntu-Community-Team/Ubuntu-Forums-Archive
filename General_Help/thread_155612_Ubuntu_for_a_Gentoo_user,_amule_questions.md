---
title: "Ubuntu for a Gentoo user, amule questions"
date: 2006-04-05
forum: General Help
---

### Post by peibol on 2006-04-05
I'm a gentoo user so I'm used to compile everything using the portage system, I've to admit that I really like it because I can customize the software I install.

Here is the question:
how do a Ubuntu user would do to install amule enabling the daemon mode and the web remote control, both features I have running in my gentoo box right now.

To get this in gentoo I had to put the following line in my /etc/portage/package.use file

net-p2p/amule amuled remote stats

This ensures that amule will be compiled including the remote mode, the daemon process and the stats feature, after compile ("emerge amule") I added it to default level services ("rc-update add amuled default"), so I don't need to login to have it started. 

How would an ubuntu user do get the same behavior?

I would like to give ubuntu a try, but I will like to discuss some of the distro diferences before (so I will know where I'm heading), and above all, I don't intend to get a flame war on this distro is better than that, I just want to know easily what are the differences and how to get the same on both.

Another questions:
what are the needed steps to compile the kernel in ubuntu?
Does ubuntu includes gcc compiler as a default?

Regards.

---

### Post by lupine_nickt on 2006-04-05
IIRC, gcc is included on the Ubuntu CD, but not installed by default. Breezy uses gcc-3.4 for the kernel, and gcc-4.0 for everything else (which has caused me a few headaches in the past, lol)... whereas Dapper just uses gcc-4.

Regarding aMule, you'd just install the amule-daemon package as well as the main amule package; then symlink it to the appropriate directory to get it to run on startup. Stats & remote capabilities come included by default, I think.

Installing a custom kernel isn't something I've tried yet in Ubuntu... but I gather that there's a semi-automated process, using the "kernel-package", erm, package. I quote:-

> 
A utility for building Linux kernel related Debian packages.
This package provides the capability to create a debian kernel-image package by just running make-kpkg kernel_image in a kernel source directory tree. It can also package the relevant kernel headers into a kernel-headers package. In general, this package is very useful if you need to create a custom kernel, if, for example, the default kernel does not support some of your hardware, or you wish a leaner, meaner kernel. It also scripts the steps that need be taken to compile the kernel, which is quite convenient (forgetting a crucial step once was the initial motivation for this package). Please look at /usr/share/doc/kernel-package/Rationale.gz for a full list of advantages of this package.



Funnily, I've been considering installing Gentoo on a spare server I've got lying around, to have a play... as I fin dthe idea of a source-based distro quite interesting... *shrug* ;)

xF,

...Nick

---

### Post by peibol on 2006-04-05
Thanks for your reply.

If you plan to install a source based distro, I'll just recomend gentoo, has plenty support, very friendly comunity and a lot of soft to play around. It's not easy at a start, but once you get used to it it's pretty easy to use. And gotta say that all I get to learn about linux I learned it with gentoo (you will learn or die)

Good tip on the amule-remote package, some time ago i've tryed ubuntu and that is something that wasn't there (a year ago or so).

About the kernel, well... i'm pretty used to compile it by hand (make gconfig, make, and then copy the image myself, etc, etc) and i just like that way so I know what's in it, another issue is that I have an ipw2200 and the default kernel code has some uncompatible code that has to be replaced to compile right...

I think i'm gonna split home partition to install a ubuntu just to try it out, where can I get the latest testing version? Dapper Drake is it?. 

Regards.

---

