---
title: "Synaptec problem"
date: 2006-05-24
forum: General Help
---

### Post by DarkDancer on 2006-05-24
When I try to load synaptec I get this:

> E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

and of course nothing shows.

I also get this from terminal:

> darkdancer@DarkDancers:~$ sudo apt-get update
Password:
E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
darkdancer@DarkDancers:~$ sudo debtags update
sudo: debtags: command not found
darkdancer@DarkDancers:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Any help would be appreciated.

---

### Post by richbarna on 2006-05-24
Hi DarkDancer,
The first message looks like a repository url problem on the sources.list.
And the second one looks like you had synaptic open already when you did apt-get in the terminal.
You can't run both at the same time.
Can you post a copy of your sources list?
> sudo gedit /etc/apt/sources.list
Then copy and paste it here.
And i'll take a look at it.

---

### Post by DarkDancer on 2006-05-24
Ok, guess I have found the probelm, there is nothing in /etc/apt/sources.list.

How do I fix it? ;)

---

### Post by dashnak on 2006-05-24
Go here:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by DarkDancer on 2006-05-24
Thanks! that seems to have turneds the trick (so to speak!) ! ;)

---

