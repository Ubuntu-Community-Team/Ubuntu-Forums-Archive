---
title: "Ext4 fregmentation"
date: 2009-12-02
forum: General Help
---

### Post by potam on 2009-12-02
Hello all,

I am running Karmic Koala, and I have an encrypted home (ext4).
The fregmentation of the home partition is 14%. I have huge number of mp3 files, when I delete them, fregmentation goes down to 4%. Free space on this partition is 90%.

I tried moving all the mp3 files to an external hdd, delete from the home, and copy back. I got the exact same fregmentation as before.

How can I reduce fregmentation? (I need to do that, sometimes I got delays while listening mp3)

---

### Post by Kilz on 2009-12-02
Per Wikipedia and other links the defragment tool for ext4 isnt in the mainline kernel yet. There are patches, if you feel up to the task and are willing to risk your data on unproven code. [Here is more info on it.]("http://lmgtfy.com/?q=ext4+fragmentation")

---

### Post by 3rdalbum on 2009-12-02
> **potam said:**
> Hello all,

I am running Karmic Koala, and I have an encrypted home (ext4).
The fregmentation of the home partition is 14%. I have huge number of mp3 files, when I delete them, fregmentation goes down to 4%. Free space on this partition is 90%.

I tried moving all the mp3 files to an external hdd, delete from the home, and copy back. I got the exact same fregmentation as before.

How can I reduce fregmentation? (I need to do that, sometimes I got delays while listening mp3)

The seek time for a hard disk is much, much less than the buffer time for a typical MP3 player. In other words, when you go to play an MP3 it will put probably 5 seconds into RAM first before starting to play. Hard disk seek times are measured in milliseconds.

If you're talking about the delay at the beginning before the file starts to play, well heck I have that too. It's not a fragmentation issue.

If that's your only "symptom", then you've got nothing to worry about.

---

### Post by potam on 2009-12-02
No, the playing starts normally, and some of the mp3s (I guess the fragmented ones) have delays during the playing.

---

