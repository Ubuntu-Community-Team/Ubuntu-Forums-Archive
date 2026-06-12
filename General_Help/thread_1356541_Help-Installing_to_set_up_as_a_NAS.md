---
title: "Help-Installing to set up as a NAS"
date: 2009-12-16
forum: General Help
---

### Post by jamesadams0 on 2009-12-16
Hi everyone,

this will be my first experience with a UNIX or Linux operating system so bear with my n00b questions please :)

I have a pentium 4 2.4ghz computer which i have decided would be useful to turn into a server/nas for my house.
What i have done so far is installed 3 x 1.5 TB hard drives (SATA2) and i have left in an old 160gb WD IDE drive which i plan on using as the boot drive.

My aims:

To set up my 3 1.5 TB hard drives in a Raid 1 or Raid 5 array.(software raid)

To be able to access the contents of those drives (mostly will be consisting of media) from every pc/mac in the house that is connected to the network. I want to be able read/write at will from any computer in the house.

To be able to stream from my server all my media to my ps3 (most probably using an application made available for linux named ps3 media server.

To have the computer running 24/7


My questions:

How am i able to set up the Raid array using ubuntu? is it during installation, before installation or after installation that i will be setting them up? (currently they are unformatted, straight out of the packaging and into the computer)

Is ubuntu the right OS for my needs and will it handle all of my needs for a nas-like server?

Im hoping not to need command line, but if i do, what will i need to do?

Which release of Ubuntu should i be looking to download if this is for me? (server, standard etc)


Thanks (in advance) soooo much for your help, and i look forward to joining the Ubuntu community if its for me

Sorry for such a long post, but just want to get this discussion flowing and all my questions out in the open.

Good luck,

James

Ps: i've heard of a thing called samba. what is it? and will i need it to complete my objectives.

---

### Post by xifer on 2009-12-16
Hi, not sure if Ubuntu is best option here - maybe look at REDHAT  or openbsd.

But look into LOGICAL VOLUME MANAGER. for software RAID options

samba is probably the easiest way to share these files across your network so read up on that too.  Good luck!

---

