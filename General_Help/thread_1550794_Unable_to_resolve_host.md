---
title: "Unable to resolve host"
date: 2010-08-11
forum: General Help
---

### Post by RedSingularity on 2010-08-11
Hey everyone, i am having a problem in the terminal window.  When i try to do various operations i get the following message before the operation starts.

sudo: unable to resolve host Tims-Laptop

Any ideas as to a cure?

---

### Post by Brandon Williams on 2010-08-11
If your /etc/hostname file contains the name 'Tims-Laptop', then there should be an entry for Tims-Laptop in your /etc/hosts file, too, as in:
```
127.0.1.1 Tims-Laptop
```

This will allow the hostname to be resolved to a localhost address.

---

### Post by RedSingularity on 2010-08-11
Thanks for that.......using your idea one thing led to another and I found the problem.

Turns out you cant have a hostname with capitals in it.  Problem solved.

---

### Post by Iowan on 2010-08-11
> **RedSingularity said:**
>  Problem solved.
[This]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") kind of solved? ;)

---

### Post by Brandon Williams on 2010-08-12
> **RedSingularity said:**
> Turns out you cant have a hostname with capitals in it.  Problem solved.

[The RFC](http://tools.ietf.org/html/rfc1034) is actually quite clear about the fact that you can use upper case characters in hostnames, but that hostnames should be interpreted in a case-insensitive manner. This means that 'Tims-Laptop' would be invalid if you are also trying to use 'tims-laptop', but that 'Tims-Laptop' is perfectly valid if there are no such collisions. A small amount of experimentation shows that my 10.04 system handles hostnames in just this way.

One of the other things that you did must have solved the problem.

---

### Post by RedSingularity on 2010-08-12
Interesting......I am going to have to experiment some more then.

---

### Post by wollewichtig on 2010-10-02
> **Brandon Williams said:**
> If your /etc/hostname file contains the name 'Tims-Laptop', then there should be an entry for Tims-Laptop in your /etc/hosts file, too, as in:
```
127.0.1.1 Tims-Laptop
```

This will allow the hostname to be resolved to a localhost address.

I have the same problem and tried the recommended input in the terminal, but reply is there is no such file or directory?

But if I go to File System/etc there is a file named hostname with my user name (admin) in it. But only the name, I actually had to change it lately to a shorter version in order to connect from my Windows laptop.

---

