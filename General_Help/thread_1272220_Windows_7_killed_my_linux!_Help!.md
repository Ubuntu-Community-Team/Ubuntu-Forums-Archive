---
title: "Windows 7 killed my linux! Help!"
date: 2009-09-21
forum: General Help
---

### Post by longreach on 2009-09-21
Hi all,

I have no doubt most of you out there will shake your head at my total noob-ness and I am scared I have lost my ubuntu install.

Here is the story:

I had a go at installing Windows 7. I made a partition to put it to (used gparted to split linux partition) and installed it. When it rebooted it came up with a "Operating System missing" error on the screen. I played around with it for a while before giving up. I deleted the windows partition, re-merged everything into 1 partition (except the swap) and put the boot 'flag' onto the primary, ubuntu partition. Which is where I assume it always was.

Now, I still get the "operating system missing" error, which I think is a windows 7 error. What the hell do I do? I'd prefer not to reformat....BIG TIME.

---

### Post by triplesick on 2009-09-21
you'll be fine bro.  i believe this is something to do with windows being a totalitarian dictator and destroying grub (the boot loader); try looking into the ubuntu alternative install CD, which has a restore broken system option.

and i am certain that whoever answers after me will have a more detailed answer; i simply wanted to post and reassure you that your system will be okay.

---

### Post by Meow27 on 2009-09-21
search recovering grub with a livecd or something of the sort

when you install windows, it replaces grub with another master boot record (mbr) which determines which operating systems boots.

this will work assuming you didnt screw around with your ubuntu partition

---

### Post by longreach on 2009-09-21
Thanks guys! I downloaded super grub for USB & it had a "fix MBR for Linux" option.

[http://www.supergrubdisk.org](http://www.supergrubdisk.org)

Was very easy to understand, and did most of it automatically. I am back online! Thanks again!

:guitar:

---

### Post by Dullstar on 2009-09-21
I think all Windows 7 will be good for is being at least not as bad as XP.

---

### Post by longreach on 2009-09-22
> **Dullstar said:**
> I think all Windows 7 will be good for is being at least not as bad as XP.

HAHA GOLD. I agree. A few friends reckon it's pretty good. I forgot, they don't know linux goodness. :)

---

### Post by fuzzyk.k on 2009-09-22
while in prefer Linux systems to windows , let us not forget Linux wouldn't have developed this far if it wasn't for the need for a windows alternative, no offence ment

---

