---
title: "Gparted - How to convert a logical partition to primary"
date: 2011-03-12
forum: General Help
---

### Post by Futa on 2011-03-12
Ubuntu is awseome. My friend was under the impression that gparted was CLI and Ubuntu would simply fail.

_Problem:_
Here's what I had, they basically needed to switch places.
C: Windows Primary (The contents of this was my boot partition)
D: Extended Logical (I wanted this to become the primary)

I googled what to do, and believe it or not it seems people really didn't have a solution besides reformatting it?

We learn from our mistakes. That's why I'm posting what I did to see if someone knows a better way!



_What I did:_
First I used an Ubuntu LiveCD or 10.04. (Not .1 oh noes)

Then I opened up gparted and shrank the extended partition so I would have enough room to move them around.

I mounted both the C: and D: partitions and copied the data over to the primary from the logical.

I deleted the logical and then moved and resized the primary!

Then I flagged the primary partition boot.

Well that's one way to get from logical to primary with your data.

Now, it's time to play repair the mbr with Windows. :P

---

### Post by Rubi1200 on 2011-03-13
There is actually a new utility that would probably have done the job for you. It is called fixparts and was written by one of the forum members here, srs5694:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

For specific questions related to the use of the program, please ask the author.

---

### Post by srs5694 on 2011-03-13
It's unclear to me what was on these partitions or why you wanted to make the change you describe. Absent that information, it's hard for me to understand why it was important to you that D: become a primary partition. The main reason to want a partition to be primary is if it's a Windows boot partition, but that clearly wasn't the case for you, since Windows can't boot from a logical partition to begin with. (There are ways to install *most of* Windows on a logical partition, but if that's the sort of configuration you had, you've probably done irreparable harm to your installation by following the procedure you did.)

If you've got some specific question about your system, you'll have to be more specific, both in asking your question and in presenting information about its current configuration. For the latter, the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) is a good resource; run it from Linux (either a regular Linux installation or an emergency boot disc) and then post the RESULTS.txt file that it produces here, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings, which will improve legibility.

---

