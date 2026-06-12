---
title: "unable to copy files from external disk to windows machine"
date: 2012-04-18
forum: General Help
---

### Post by kurja on 2012-04-18
I have an external ntfs hdd that contains amongst other things my music collection. I usb-connected the external drive to a windows computer and proceeded to copy that music folder with all it's files there, but a few folders - that were recently created by Rhythmbox when extracting music from cd's - refused to get copied, XP just prompted an error saying that "files not currently available". I was able to browse them in XP just fine, but couldn't do anything to them. In Ubuntu I don't see how they would be different from all the other files that were successfully copied.

Any ideas on what might be going on?

---

### Post by papibe on 2012-04-18
Hi kurja.

Have you tried running a check disk on Windows?

Just and idea to discard hardware problems, or corrupted directories and files.

Regards.

---

### Post by strask on 2012-04-18
I don't know Rhythmbox so this might be a stupid idea, but maybe the files in question are really symbolic links to some place not on the removable drive?

---

### Post by kurja on 2012-04-19
> **papibe said:**
> Hi kurja.

Have you tried running a check disk on Windows?

Just and idea to discard hardware problems, or corrupted directories and files.

Regards.

I have not, but the files work just fine on a ubuntu computer.

---

### Post by kurja on 2012-04-19
> **strask said:**
> I don't know Rhythmbox so this might be a stupid idea, but maybe the files in question are really symbolic links to some place not on the removable drive?

That occured to me as well, but they seem to be there (and not just links). I don't think windows would know to report that a file is not found at the other end of a symlink?

But taking another look at those files, there seems to be something going on about them, rhythmbox reports the durations all wrong... totem handles them just fine though. hmmm.

---

### Post by HiImTye on 2012-04-19
does rhythmbox report durations of 0:00? if so it could be a permissions problem

---

### Post by kurja on 2012-04-19
> **HiImTye said:**
> does rhythmbox report durations of 0:00? if so it could be a permissions problem

No, it reports a two minute-something file to last over 9 minutes. When played it seems to contain the next few songs as well! That is, if I skip forward to 3 minute mark I'm hearing the next song.... In Movie Player it's just that one song in one file - but on a closer look, Movie Player doesn't get the duration entirely right either, the number flickers back and forth as if the program wasn't sure how long it is. Playing in Rhythmbox it skips to the next track after the "correct" duration, even as it shows that there would be seven minutes left in the track. Super weird.

---

### Post by dcstar on 2012-04-19
> **kurja said:**
> I have an external ntfs hdd that contains amongst other things my music collection. I usb-connected the external drive to a windows computer and proceeded to copy that music folder with all it's files there, but a few folders - that were recently created by Rhythmbox when extracting music from cd's - refused to get copied, XP just prompted an error saying that "files not currently available". I was able to browse them in XP just fine, but couldn't do anything to them. In Ubuntu I don't see how they would be different from all the other files that were successfully copied.

Any ideas on what might be going on?

Check the file names for illegal characters, what works on one OS does not necessarily work on another.

---

