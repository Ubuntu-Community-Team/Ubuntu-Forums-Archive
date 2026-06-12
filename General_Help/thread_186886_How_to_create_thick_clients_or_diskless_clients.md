---
title: "How to create thick clients or diskless clients?"
date: 2006-06-02
forum: General Help
---

### Post by delagarza on 2006-06-02
I have struggled trying to find complete, consise, step by step instructions on how to create "thick clients or diskless clients" using Ubuntu over NFS.  Every document I have found is vague, out of date or lacking in some way of actually creating the client.  

Has anyone really done this?  If so how did you do it?  Your help is greatly appreciated.

-raul

---

### Post by garyng on 2006-06-02
out of date ? That mechanism hasn't been changed for ages so even it was a 5 years old doc, it should work. Basically you need :

1. A DHCP/BOOTP server that can handle netboot/etherboot(to direct them usually based on MAC to the right linux image)

2. A TFTP server that stores these linux image/initrd the client would retrieve and boot(directed by 1)

3. A NFS server serving as the root for the image in (2)

That is all.

The LTSP package should have all you need.

---

### Post by Ronald Baljeu on 2006-07-30
I've made an odd fat client setup, without using LTSP.
This works great for me. Then I thought I would share it
with everyone, by writing a document. Phew, that aint easy...
Documenting is harder than setting it up :D 

Current attempt:
[http://www.xs4all.nl/~rjb/](http://www.xs4all.nl/~rjb/)

Currently I'm writing scripts to make setting up the thing less complicated.

I hope to finish the docs soon.

Cheers,
Ronald

---

### Post by EmmEff on 2006-08-03
Any hints for doing an install from a PXE booted host?  When I use the alternate install CD, it goes to the web, by default.  How do I tell it to use a NFS share on the local network as the installation media?

---

### Post by Ocxic on 2006-08-03
if your using a network pxe boot, you don't need the cd. and technically prolly shouldn't even have to use it.

---

### Post by EmmEff on 2006-08-03
Sorry, I meant that I wanted to share the files from the CD to use as the installation media.  I did figure it out and realized I needed a preseed file.  Thanks.

---

