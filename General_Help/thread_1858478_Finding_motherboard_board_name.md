---
title: "Finding motherboard board name"
date: 2011-10-12
forum: General Help
---

### Post by knowram on 2011-10-12
I am thinking about upgrading my CPU and am trying to see if the one I am looking at is compatible. I am looking at the Intel I5-2300. When i try and use Intel's site to see if the chip is compatible i need to know my board name. this is my first time trying to do something like this so I am not sure how to figure out my board name. I am running the newest version of ubuntu desktop. The Intel web site I am trying to use is [http://processormatch.intel.com/CompDB/](http://processormatch.intel.com/CompDB/)

Can someone please help me out.

---

### Post by cryptotheslow on 2011-10-12
Is it a desktop machine? If so - why not just read the make/model printed on the motherboard itself?

---

### Post by Mark Phelps on 2011-10-12
Also, you need to find the Version number -- it's printed on the motherboard somewhere.  Different versions tend to support different CPUs, the more recent the version, the more modern the CPUs.

---

### Post by CharlesA on 2011-10-12
Thought you could cat /proc/cpuinfo or something like that.

EDIT: Found that you can get a load of info by running this:

```
sudo dmidecode
```

Source: [http://www.webhostingtalk.com/showthread.php?t=440128](http://www.webhostingtalk.com/showthread.php?t=440128)

---

### Post by oldfred on 2011-10-12
This will create a HTML page of your system. But may not give version numbers.

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
Some more info:
udevadm info --export-db > file.txt

---

### Post by The Sorrow on 2011-10-12
most boards have model numbers on them. find that or google the make/model of the pc and find the board.

---

### Post by Mark Phelps on 2011-10-13
> **The Sorrow said:**
> most boards have model numbers on them. find that or google the make/model of the pc and find the board.

While that's true, it won't provide the Version number of the specific board -- and, different Versions support different CPUs.

For example, I have a Gigabyte motherboard, version 2.  It supports AMD3 CPUs up through the 1090T.  While the AMD 1100 is will plug into the CPU socket on this board, it will not work because that requires version 3 of the board.  And, while there is a BIOS upgrade that should allow this version to work with that CPU, I tried the upgrade and it crashes the board.

So, version is important when selecting newer CPUs.

---

### Post by collisionystm on 2011-10-13
if you have windows installed anywhere, run speccy. google it.

---

