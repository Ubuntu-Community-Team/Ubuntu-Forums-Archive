---
title: "Major Failure(NEED HELP URGENT)"
date: 2009-11-16
forum: General Help
---

### Post by Mag1cN1nja on 2009-11-16
I treid to get on my computer today after one day of being off. I boot ubuntu with win xp as my slave. Boot ubuntu and it freezes. I tried to boot again and a bunch of commands come up with switching to high resolution mode at the end. Tried seperatly running my ubuntu har drive. Same thing. Trie seperatly booting my win xp hard drive. It comes up and about 5 min after it freezes and goes to the ble screen of death. I switched the cable the connected the hard drives to the mother board 3 times(had thre different cables laying around) After i switched cables i started ubuntu and it started and i surfed for a bit on firefox then it just froze and wouldnt start at all after word. Same thing for winxp. booted but blue screen of death afterward. I tried to get an av for ubuntu thinking it may be that but i cant get to that download page. Same with my win xp. I cant even get my programs running on there. Thats about as detailed as i can get so can someone please help me

---

### Post by Mag1cN1nja on 2009-11-16
help ne one

---

### Post by sccrstvn93 on 2009-11-16
Try booting from a live cd. Sounds like it could be a hardware problem.

---

### Post by Mag1cN1nja on 2009-11-16
> **Mag1cN1nja said:**
> I treid to get on my computer today after one day of being off. I boot ubuntu with win xp as my slave. Boot ubuntu and it freezes. I tried to boot again and a bunch of commands come up with switching to high resolution mode at the end. Tried seperatly running my ubuntu har drive. Same thing. Trie seperatly booting my win xp hard drive. It comes up and about 5 min after it freezes and goes to the ble screen of death. I switched the cable the connected the hard drives to the mother board 3 times(had thre different cables laying around) After i switched cables i started ubuntu and it started and i surfed for a bit on firefox then it just froze and wouldnt start at all after word. Same thing for winxp. booted but blue screen of death afterward. I tried to get an av for ubuntu thinking it may be that but i cant get to that download page. Same with my win xp. I cant even get my programs running on there. Thats about as detailed as i can get so can someone please help me
 
> **sccrstvn93 said:**
> Try booting from a live cd. Sounds like it could be a hardware problem.
 
yeah i think i got a bad cpu, i did a mem test with ubuntu and everything failed. But i just ate dinner and did another mem test and everything passed. so wtf. idk. will report back in  a few

---

### Post by blazemore on 2009-11-16
Boot from a liveCD and do
```
sudo fsck -A -ay
```

---

### Post by Ceiber Boy on 2009-11-16
OK, what ever the problem it is important to remember that the most important thing is not the machine or the operating system by your data, the forst thing i would do is boot with a liveCD, and salvage what you can on an flash or external HDD or burn to disk if possiable.

then once your happy your data is safe remove the HDD and install it into another computer and see if it is appropriable, if it is it would indicate that the fault is in your first machine, use the same principle to isolate the fault.

Good luck

---

### Post by Mag1cN1nja on 2009-11-16
> **Ceiber Boy said:**
> OK, what ever the problem it is important to remember that the most important thing is not the machine or the operating system by your data, the forst thing i would do is boot with a liveCD, and salvage what you can on an flash or external HDD or burn to disk if possiable.

then once your happy your data is safe remove the HDD and install it into another computer and see if it is appropriable, if it is it would indicate that the fault is in your first machine, use the same principle to isolate the fault.

Good luck

Can't even boot from a live cd it just freezes
every time.even when i try to run linux I installed on my jump drive it won't load anything. Wouldn't be the first time I lost over 20 gigs of music

---

### Post by Mag1cN1nja on 2009-11-16
Bump. I stil need assistance. I'm using an ippod touch for crying out loud

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Sounds like the RAM might be bad... or worse. The post above that said try the drives in another PC is a good idea. Try also re-seating the RAM with the PC shut off and the power cord out. Did your PC come with a diagnostic disk? If you have more than 1 RAM stick try booting with only one in... if no good then try another. Also try each one in a different slot.

---

### Post by Mag1cN1nja on 2009-11-16
Can't try hdd in another one cause I don't have a a another one to do that with. Ill try the RAM cards

---

### Post by Mag1cN1nja on 2009-11-16
Just pulled one of my ram cards out and guess what, my computer is working, its only been 5 min so ima wait to see what happens

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Sounds like it might be bad but keep testing and see. Try running memory intensive programs and see if it triggers anything. If not... you might still want to try the other chip and see what happens. Could still be a problem with the seat perhaps.

---

### Post by Mag1cN1nja on 2009-11-16
256 mb of RAM is soooooo slow, omg i hate it

---

### Post by JonRohan on 2009-11-16
I'd run a backup first. :p

---

### Post by Mag1cN1nja on 2009-11-16
> **JonRohan said:**
> I'd run a backup first. :p

dont have a backup, i reseated the second ram card and now it runs like it never had a problem, what should i do to check for problems?

---

### Post by JonRohan on 2009-11-16
> **Mag1cN1nja said:**
> dont have a backup, i reseated the second ram card and now it runs like it never had a problem, what should i do to check for problems?

You should have a backup in case your drive dies etc. 

I think you have found the source of your problem. If the RAM stick is new RMA it.

---

### Post by Mag1cN1nja on 2009-11-16
> **jonrohan said:**
> you should have a backup in case your drive dies etc. 

I think you have found the source of your problem. If the ram stick is new rma it.

rma?

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Means to tell the vendor it's broke and get it replaced via the warranty. The exact acronym words escape me at the moment but if it crashes again contact corsair or whoever made the chips and get them replaced. If not under warranty then you will have to acquire a new one by other means.

---

### Post by Mag1cN1nja on 2009-11-16
> **Sin@Sin-Sacrifice said:**
> Means to tell the vendor it's broke and get it replaced via the warranty. The exact acronym words escape me at the moment but if it crashes again contact corsair or whoever made the chips and get them replaced. If not under warranty then you will have to acquire a new one by other means.

i bought my computer used, it was built by a tech person at a Christian thrift store lmao, i needed a computer desperately, and they were sellin em cheap. i replaced the hard drive so far and the disc drives and the cables. time to replace the ram

---

### Post by blazemore on 2009-11-17
Any idea what type of RAM is uses?
RAM is cheap as... well, chips nowadays.

Have a look on ebuyer

I got a 4gb kit for about £40 six months ago, but your PC might not physically take that type of RAM, so check what type you have first.

---

### Post by Ceiber Boy on 2009-11-17
if it is a hardware fault (which it sounds like) it is good news as as your data is safe, providing the fault is not with the HDD, if it is you have two options.

1, order a new computer.

2, pay a lot of money for a specilist to open your HHD and perform magnetic data recovery.

Good Luck.

---

### Post by Mag1cN1nja on 2009-11-17
well next day, im running my main hard drive no prob. My win xp wont load still. What tests can i run on ubuntu to test everything. and i think i deleted one of the software sources so could someone help me with that

---

### Post by Mag1cN1nja on 2009-11-17
just a bump to if ne one is there

---

