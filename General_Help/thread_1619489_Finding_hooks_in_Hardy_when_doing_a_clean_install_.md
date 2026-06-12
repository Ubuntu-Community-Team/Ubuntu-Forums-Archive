---
title: "Finding hooks in Hardy when doing a clean install onto Lucid"
date: 2010-11-11
forum: General Help
---

### Post by pharubu on 2010-11-11
What are the tricks of the trade to finding hooks on a current system
which have not been included in an upgrade / need to be included
on a clean install ?

My predecessor who managed our website installation was a demi-linux-god...
I on the other hand barley scratch the Linux surface. 

A few months ago I ran an update for Hardy Heron. Sure enough the website 
did not run as expected with the new upgrade.

So I performed the below steps to find any hooks that were missing:
- ftp the current system to a directory on a shared drive
- created a new VM of the current system
- pressed "update" on the new VM
- ftp the new VM system to a directory on a shared drive
- ran a diff over all the files/dirs

Two svn files buried deep in the system had been changed by the update. 

To better understand the website I would now like to build it from the ground 
up on Lucid.

So I can: 
- do a compare with Synaptic package manager
- diff as per above

But what other tricks are there ?

---

