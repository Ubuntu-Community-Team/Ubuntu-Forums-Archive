---
title: "Small Server"
date: 2012-06-28
forum: General Help
---

### Post by Bob Fletcher on 2012-06-28
I am posting this here as the other option is the server forum but that looks too technical for me.

I am currently running a Web and FTP server on my QNAP TS-212 NAS. The server is used for general testing and uploads used by myself and a few friends. Any more tragic might push my bandwidth too much.

It would seem to me I would be better setting the server up on a separate Linux Box running a flavour of Ubuntu. There are plenty of ex commercial computers I can pick up cheaply. 

1. Is this a good idea? I like to keep storage and servers separate.
2. Considering the ARM processor and modest memory in the NAS what would be the minimum requirements for satisfactory running.

Like to get some opinions especially from anyone else who is doing similar.

Robert...

---

### Post by zero2xiii on 2012-06-28
Hay,

I am running a FTP, HTTP, and NAS server on a dual-core 1.6GHz 2GB ram system with aproxamitly 12-25 users at any given moment. And I have no issues with specs being to low.

A couple of tips:

Use the gui ubuntu to setup everything. And then disable the graphical environment and boot only to a CLI to conserve some resources (even on the arm system this should give you space for 1 or 5 more users...)

using something like webmin to admin everything helps quite a bit in making things easier.

As for the storage. There are so much options. But one thing I recommend is backups!! like everything.. Also if data integaredy is an issue I recommend the ZFS filesystem format, or XFS.. There are some trade offs (and difficulties in using them such as in the case of ZFS) but it helps againts data corouption due to power failure, IO error and so forth.

I would personaly (if the hardware is availible) set up a storage server with the storage needed with atleast 2x 1gigbit network connections to the server hosting the HTTP and FTP servers. This allows all the file system handeling to be done away from the actual server resources. Such as backup, shadowing, taking snap shots or what what...

Or, I would run a VM for the server ON the storage server, thus avoiding the bottleneck (of the network), but you need the hardware to back this. Atleast i3 system with upwards from 4gig ram.

If you have any specific questions or need help setting up stuff to your specific needs or with your hardware... PM me, so as not to clutter the forums with redundent questions as most questions will have answers in the forums already (I have responded to a very similar thread a while back aswell)

Cherz

EDIT:
Just a link. To turn a GUI system to a headless or CLI:
[http://ubuntuforums.org/showpost.php?p=11825232&postcount=10](http://ubuntuforums.org/showpost.php?p=11825232&postcount=10)
I do state that it saves very little resources. It does save some. And on a small, lightweight machine, every few MBs of ram you can spare and few CPU cycles can make a difference between "enough" and "just a little to little" hahaha.

---

### Post by Cheesemill on 2012-06-28
> **Bob Fletcher said:**
> Any more tragic might push my bandwidth too much.

If it's bandwidth that is a concern then setting up a new server won't make a difference.

Even if you spent £10,000 on a server you would still have the same internet bandwidth, only purchasing a faster internet connection would change this.

---

### Post by Bob Fletcher on 2012-06-28
> **zero2xiii said:**
> 
If you have any specific questions or need help setting up stuff to your specific needs or with your hardware... PM me, so as not to clutter the forums with redundent questions as most questions will have answers in the forums already (I have responded to a very similar thread a while back aswell)

Cherz

EDIT:
Just a link. To turn a GUI system to a headless or CLI:


Hi Cherz

Thank you so much for your offer of help and I will indeed PM you as I am in new territory here. My system will be very modest. Yes once everything is installed I would prefer to run something like Webmin and just hide it in a corner.

Robert

---

### Post by Bob Fletcher on 2012-06-28
> **Cheesemill said:**
> If it's bandwidth that is a concern then setting up a new server won't make a difference.

Even if you spent £10,000 on a server you would still have the same internet bandwidth, only purchasing a faster internet connection would change this.

Hi,
When I mentioned bandwidth it was about chewing up my 40 G allocated allowance. I do have a hosted website and that is where the public can go. As I said my home server will and is used for testing and private use. I am not planning on running on ARM doing that already.

My rational is the NAS is for storage mainly my media files and Squeezbox Server also for backups from my desktop and website. Therefore the NAS should be kept this way but as it performs very well for my web user I can see that resources do not have to be great.

Robert...

---

