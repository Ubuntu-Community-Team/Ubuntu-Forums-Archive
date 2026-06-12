---
title: "Clonezilla quandry"
date: 2010-05-10
forum: General Help
---

### Post by CNBarnes on 2010-05-10
I am going to start this with a disclaimer that up until now, I have always used Symantec Ghost to create my images.  Which means I am mentally in the "mode" of wanting to do things in the same general methodology.

My environment:
* a computer lab of 16 computers 
* each computer is dual boot w/ Win7 & Ubuntu (10). 
* I have 1 computer setup and working perfectly.

What I want to do is to make an image of this computer, saving the image to a disk on a server.  Then I want to copy this image to all 16 computers simultaneously over the network.  


I have read the page at [http://www.clonezilla.org/clonezilla-server-edition/](http://www.clonezilla.org/clonezilla-server-edition/) and have to admit that I am REALLY confused.  It appears that what I need to do is to setup a DRBL server - but that is talking about doing private networks, etc.  :confused:   (Ghost never required a private network)


Also, I am concerned with the parts where it warns about "the disk size of the destination must be at least as big as the original".   The original disk was not completely full - does this mean Clonezilla/DRBL is copying the empty space too?


Note: the only reason I am looking at Clonezilla is because even the newest version of Ghost can't handle ext4 filesystems.  :(

---

### Post by Mark Phelps on 2010-05-10
Sorry for the obvious question but I feel compelled to ask ... are these all identical hardware? And I do mean identical.

---

### Post by CNBarnes on 2010-05-10
Yes.  They are EXACTLY identical.

---

