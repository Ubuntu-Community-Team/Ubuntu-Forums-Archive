---
title: "New build. Hard drive set up. RAID questions &amp; SSD questions."
date: 2010-11-03
forum: General Help
---

### Post by gofes on 2010-11-03
After keeping my old (laptop) computer going for 8 years, I've finally taken the splash and ordered myself a new PC, well the compoents any way to build myself a desktop this time.

I've just got a couple of questions.
I've got a 60GB SDD and a 1TB HDD. On the SDD I was planning on partitions for 
Ubuntu
Swap
Window partition, to run a Virtulisation, not dual boot.

Performance wise, is it best to install / on the SDD and /home on the HDD or /home on the SDD as well and just move music and videos ect to the HDD.

Just to complicate things, when ordering the HDD there was an offer to get a second 1TB HDD for an extra £11, so now I have 2. I was planning to set these up as RAID 1, which I believe I can do via the alternative install. 

What would be the best way to then backup / . I guess it must be possible to schedule an image of/ to be copied across to HDD is it?

I did hear that RAID was a bit iffy in ubuntu, but looking about on the net things seem to be better 9.10 &#8594; Also the boot disk isn't RAID.

Is this the right way to go about things? Are there any RAID or SSD issues I should be aware of?

---

### Post by dcstar on 2010-11-04
> **gofes said:**
> 
.........
Is this the right way to go about things? Are there any RAID or SSD issues I should be aware of?

Do not "waste" your SSD with Swap or things like /tmp & /var- all they will do is increase the usage of the finite number of writes that a SSD has.

Even moving /home off the SSD will probably be worthwhile - leave the SSD for things that have minimal changes but where you want maximum read speed.

Make sure you use the "discard" fstab option for your SSD partition(s) and make sure **all** OSs using the SSD support TRIM (10.10 does, 10.04 does not - yet).

---

