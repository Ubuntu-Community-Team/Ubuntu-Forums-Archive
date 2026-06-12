---
title: "How to determine which Linux distro is running"
date: 2009-10-08
forum: General Help
---

### Post by ghormley on 2009-10-08
If one wants to know the particular distro that is running on this PC, what is the command to determine that?  Isn't there a CLI command for this?

Also, if asking such a question here is inappropriate, how should a noob find this information?

---

### Post by philinux on 2009-10-08
System>admin>system monitor> System tab

or

```
lsb_release -a
```

---

### Post by alphaniner on 2009-10-08
Ubuntu has a file /etc/issue.net, but I dunno about other distros.

---

### Post by ghormley on 2009-10-08
Someone can probalby answer this directly, but I'm looking to learn how to do it in the future.  I've just setup SmoothWall on a PC and want to find out what distro it runs on.  I tried the lsb_release -a command from the CLI but it does not recognize that command when running at root.  Returns "-bash: lsb_release command not found".  Is there another way to determine the particular distro from the command line?

---

### Post by Dougie187 on 2009-10-08
lsb_release is only for ubuntu if I remember correctly.

I think you best bet is to poke around in the system tab for something like "About Ubuntu" or "About Distro"

Also though, you could (in a terminal) type
```
dmesg | grep "Linux version" -i
```

That might give you the distro in it.

---

### Post by wojox on 2009-10-08
Try:

```
uname -a
```

---

### Post by Dougie187 on 2009-10-08
> **wojox said:**
> Try:

```
uname -a
```

This only works on some distros. For example,

In ubuntu it gives
```
uname -a
Linux doug-lt 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux
```

In centos it gives
```
uname -a
Linux dskscs057 2.6.18-128.1.16.el5 #1 SMP Tue Jun 30 06:10:28 EDT 2009 i686 i686 i386 GNU/Linux

```

It only gives the distro name if the distro name is included in the kernel version.

EDIT: /etc/issue.net is there in both ubuntu and centos, and thus RHEL, but I am not sure if it's there in everything else.

---

### Post by drs305 on 2009-10-08
And for non-CLI, there is always System, Administration, System Monitor: System tab. It tells you Release (9.10 Karmic, etc), Kernel (2.6.31-12, etc), Memory, Processor(s) and disk space remaining.


Edit: See philinux had this as the second part of his post.

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Dougie187 on 2009-10-08
> **drs305 said:**
> And for non-CLI, there is always System, Administration, System Monitor: System tab. It tells you Release (9.10 Karmic, etc), Kernel (2.6.31-12, etc), Memory, Processor(s) and disk space remaining.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

But this would be different if it was a different distro, even if it wasn't GDM. I would assume by the question that the computer in question isn't obviously running ubuntu.

---

### Post by drs305 on 2009-10-08
> **Dougie187 said:**
> But this would be different if it was a different distro, even if it wasn't GDM. I would assume by the question that the computer in question isn't obviously running ubuntu.

Since this is a relatively basic question by a self-described 'noob' (which is fine), I don't necessarily assume the terminology is precise. New users often mix terms, so I didn't key on "distro".

For the record:
Distribution: Ubuntu
Release: 9.10
Codename: Karmic

---

### Post by ghormley on 2009-10-08
This PC in NOT running Ubuntu.  I run Ubuntu on my desktop, but wanted to add a Trendnet ethernet nic driver to the SmoothWall PC.  That driver only exists in an RPM format, so my first question is what distro is SmoothWall running on?  Thus the need to determine the distro.  Due to the failure of the above suggestions to determine the distro and NOT having a GUI to work with on the SmoothWall PC, I'm limited to CLI.

---

### Post by Dougie187 on 2009-10-08
what did the dmesg command give you? I don't know if it would have any useful information in it or not, but it has on the two computers I tested it on.

---

### Post by sedawk on 2009-10-08
The primitive solution I use is 
```

cat /etc/*elease*

```

This works as long as nobody else things it is a good idea
to drop other "release" files there.
The filename itself tells you the distro and the
content of the file the version.

If there is a better solution tell me too !-)
(No, "uname -a" doesn't work!)

---

### Post by wojox on 2009-10-08
My bad. I thought uname was compatible across the all *nix's. Sorry OP :P
I tried sedhawks and that works good. Have to remember that.

---

### Post by ghormley on 2009-10-08
**dmesg | grep "Linux version" -i**  gives this response:

[INDENT]Linux version 2.6.16.60 (root@build) (gcc version 3.3.5) #1 Wed Jan 7 07:00:21 GMT 2009[/INDENT]

Obviously I have not set the date or connected the PC to the Internet.

**uname -a** gives this response:
[INDENT]
Linux jcghouse 2.6.16.60 #1 Wed Jan 7 07:00:21 GMT 2009 i686 GNU/Linux[/INDENT]

**cat /etc/*elease***  gives this response:

[INDENT]cat: /etc/*elease*: No such file or directory[/INDENT]

It seems strange that there is no command in the kernal that will identify the distro or a file written by the distributor that identifies their software.

---

### Post by ghormley on 2009-10-08
I visually checked the /etc directory and no file that matches *elease* exists in that directory.

---

### Post by wojox on 2009-10-08
One more:

```
cat /proc/version
```

---

### Post by dchriscoe on 2009-10-08
How about typing in the terminal "cat /etc/lsb-release".

---

### Post by ghormley on 2009-10-08
**cat /proc/version**  gives this response:

[INDENT]Linux version 2.6.16.60 (root@build) (gcc version 3.3.5) #1 Wed Jan 7 07:00:21 GMT 2009[/INDENT]

---

### Post by Dougie187 on 2009-10-08
> **ghormley said:**
> It seems strange that there is no command in the kernal that will identify the distro or a file written by the distributor that identifies their software.

There typically is. But it varies by the making of the distro. Just by looking at smoothwall's site it appears to be a homemade 'distro' if you could even really call it that. For the most part I think it's just the kernel.

---

### Post by ghormley on 2009-10-08
**cat /etc/lsb-release**  gives this response:

[INDENT]cat: /etc/lsb-release: No such file or directory[/INDENT]

There is no match for a file that begins with lsb in the /etc directory

---

### Post by ghormley on 2009-10-08
I thought this would be a slam dunk for seasoned Linux users and it's a bit heartening to learn it stumps the best for whatever reasons.

However, given the fact that it may not be a recognized distro, I suppose I should give up the idea of using the Trendnet TE100-PCIWA nic and find one that is recognized by the kernel without having to load a driver.

I definitely appreciate all the help, guys. (May be a bad assumption that you are all male.  Sorry, if so.)

---

### Post by philinux on 2009-10-08
Try this

```
cat /etc/issue

or

cat /etc/version
```

it's lsb_ I always forget that.

---

### Post by ghormley on 2009-10-08
There are no files in the /etc directory that match either, lsb_*, or issue, or version.

---

### Post by wojox on 2009-10-08
From the site:

> What is the SmoothWall Open Source Project?
The SmoothWall Open Source Project was set up to develop and maintain SmoothWall Express - a free firewall that includes its own security-hardened GNU/Linux operating system and an easy-to-use web interface.

---

