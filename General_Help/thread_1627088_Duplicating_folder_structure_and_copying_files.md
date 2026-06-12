---
title: "Duplicating folder structure and copying files"
date: 2010-11-21
forum: General Help
---

### Post by BuddyThirteen on 2010-11-21
I'm looking for some way to search a given directory, copy its folder structure to another given directory, and copy from the original only certain files into the newly created directory.

Vague, I'm sure. But here's what I'm actually looking for:
My music player won't display album art without a "cover.jpg" image in each folder where the files are, but I have Rhythmbox set to only copy the top rated songs. Each file does have its cover embedded in it, but there's also a cover.jpg in each folder.

So I'd like to let Rhythmbox handle the actual song copying, and then have a script or something that I can run that will scan my onboard music directory for cover.jpg files and then place them in the appropriate folders within my music player's folders. Obviously I can't just copy my onboard music directory, or I'm getting *every* song, not just the top-rated, which defeats the purpose of syncing at all.

Thanks in advance!

---

### Post by HermanAB on 2010-11-21
Howdy,

Rsync is your friend.  Read the man page for the --exclude option.  It is frequently easier to specify what you don't want to copy, than what you do want to copy.

---

### Post by BuddyThirteen on 2010-11-21
Thanks, I think that should work. Now I just gotta figure out how to do it.

I tried:
```
rsync -r -u --exclude=*.ogg /media/Archive/Music /media/0123-4567/MUSIC
```And nothing happens. No error messages, but no copied files, either. Does the destination folder have to already exist, or will it create them as it finds the files?

Oh, wait! I forgot trailing slashes. It was creating a new music directory *in* the music directory. Silly. Okay, that totally worked. Thank you thank you thank you! Now, even music that I haven't rated yet will have a cover.jpg waiting for it on the music player.

The final command I used was:
```
rsync -r -u -v --exclude=*.ogg /media/Archive/Music/ /media/0123-4567/MUSIC/
```

---

