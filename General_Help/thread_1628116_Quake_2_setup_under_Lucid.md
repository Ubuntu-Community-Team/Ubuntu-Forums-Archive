---
title: "Quake 2 setup under Lucid"
date: 2010-11-22
forum: General Help
---

### Post by groping_blindly on 2010-11-22
Is it possible to run ID software's Quake 2 under Lucid 10.04, and if so, how?

I've been passing a sleepless night by trying to do so with this how to:

[https://help.ubuntu.com/community/Games/Native/Quake2#Comments](https://help.ubuntu.com/community/Games/Native/Quake2#Comments)

But it's a bit out of date.  I've been following it to the letter as much as I can, but have had to make a few changes.  For example, I had to change all references in the how-to from '/cdrom' to '/media/cdrom0' to make it work that far.  Another oddity was that the tar xvzf . . . command in the 'binaries' section of the how-to kept throwing errors because permission to unpack the tar.gz was denied for some - but not all - of it's contents.  So I unpacked the tar file with archive manager instead and that seemed to work.  Then none of the commands in the 'launcher' section worked - I kept getting 'permission denied' errors.  Turns out that the directory created by the previous instructions was read only.  So I sudo-ed in as root and changed the permissions, then un-sudoed again.  That allowed me to run the echo commands, but now the last hurdle - when I run 'quake2' at the command line, I get a 'command not found' error.  Clearly I've not succeeded at creating the launcher.

No prizes for guessing I don't really know what I'm doing here.  Maybe I've just made a simple mistake that I don't know how to spot.

Has anyone successfully installed Q2 under Lucid using this tutorial or another one they could point me too?

By the way, I do have the original Q2 cd that's been hanging around since my Windows days, in case that wasn't obvious.

---

