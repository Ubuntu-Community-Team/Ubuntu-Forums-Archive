---
title: "Setting Up Basic Network"
date: 2010-06-18
forum: General Help
---

### Post by spearlymatt on 2010-06-18
Hello all, and I am sorry if this is in the wrong section.  I saw the networking section, however, I am not trying to do any advanced networking. 

I have about three computers or so connected to the Internet, and they all work fine, except I have no clue how to make them communicate with each other.  I've seen countless guides and tutorials, but they are all either very confusing, or not what I need.

Eventually, I would like to have a server, or at least a Public folder of my network.  

I don't even know where to start, though, like I said, there are a million tutorials I have found, but none of them seem to help me.  If it is easier to set up a network (I'm not even sure what the true definition of network is) via a different operating system, I have Ubuntu +Vista on this machine, XP on another, and varying distros on the last machine.  

Just even a basic start point would be appreciated.

Thank you.

EDIT: Also, on startup, my splash screen shows for a long time.  I don't see an obvious reason why, as this is a fairly good computer (4gb RAM, Phenom II 955, etc.) and 9.10 booted instantly.  I have researched it before, and people say that if you didn't have a floppy drive, and had it enabled in BIOS, it would cause it.  But I went back through and disabled mine, but the problem still persists.

EDIT2:  Sorry, I just keep thinking of small little problems I could never find the answer to.  In Fedora, how do you go about installing programs?  I go to add/remove programs, and find the package and everything, but what do you do from there?  And is Fedora any harder than using Ubuntu to make a server?

---

### Post by yeleek on 2010-06-18
If you want your shared folder to be accessible by windows and linux, you'll need to use SAMBA.  Heres why

[http://en.wikipedia.org/wiki/Samba_%28software%29](http://en.wikipedia.org/wiki/Samba_%28software%29)

and here is a howto for a peer-to-peer network.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Additional q 1) I did read issues re slow GRUB booting on a dual booting machine, can't remember specifics.  Try googling or hope someone else replies

Additional q 2) Server - A proper server distro, doesn't have a gui, is command line only, hardened for security purposes etc.  If you are just starting out, personally I'd stick with ubuntu desktop and install the packages you want on there.

---

