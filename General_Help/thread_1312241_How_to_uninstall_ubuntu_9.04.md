---
title: "How to uninstall ubuntu 9.04"
date: 2009-11-03
forum: General Help
---

### Post by kyqinqiqin on 2009-11-03
Now this ubuntu 9.10 is out! I want to install this ubuntu 9.10. I didn't knew how to uninstall this ubuntu 9.04 from my machine. Who can tell me how to do!
Thanks for all your help!

---

### Post by RedSingularity on 2009-11-03
System>admin>Software sources.  Make sure under the updates tab "show new distro" is set to normal releases.  Then just do an update with the update manager.

---

### Post by RedSingularity on 2009-11-03
I made it hard.....better yet do this from terminal.  

sudo apt-get update

sudo apt-get upgrade

sudo apt-get distro-upgrade

Then you will have 9.10:)

---

### Post by kyqinqiqin on 2009-11-11
In this way,I tried to update this ubuntu 9.04 to this ubuntu 9.10, I is faults. And now I only thinking want to uninstall this ubuntu 9.04 when I'm want to disapear this ubuntu linux used a disk setion, and I want to put it for windows. I think in this way of my thinking, would go to the lavatory help me managing two systems of in stall my machine.
 
But finally. I don't understand how to unstall ubuntu 9.04. Please help me. 
 
Thank you for your help.

---

### Post by RedSingularity on 2009-11-11
Well you can reformat your hard disk drive all together.  That will erase all the stuff on the hard disk.  Then you can install windows first and ubuntu 9.10 second.  To reformat the hard disk do the following:

1)  Instert a ubutnu live cd
2)  In a terminal do "sudo apt-get install gparted"
3)  Go to system>admin>partition editor
4)  Select the hard disk u want formated and format it under Fat32.

That will clean the drive for you.

---

### Post by Hendrixski on 2009-11-11
If managing two systems is too much, then just delete windows and install just Ubuntu 9.10.

Simple. :-)

---

### Post by Puzzled Guy on 2009-11-21
Just go to the update manager in System>Administration>Update Manager

On the top of the window there should be a box with "New distribution release 9.10 is available [Upgrade]".

Before you upgrade though, google for an upgrade guide, there are quite a few of them.

And also  check this: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

