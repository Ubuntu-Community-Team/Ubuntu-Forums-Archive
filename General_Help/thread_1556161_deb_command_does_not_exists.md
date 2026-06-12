---
title: "deb command does not exists"
date: 2010-08-19
forum: General Help
---

### Post by tongucy on 2010-08-19
Hi, I downloaded the latest version Ubuntu from ubuntu.com and I am trying to install Oracle XE from the below link but for the first step couldn't find "deb" command, is the command replaced? Thanks.

[http://www.oracle.com/technetwork/topics/linux/xe-on-kubuntu-087822.html](http://www.oracle.com/technetwork/topics/linux/xe-on-kubuntu-087822.html)
[I]
..
[/I]*There is now an apt-get repository up on oss.oracle.com for XE. Just add:*
                                    [I]deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free
[/I]*  to /etc/apt/sources.list and then:                                     *
..

---

### Post by jobix on 2010-08-19
There is no "deb" command. All it is asking you to do is add that line to the /etc/apt/sources.list file and then execute the "wget" command to get the file followed by apt-get.

---

### Post by tongucy on 2010-08-19
Thanks jobix, my mistake, regards.

---

### Post by snowpine on 2010-08-19
Welcome to the forums! You are trying to follow a tutorial for the long-obsolete Ubuntu 5.10 using a repository for Debian Unstable! :(

This info seems more current (but note I am not an Oracle expert so proceed with caution): [http://www.oracle.com/technetwork/database/express-edition/downloads/102xelinsoft-102048.html](http://www.oracle.com/technetwork/database/express-edition/downloads/102xelinsoft-102048.html)

---

