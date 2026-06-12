---
title: "gnome-terminal question?"
date: 2005-02-28
forum: General Help
---

### Post by gmc on 2005-02-28
Hello Folks,

I'm trying to get gnome-terminal to open multiple ssh sessions with (in) tabs. If I try:

**gnome-terminal -e sh --tab -e sh**

I get a terminal window with 2 tabs and a CLI in each... however if I try:

**gnome-terminal -e "ssh -XC hostone" --tab -x "ssh -XC hosttwo" --tab -x "ssh -XC hostthree"**

I get a terminal window with no tabs and a CLI on hostone?

Anyone know how to do this?  ](*,) 

Gord

---

### Post by gmc on 2005-03-04
Folks,

   I found my solution. If you want gnome-terminal to open multiple tabs that are ssh'ed to multiple local machines, it's done as follows:

   gnome-terminal -e **'**bash -c **"**ssh -C hostone**"** **'** --tab -e **'**bash -c **"**ssh -C hosttwo**"** **'** --tab -e **'**bash -c **"**ssh -C hostthree**"** **'**

*note*: the usage of **'** (single quotes) and **"** (double quotes).

The above will open three tabs in gnome-terminal and each tab will be ssh'ed to a different host. It's kind of handy if your are doing maintenance on multiple machines.

Gord  8-)

---

### Post by jdodson on 2005-03-04
howto is not the place to ask questions.  please read the forum rules before posting.

---

