---
title: "A fast way to destroy 1 terabyte worth of storage?"
date: 2010-02-15
forum: General Help
---

### Post by geordie_123 on 2010-02-15
Hello,
I've been backing up a lot of my computer data for 2 years now and it has added up to a terabyte, so I went to bestbuy and bought a 1.5 terabyte external hard drive. I went home and I moved all my data on to it.
Now it is starting to fail! As soon as I heard clicking noises I copied all the files over back to my original hard drive. 
I had alot of personal information on the 1.5 TB hard drive that is failing(it is still working though), and incase 
when I try to take it back and they restore it, I do not want them looking through my stuff. I have tried the shred command but thats going to take forever just to overwrite one terabyte once.
Will a format remove all my personal files from recovery? What are some other things I could try?

---

### Post by audiomick on 2010-02-15
Shred or something similar is the only way to make data really disappear. A format doesn't physically overwrite the data, it just removes all indexing information that shows where the files are. If someone really wants to read it, it is theoretically possible, but requires a lot of effort. The question is, are the people at the store or the manufacturer of the drive interested in making the effort?

Shred takes a long time because it has to write to every single bit of your 1.5TB. This takes time, and can't be sped up. It is a function of the speed of the drive.

---

### Post by philinux on 2010-02-15
> **geordie_123 said:**
> Hello,
I've been backing up a lot of my computer data for 2 years now and it has added up to a terabyte, so I went to bestbuy and bought a 1.5 terabyte external hard drive. I went home and I moved all my data on to it.
Now it is starting to fail! As soon as I heard clicking noises I copied all the files over back to my original hard drive. 
I had alot of personal information on the 1.5 TB hard drive that is failing(it is still working though), and incase 
when I try to take it back and they restore it, I do not want them looking through my stuff. I have tried the shred command but thats going to take forever just to overwrite one terabyte once.
Will a format remove all my personal files from recovery? What are some other things I could try?

If the drive is toasted a large hammer will do the job. ;)

---

### Post by geordie_123 on 2010-02-15
Thanks, I have 20 terminals open shredding different parts of the hard drive. :)

---

### Post by audiomick on 2010-02-15
> **philinux said:**
> If the drive is toasted a large hammer will do the job. ;)
True, Phil, as would a magnet (oh, hadn't thought of that as I was writing the last post...), but I think the OP is going for a warranty claim.:)

On the subject of magnets, if you wrap a number of turns of an AC power cable around it with something on the end that is drawing a bit of power and leave it for an hour or so, I suspect that would kill it, but I do mean kill it. If would probably void any chance of warranty too.;)
I don't know how well drives are shielded, but putting magnetic storage in an oscillating electrical field like that is definitely not good for it...

---

### Post by geordie_123 on 2010-02-15
Wow, thats pretty awesome. I'm going to remember that,

---

### Post by bowens44 on 2010-02-15
> **philinux said:**
> If the drive is toasted a large hammer will do the job. ;)

Yes, but wouldn't that void the warranty :D?

---

### Post by The Cog on 2010-02-15
I would use a command like this but be careful to get the correct output device name or you might wipe a valuable disk:
> sudo dd if=/dev/zero of=/dev/sdx
This will overwrite the entire disk with zeros, removing partition tables and data.

---

