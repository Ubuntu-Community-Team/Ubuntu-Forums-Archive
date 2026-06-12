---
title: "i want to setup a print server in the house"
date: 2010-01-14
forum: General Help
---

### Post by osmorphyus on 2010-01-14
hello!

i have an old clunker box with no HD insalled in it.  it does have a cd rom however, and i would be able to run DSL from it with that alone.

i want to set this box up as a print server, since as it is all of the computers in the house must actually be moved to the printer and connected to it via USB to print.

i am looking to simplify this for everyones benefit, here.

the box i am going to use will *not* be connected to a monitor, KB or mouse once it is ready to be left on its own.  i will use these to set it up, but after that, id prefer a way to http:  into it or FTP into it.

i am on ubuntu, the rest of the house is on XP.  i figure i will have to configure the computer with SAMBA in order to set it up for sharing, is that correct?

i will be connecting the computer to the wireless router.  



basically, id just like help with a roadmap on what needs to be done to set this up.  i dont need step by step directions on everything, just an idea of where to start.  id really like to get this setup within a few hours.  

:D i hope someone can help!

p.s.
just wanted to append:
the printer has no network capabilities built into it.  just a standard issue USB driven print/scanner/fax.  unless the fax function has a way to give it network support...?

---

### Post by ST3ALTHPSYCH0 on 2010-01-14
Should be able to just install the printer to that machine and share it. Then set the other machines up to print to a shared printer

---

### Post by audiomick on 2010-01-14
samba to share the printer.
ssh to access the "printer server" from another box.

---

