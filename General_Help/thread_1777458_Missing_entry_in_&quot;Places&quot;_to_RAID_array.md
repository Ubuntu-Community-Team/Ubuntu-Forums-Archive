---
title: "Missing entry in &quot;Places&quot; to RAID array"
date: 2011-06-07
forum: General Help
---

### Post by inhumangeek on 2011-06-07
Almost complete rookie here!

I've just re-installed 11.04 and noticed that my RAID array does not appear as an entry under "Places". In the previous installation, and in the LiveCD boot (which I'm using now), it appeared as en entry which I could click on to mount.

In Disk Utility (and Gparted I think - not 100% sure) I can see both hard drives, and I can see the SIL controller that they come under, but I'm just not getting the array showing up in "Places", and the array checks out OK in BIOS. Using the Live CD, the array appears as an entry in /dev/mapper but when using the main installation all I can see in this location is "control".

The array is a psuedo hardware array, being controlled by the SIL controller on my motherboard. 

Grateful for any suggestions I can try to convince Ubuntu to see the array.

Thanks!

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums :-)

Run this command in the terminal on your Ubuntu install to find the arrays:

```
sudo dmraid -r
```If this recognizes the array you should be able to activate them with this:

```
sudo dmraid -ay
```

---

### Post by inhumangeek on 2011-06-08
Perfect thanks very much!! 

Any idea why the array wasn't activated in my current install? Perhaps one of the updates I installed removed/disabled dmraid (I had to install it)?

---

### Post by Rubi1200 on 2011-06-08
No problem, you are more than welcome :-)

Not sure why it wasn't installed, but I am glad this solution worked for you.

Good luck!

---

### Post by ronparent on 2011-06-10
I've noted that although it is present on the live cd that dmraid is not installed when the system is installed somewhere other than the raid. Is this what you are seeing?

---

### Post by inhumangeek on 2011-07-15
> **ronparent said:**
> I've noted that although it is present on the live cd that dmraid is not installed when the system is installed somewhere other than the raid. Is this what you are seeing?

Sorry for the delay. Yes, this is what I'm seeing I think.

---

