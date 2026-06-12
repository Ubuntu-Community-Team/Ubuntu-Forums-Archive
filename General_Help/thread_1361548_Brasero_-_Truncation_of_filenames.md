---
title: "Brasero - Truncation of filenames"
date: 2009-12-22
forum: General Help
---

### Post by muteXe on 2009-12-22
Hi,
I burnt a load of files onto a cd last night using Brasero (on Hardy). I've just put the CD into my works laptop (windows xp) and ALL folders and filenames have been truncated to about 7 or 8 characters.
It'll be interesting to see if the filenames look like this when i put it back in one of my linux boxes tonight, but if it continues to do this I don't think i'll be able to use it anymore.  
Has anyone else experienced this at all?  I'm using Hardy.
Cheers,
mute

---

### Post by muteXe on 2009-12-22
Nevermind - it's a known bug.

---

### Post by StuartN on 2009-12-22
> **muteXe said:**
> Nevermind - it's a known bug.

I was hoping someone would post as I only use Brasero for burning ISO images, and that seems to work fine. The issue might relate to the filing system on the burned CD - for compatibility (i.e. DOS 8.3 naming) some filesystems use 8 character names, or 7 plus a truncation marker (like ~), and also truncate long paths. There does not seem to be any user setting in Brasero to choose the filesystem.

GnomeBaker is one alternative. As far as I know, the data CD mode writes proper filenames and paths with sensible limits.

---

### Post by geirha on 2009-12-22
Another alternative, while you wait for the bug to get fixed, is to use nautilus, the file browser. Just pop in an empty CD and choose to "do nothing" when/if that dialog pops up. The CD will then be listed as "Empty CD" in the left margin of nautilus windows. Drag the files you want to burn onto it, and when done, open the CD and click the burn/write button.

---

### Post by muteXe on 2009-12-22
AH ok. Cheers both. I just been used to using brasero. Maybe i've not noticed this problem before cuz i burn a lot of iso's instead of everday files.  I'll try the CD in both my ubuntu machines tonight and post back with results if anyone's interested.
Might look at gnomebaker as well.
Cheers again,
mute

---

### Post by Scoobin on 2010-08-02
Thanks for the tip geirha that seems to have worked for me. You'd think between Brasero and GnomeBaker they could get it fixed. It seems like a major bug if you ask me (I previously used GnomeBaker and it clipped all my filenames).

---

### Post by warthog10 on 2010-08-02
> **Scoobin said:**
> Thanks for the tip geirha that seems to have worked for me. You'd think between Brasero and GnomeBaker they could get it fixed. It seems like a major bug if you ask me (I previously used GnomeBaker and it clipped all my filenames).


That tip works for me also.  It looks like this bug is around 2 yrs old?! Lame.

---

### Post by Scoobin on 2010-08-03
OK so I managed to burn the disc OK, but when I play it in my car MP3 player, the tracks are all in random order for some reason. The filenames are ordered correctly so I have no idea why this happens. I used to use Windows when I previously wrote my music discs (without this problem), but I'd like to think I'd be able to do it with Lucid.

---

