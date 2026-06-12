---
title: "What distro would best fit me?"
date: 2010-01-19
forum: General Help
---

### Post by Serpher on 2010-01-19
Hello,

I've been using Linux for about a good year and a half now and I've pretty much just been using Ubuntu dabbling in another couple distro's like Fedora and OpenSuSe. I'm currently in school for IT (Computer Systems Technology) and I'm looking for a distro I can use at home for personal computing. I want something I can learn a lot with and something that would be more geared towards making LAMP servers and that kind of deal. I really just kinda want a "more hardcore distro" while not wanting to kill myself to get simple tasks done. I'm kinda leaning towards Fedora but I would appreciate input. Thanks!

---

### Post by x33a on 2010-01-20
you can  try ubuntu-minimal, arch, sidux, slackware, etc. apart from fedora of course.

---

### Post by Malakai on 2010-01-20
You can learn about Linux from any distro, you just need to tinker with the OS, learn about the directory structure, permissions, ect. I suggest buying a book about linux from a store, that teaches the basics of linux that I mention above. Learn how to compile a kernel, mount filesystems, there are hundress of little things to do on the CLI that will serve you well no matter what distro you use, and the best way to learn them IMO is starting with a good book on the basics, and from there just playing with a linux install.

To realy learn about the ins and outs of a linux system tho, I strongly suggest giving gentoo a shot. You will end up learning the CLI a lot out of neccessity and thus will learn where all kinds of config files are, how to edit them, where different types of files are located in the filesystem, ect. It took a book (linux for beginners or something) and using gentoo for a few years as a secondary OS, but now I am very comfortable in nearly any distro and most importantly can fix most linux problems from the command line, which is a big step. You will often find, once you pass a certain level of knowledge, that the CLI is simpler and faster than trudging through some GUI tools. I rarely run a file manager but use the cli, same goes for mounting filesystems, editing startup services & such, once you know how to use it you can do everything from one terminal vs switching between 10 different gui programs.

And people who do not know the cmd line will look at you and believe you possess some kind of "hackers" otherworldly computer knowledge which is also cool =)

---

### Post by amsterdamharu on 2010-01-20
Think ubuntu 8.04 is good, it's the long term release and is pretty stable. Most packages work when installed without tweaking them. Anything newer (allthough in the release) might need more work to get going.

Installing Lamp:
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)


For php debugging you can use phpeclipse
[http://www.ibm.com/developerworks/library/os-debug/#N101F3](http://www.ibm.com/developerworks/library/os-debug/#N101F3)

---

### Post by Serpher on 2010-01-24
I think I'm going to give Gentoo a shot. I already know how to mount file systems and where things are for run levels and stuff like that but I've come to the conclusion I basically want the most bare bones Linux I can find and then customize it exactly how I want it.

---

### Post by falconindy on 2010-01-24
Gentoo will leave you in pain if you don't have a fast rig (and even then its questionable), as you need to compile **everything**. Compiling a full DE such as Gnome is something you want to do overnight. If your interest is in learning, I suggest you look elsewhere to start. To paraphrase someone smarter than me, "watching text scroll by for hours does not make you an expert".

A distro such as Arch or Slackware still gives you nearly limitless freedom in terms of customization, and you still have the ability to recompile packages easily to make whatever changes you're interested in. It also brings you down to the roots of Linux and forces you to learn what each component does, while maintaining some level of sanity.

---

### Post by danastasio on 2010-01-24
I suggest Arch Linux, very difficult to install, you will need to print out a copy of the beginners guide, however, you will learn an incredible ammount about linux that you didnt even know existed by the time you finish configuring everything. You dont have to compile very much like in Gentoo, but EVERYTHING that can possibly be left to the user, is left to the user.

---

### Post by x33a on 2010-01-24
> **danastasio said:**
> you will need to print out a copy of the beginners guide

I wrote it down :D (don't have a printer).

---

### Post by andrew.46 on 2010-01-25
Hi Serpher,

> **Serpher said:**
>  I really just kinda want a "more hardcore distro" while not wanting to kill myself to get simple tasks done.

It sounds like you are describing Slackware. If you can hold off for Slackware 13.1 (when the kde issue is finally put to rest) you will find a distro that enables you to learn while at the same time still enabling things to be done with a minimum amount of fuss. I attach a gratuitous screenshot of Slackware 13.0 running xfce :).

All the best,

Andrew

---

### Post by Serpher on 2010-01-25
Would it be advisable to run GNOME on Slackware? I understand certain distributions run different desktop environments differently such as how Kubuntu is optimized to run KDE, or is it just the default installed desktop manager?

EDIT: I looked on their website and it states it's inadvisable to use GNOME so I guess I'll just get used to KDE4. I'll give this a try over the weekend. Thanks everybody.

---

### Post by andrew.46 on 2010-01-26
Hi Serpher,

> **Serpher said:**
> Would it be advisable to run GNOME on Slackware?

As you have no doubt seen from the slackware website Slackware does not actually ship with gnome any more and by default will give you a choice of kde, xfce, fluxbox, blackbox and a couple of others. Gnome is available from a couple of third party sites which I confess I have not tried, being an xfce man from way back :).

Andrew

---

