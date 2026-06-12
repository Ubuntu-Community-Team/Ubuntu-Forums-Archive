---
title: "Install Firefox 1.5 kubuntu?"
date: 2006-03-29
forum: General Help
---

### Post by dawhoo on 2006-03-29
First of all - wow.  I really like the new OS.  

I installed Ubuntu first, but my little experience with linux previously (Peanut) reminded me, I want KDE instead, so I installed Kubuntu so I could have my slightly more familiar KDE. But to my dismay, there was no Firefox in Kubuntu, at least I don't think there is.

How can I get Firefox 1.5 installed?  I'm a n00b, so I need as much simple direction as possible.  And once I do get it installed (lots of faith) do the extensions still work like in Windows?

I did manage to get NTFS to read, so I'm super stoked at that.  Also, this may be the easiest distro I've ever used to install, but where it's really shines: it's easy to use and that's what will make people switch.

---

### Post by dawhoo on 2006-03-29
Just to clarify, I tried the install method found in the wiki for FF 1.5, but it didn't work for me and I was getting back a lot of errors "No such file or directory".

When I tried to install 1.0.7 first using

sudo apt-get update
 sudo apt-get install firefox

I get 

Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

Thanks!

---

### Post by aysiu on 2006-03-29
When you get that message, it means your sources.list is messed up.

To clean up your repositories list, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

To have a script install Firefox 1.5 go here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Note: you will need a good sources to list in order for the script to work.

---

### Post by dawhoo on 2006-03-29
Oh yeah!  That did it.

I ahve all my files and Firefox too. :D

where's the dancing smiley?  :D

---

### Post by aysiu on 2006-03-29
[QUOTE=dawhoo]Oh yeah!  That did it.

I ahve all my files and Firefox too. :D

where's the dancing smiley?  :D[/QUOTE] Great to hear that it works.

---

