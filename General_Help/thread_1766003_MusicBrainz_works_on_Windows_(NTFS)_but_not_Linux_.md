---
title: "MusicBrainz works on Windows (NTFS) but not Linux (ext4)"
date: 2011-05-23
forum: General Help
---

### Post by nethero on 2011-05-23
I have the strangest bug I've seen yet.  

I'm using Ubuntu 10.10 and when I was tagging my music files using MusicBrainz Picard version 0.14, it trimmed a little bit of the beginning of the song.  I tried upgrading MusicBrainz, reinstalling, playing with various tagging options, sacrificing goats, and nothing worked.  I have a dual boot system and MusicBrainz has a windows client so I logged onto Windows XP.  I tagged my music files while logged onto Windows XP using the Windows version of MusicBrainz Picard (still version 0.14) and the file did not have any of the beginning deleted.  Naturally, I thought it was an annoying Linux bug and considered going back to Windows (just kidding (sort of)).  Then I realized what was causing it.  Here is where it gets weird...   

I noticed that when I tagged the music files while logged onto Ubuntu (10.10) when the music files were stored on the Linux partition (ext4), it trimmed the beginning of the song.  However, when I tagged the music files logged onto Ubuntu (10.10) when the music files were stored on the Windows XP partition (NTFS), it did not trim the beginning of the song.  In other words, the linux MusicBrainz client tags the files with no errors as long as the files are stored on my NTFS partition.  Any ideas how to fix this?

---

### Post by nethero on 2011-05-30
I upgraded to 11.04 and this issue seems to have gone away.  I never did figure out what was causing it.

---

