---
title: "I have a dumb question about Raid"
date: 2010-01-26
forum: General Help
---

### Post by cptrohn on 2010-01-26
Ok, I will admit right from the start that I have absolutely no clue how it works and only know a very small bit about it.  I only ask because I am considering a a laptop build using this hardware from OCZ...  [http://www.newegg.com/Product/Product.aspx?Item=N82E16856172010](http://www.newegg.com/Product/Product.aspx?Item=N82E16856172010) and it has 2 HD bays... (big selling point for me since I am considering this for a desktop solution to save space, plus you can run the core2 quad mobile processor with this)...  So with the 2 HD bays would Ubuntu just see one of the bays as an external HD type of storage?  but with the Raid it would see both drives as one device correct?  And how hard is it to set up a Raid in Ubuntu?  Anything I would need to watch for hardware wise?

---

### Post by audiomick on 2010-01-26
Hallo.
Without raid,  you would have to create a partition ( or a couple, if you want) on the HD that you don't do the install to, and specify a mount point for it during the install.

With Raid, your system will only see one drive. There is an expalantion of the different RAID levels here
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Raid can be tricky with Ubuntu.
here are a couple of links to things in the Ubuntu documentation.
I think the first one is the one that is relevant.
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by t4thfavor on 2010-01-26
RAID has alot of different modes, but yes with RAID you will only see one drive in the OS if you set it up correctly.

This will be software raid, because I don't think the Laptop has built in RAID. 


Do alot of research on your desired config before you proceed, as messing this up has potential to lose you lots of time and data.

---

### Post by cptrohn on 2010-01-26
Thanks for all the help folks!

In the specs for this machine it says it supportsw Raid 1 and Raid 0.  I don't know what this means of course, but thanks to the great links provided I have a starting point at least to consider!  


Which one of those works best with Ubuntu?

---

### Post by cptrohn on 2010-01-26
But thinking about it just creating a mountpoint and not using Raid doesn't seem like that bad of an option either I guess.

---

### Post by audiomick on 2010-01-26
> **cptrohn said:**
> In the specs for this machine it says it supportsw Raid 1 and Raid 0.  I don't know what this means of course, 

It may have a real hardware RAID controller, but I rather suspect that the second link I posted would be relevant. The one about fake raid.

---

### Post by cptrohn on 2010-01-26
> **audiomick said:**
> It may have a real hardware RAID controller, but I rather suspect that the second link I posted would be relevant. The one about fake raid.

After reading those links, thats what I think too....

---

