---
title: "Problems with Software Centre and OS Updates"
date: 2011-05-14
forum: General Help
---

### Post by Trilby on 2011-05-14
A friend of my has very recently installed Ubuntu 11.04 on his Compaq laptop (using the classic desktop if that is of any relevance). There appear to be no issues with one exception. He finds himself unable to see any search results on the Ubuntu software centre or see the list of updates for the system. In addition, apt-get does not appear to work either.

Can anyone help?
My friend is a total virgin to Linux, so to speak, and I'd rather not have this issue sour his first impression of Ubuntu.

Many thanks,
Trilby

---

### Post by SavageWolf on 2011-05-14
What are the problems with apt-get?

---

### Post by CoolJohnB on 2011-05-14
Maybe he needs to change the server in software sources and of course make sure there is one there!

---

### Post by Trilby on 2011-05-15
The problem is now fixed. Details as follows:

Running "sudo apt-get update" produced this error:
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```Upon examination, this file had been replaced with a HTML file.
deleting it re-running "sudo apt-get update" replaced the file with a valid one and switched the error to "restricted-i386" instead of "binary-i386".
deleting the whole "/var/lib/apt/lists" and re-running "sudo apt-get update" solved the problem

In short:
Diagnosing
If running "sudo apt-get update" gives this output:
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/<ANYTHING>
E: The package lists or status file could not be parsed or opened.

```then this issue is the one in question.

Solving the problem:
Delete /var/lib/apt/lists/
re-run apt-get update to rebuild it.
relevant commands:
```

sudo rm -rf /var/lib/apt/lists/
sudo apt-get update

```

---

### Post by minimike150 on 2011-05-17
Thanks for the suggestion Trilby, that fixed my issue straight away.

---

