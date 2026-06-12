---
title: "How do you learn networking from an Ubuntu/Linux perspective?"
date: 2012-02-24
forum: General Help
---

### Post by birdfoot on 2012-02-24
I don't know a lot about linux or networking, though I do know the basics.

I've looked at a lot of free networking materials on the net but they all seem to teach things from a windows perspective (eg, they use windows commands). 

Are there any kinds of free material (ebooks, courses, podcasts etc) on the web to learn networking from a linux perspective, using linux commands and linux programs?

---

### Post by raja.genupula on 2012-02-24
[We have many]("http://www.google.co.in/search?aq=1&oq=Linux+networking+pdf&ix=hca&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=linux+networking+pdf+download")

look at that.
hope it helps you . 

all the best.

---

### Post by efflandt on 2012-02-24
Are you familiar with **man** and **apropos** terminal commands?  **man** is to read about specific commands (ie, the manual).  **apropos** helps you search for commands related to some word, to look up with **man**.

So start with **man apropos** (you can use cursor keys or PageUp/PageDown, or q to quit).  Then try **apropos network**, or **apropos network | less** if you want to easily scroll up and down the list.

Then see man pages for ifconfig, route, resolv.conf, and NetworkManager.

Some commands to try:

```
ifconfig -a
route -n
cat /etc/resolv.conf
cat /etc/hostname
cat /etc/hosts
```

---

### Post by birdfoot on 2012-03-12
> **raja.genupula said:**
> [We have many]("http://www.google.co.in/search?aq=1&oq=Linux+networking+pdf&ix=hca&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=linux+networking+pdf+download")

look at that.
hope it helps you . 

all the best.

> **efflandt said:**
> Are you familiar with **man** and **apropos** terminal commands?  **man** is to read about specific commands (ie, the manual).  **apropos** helps you search for commands related to some word, to look up with **man**.

So start with **man apropos** (you can use cursor keys or PageUp/PageDown, or q to quit).  Then try **apropos network**, or **apropos network | less** if you want to easily scroll up and down the list.

Then see man pages for ifconfig, route, resolv.conf, and NetworkManager.

Some commands to try:

```
ifconfig -a
route -n
cat /etc/resolv.conf
cat /etc/hostname
cat /etc/hosts
```
Thanks very much guys, but is there maybe something a bit more laymen friendly?

---

### Post by birdfoot on 2012-03-12
Sorry I meant that that 2nd reply was a bit too technical and dry.

The first pdf from the search in the first link is over 12 years old. The other results are not very helpful.

---

### Post by birdfoot on 2012-03-12
bmp

---

### Post by kevdog on 2012-03-12
What specifically do you need to know?  A lot of networking jargon and info spans OS types -- IP addressess, tcp, udp, etc.

---

### Post by birdfoot on 2012-04-05
> **kevdog said:**
> What specifically do you need to know?  A lot of networking jargon and info spans OS types -- IP addressess, tcp, udp, etc.

Well I've just noticed that there are a lot of commands that they use in beginning networking that are from windows. I don't think the commands are the same in Linux, unless I'm wrong. Also, many GUI features available to get information about and configure network connections are not available in Linux (as far as I know).

---

### Post by wildmanne39 on 2012-04-05
Hi, to be honest there is no easy way, I have been studying and working with wireless issues for the better part of a year, I have learned everything from google and watching some good people in the networking section work and asking questions when needed.

I started by pasting the commands they used into the terminal to study the information that was outputed.

---

