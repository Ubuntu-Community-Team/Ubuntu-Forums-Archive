---
title: "Whats wrong with my karmic?"
date: 2010-03-13
forum: General Help
---

### Post by stjohnmedrano on 2010-03-13
good day fellow ubuntu users, i started using ubuntu last october 2009, so i guess iam still a newbie. everytime i go to work and school i am very excited to go home just to check on my ubuntu, i dont know may i guess i was addicted to it. last week i decided to make it a ftp and ssh server, a week after the installation when i get home my ubuntu was corrupted and i dont know how to fix it, i wasnt able to sleep last night, thingking what happen to her?, but still i can log on as root user but errors are coming up everywhere, then it pops out on my mind to solve the problem using this command

sudo fsck /dev/sda1

suddenly i was able to login in my desktop.

1. my question is how do i know my system is still in good running condition? what commands to I use?

2.  I am afraid that those errors might still comeback, coz its somewhat to do with my sda1.

thank you and hoping to hear any suggestions that will help me. thank you.

---

### Post by Iowan on 2010-03-13
Sounds similar to a problem I had with a machine awhile back. It'd crash every couple of weeks. *Usually* it worked after a FSCK - but the last time it had damaged too many critical files. The problem went away when I replaced the hard drive.

---

### Post by stjohnmedrano on 2010-03-13
> **Iowan said:**
> Sounds similar to a problem I had with a machine awhile back. It'd crash every couple of weeks. *Usually* it worked after a FSCK - but the last time it had damaged too many critical files. The problem went away when I replaced the hard drive.

thank you for the response sir,  now i get it, the problem will still coming back so i have to replace my hard drive.

---

### Post by souleke on 2010-03-13
had the same Iowan said, kept fixing it but after a while i had a big crash 
so best you go and replace the hd ;-)

---

### Post by stjohnmedrano on 2010-03-13
> **souleke said:**
> had the same Iowan said, kept fixing it but after a while i had a big crash 
so best you go and replace the hd ;-)

thank you very much for your adviser sir..

---

### Post by sdowney717 on 2010-03-13
you can run system admin disk utility to check the disk

---

### Post by stjohnmedrano on 2010-03-13
> **sdowney717 said:**
> you can run system admin disk utility to check the disk

thank you sir and let me show you the result.

[IMG]http://farm3.static.flickr.com/2767/4429687654_d7331f68f0_m.jpg[/IMG]

---

### Post by sdowney717 on 2010-03-13
your picture is not a link.
So no one can view it.

---

### Post by stjohnmedrano on 2010-03-13
> **sdowney717 said:**
> your picture is not a link.
So no one can view it.

I, sorry sir, here it is

[http://farm3.static.flickr.com/2767/4429687654_d7331f68f0_b.jpg](http://farm3.static.flickr.com/2767/4429687654_d7331f68f0_b.jpg)

---

### Post by sdowney717 on 2010-03-14
Disc has a few bad sectors. The disk is designed to fix itself up to a point. Something like this may never give more trouble or may give additional trouble.
Disk does its own self monitoring and will mark and lock out sectors as bad, so they wont be used for data anymore.
It must be that the data you had was used in booting and when the disk decided those sectors were bad, they were locked and the system could not boot.

---

### Post by stjohnmedrano on 2010-03-14
> **sdowney717 said:**
> Disc has a few bad sectors. The disk is designed to fix itself up to a point. Something like this may never give more trouble or may give additional trouble.
Disk does its own self monitoring and will mark and lock out sectors as bad, so they wont be used for data anymore.
It must be that the data you had was used in booting and when the disk decided those sectors were bad, they were locked and the system could not boot.

thank you very for your time in explaining sir, so i guess i have to buy a new hard disk then.

thank you, thank you..

---

### Post by stjohnmedrano on 2010-03-15
> **sdowney717 said:**
> Disc has a few bad sectors. The disk is designed to fix itself up to a point. Something like this may never give more trouble or may give additional trouble.
Disk does its own self monitoring and will mark and lock out sectors as bad, so they wont be used for data anymore.
It must be that the data you had was used in booting and when the disk decided those sectors were bad, they were locked and the system could not boot.

sir last sunday night my karmic crash again, right now im having a fresh install. :confused:

---

