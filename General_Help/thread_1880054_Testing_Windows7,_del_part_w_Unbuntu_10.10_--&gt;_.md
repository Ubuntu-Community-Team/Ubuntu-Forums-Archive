---
title: "Testing Windows7, del part w/ Unbuntu 10.10 --&gt; CDBOOT error 5"
date: 2011-11-12
forum: General Help
---

### Post by wannabegeek on 2011-11-12
Hi Folks....

I'm still trouble shooting my new media server.....Ubuntu 11.10 so far appears the best Ubuntu for it.
I also want to experiment with windows7 .

I have a Windows7 CD that I tried to install win7 from. Because the partition I pointed to was still in EXT4 the installer wouldn't touch it.

So I then deleted the partition, created a new table,  and used the whole drive to make a single NTFS partition. That's the one and only partition on the disk now. 

I disconnected my other drive with my media on it and connected the SATA HD for install, to the first 
SATA port on MOBO.  


Perhaps I put it in the wrong one ? I have an Asus P8H67 and it has two grey colored labeled SATA6G
and four other SATA connectors that are blue and labelled SATA3G.

When I try booting from the Win7 DVD ROM, I get the CDBOOT error 5 message...
Not sure what to trouble shoot now....not sure I'm connecting the HD to the first boot drive either...

TIA !
wbg

---

### Post by wannabegeek on 2011-11-12
Perhaps I didn't trouble shoot long enough....trying to get something working by tonight as I have to return a
borrowed USB DVD ...

I changed to another Wind7 disk I have 'laying around'  and switched the USB port of the DVD reader to another one I think is more stable for this kind of thing.

Got back to an install procedure and installing now....I'll prolly dual boot this thing since I have a bunch of media already on ext4.

---

### Post by Mark Phelps on 2011-11-13
Is there a question here?

The two types of SATA ports are for two types of SATA drives -- as indicated -- 3GB/s and 6GB/s.  Unless your drive indicates it handles 6GB/s, you should connect it to the 3G ports -- although, it might still work on the 6G ports because some are downward compatible.

---

### Post by wannabegeek on 2011-11-13
Thanks Mark for your interest....I was staying up too late working on this...

My question which was pretty mis-formed, is, whether I need the Sata Drive to be connected in a certain way for Windows to install to it ?

After getting Win7 installed, I wasn't as impressed as I thought I would be and decided  that Ubuntu 11.10 is actually a better fit for this project.

cheers,
dpc

---

