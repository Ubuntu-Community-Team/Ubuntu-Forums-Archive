---
title: "Scripts to run on newly built laptops"
date: 2010-04-07
forum: General Help
---

### Post by Jennii on 2010-04-07
Hi, not sure if anyone can help me with this. I need to try and come up with some scripts to run on newly built laptops to make sure they are in the right groups, have the right software installed etc, my boss wants to have one report per laptop that he can look at and see straight away what is installed. Anyone have anything like this or do anything like this before? Would love some help with this as i am seriously stuck :confused:, thanks a mil

---

### Post by dcstar on 2010-04-07
> **Jennii said:**
> Hi, not sure if anyone can help me with this. I need to try and come up with some scripts to run on newly built laptops to make sure they are in the right groups, have the right software installed etc, my boss wants to have one report per laptop that he can look at and see straight away what is installed. Anyone have anything like this or do anything like this before? Would love some help with this as i am seriously stuck :confused:, thanks a mil

There are apt commands to list all installed packages, and you can use similar command line tools to list users and groups.

You should be able to create some simple scripts yourself to extract this information.

Have a read of the various man pages.

---

### Post by Jennii on 2010-04-08
thanks a mil for your reply, will have a look

---

### Post by terrrorr on 2010-04-08
Hi

Do you have any kind of idea what information you really need. It would be easier to help out.

Here is couple handy commands which might help you out

```
$ dpkg --get-selections
$ uname -a
$ id
$ cat /etc/passwd
$ cat /etc/group
$ ifconfig
$ hwinfo

```

And of course, man will help you to get more information about the command itself

---

