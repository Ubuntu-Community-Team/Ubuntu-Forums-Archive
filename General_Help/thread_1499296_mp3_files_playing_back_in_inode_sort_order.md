---
title: "mp3 files playing back in inode sort order"
date: 2010-06-01
forum: General Help
---

### Post by Dan Z on 2010-06-01
Hello I have many mp3 files I play back while driving. In  the past I burned them to a CD. To get them to play in the order I want they were named in numeric order, ie 1.mp3, 2.mp3, 3.mp3 etc. 

Then the player died and I got a new one. This unit plays back from an SD card or thumb drive. 

The problem is the files wont play back in file name order. They are playing back in inode order, which means oldest file plays first, and any new music goes to the end, I would like to mix the new ones in with the older music.

Is there a way to change inode number to match my play order, or to trick the system into assigning inode numbers in my play order?

Thanks Dan :guitar:

---

### Post by sdennie on 2010-06-01
I'm not positive about this but, doing a few tests, I think inode numbers are re-used sequentially as they are freed up.  I did this twice:

```

cp * /some/place

```

Both times the files ended up having inode numbers that, sorted, would also be in alphabetical order.  The individual files also had different, but sometimes re-used from the previous copy, inode numbers.

So, it's a brute force approach but, you could potentially just copy over your entire music library when you want to update.

---

### Post by Dan Z on 2010-06-06
Worked! Thanks for the help! dan

---

