---
title: "Strange Rhythmbox Import Errors"
date: 2009-07-23
forum: General Help
---

### Post by adempewolff on 2009-07-23
I am trying to figure out if I actually have a bug here (worthy of launchpad) or was just being stupid.

I recently put a symbolic link in my ~/Music/ folder that pointed to the "My Music" folder on my windows partition.  Turns out this was a bad idea because Rhythmbox tried to reimport my entire library which had previously been imported from the "My Music" folder as it was mounted in /media/.

However the bug I then encountered was that when it tried this it failed at importing the vast majority of these files, most notably the .wma files (which already existed in the library previously).  I got an increasing list of import errors most of which said "the stream is encrypted and decryption is not supported" (some others said something about 'smil' but these all looked like random wmplayer playlists and such, not music files).  Furthermore a box would repeatably show up asking me to search for suitable codecs, would fail and then another one would show up.  If I pressed cancel rather then searching for codecs, the box would just pop up again.  I would usually have to force quit at this point because Rhythmbox would not exit (probably because it was still trying to import the rest of my music library.

At first I thought my restricted codecs had just been deleted/corrupted so I reinstalled them all.  I then tried playing the files in mplayer which was successful and keyed me in to the fact that something else was amiss.  I then remembered the symbolic link I had created and deleted in and restarted Rhythmbox.

At this point Rhythymbox now had about 500 missing files, which turned out to be duplicates suggested that certain files/filetypes imported successfully.  Of course at the time I was just trying to fix the problem so I didn't note the filetypes of the successful imports ](*,)

Anyway I have no problem anymore, and realize how stupid it was putting that link in a monitored folder but I am just wondering why Rhythmbox had these troubles importing the files and if it is a bug worth reproducing and putting on launchpad?

---

### Post by Strongman332 on 2009-07-23
I dont think its a bug in rythembox. 

is your windows partition a fat or ntfs file system.

Ntfs can have problem with linux at times

---

### Post by adempewolff on 2009-07-23
ntfs, but all the files currently in the library are on it.  additionally I tried importing some more files off that partition that weren't in the library after fixing the error and they worked fine.

I'm not certain I'm explaining this very well... 

it was just when Rhythmbox tried import files from the symlink I put in my ~/Music/ directory.  So it tried importing files that were already in the library but now had another possible path to them because of the symlink.

eg:

song.wma is in my music library, the path for it is /media/disk/Documents and Settings/user/My Documents/My Music/song.wma


I put the symlink in, open Rhythymbox and now it tries importing the same song.mp3 from the path /home/user/Music/My Music/song.wma

it fails in doing so and gives the message "the stream is encrypted and decryption is not supported" and floods me with windows asking me to searc hfor codecs

I'm glad it wasn't successful in uploading a second copy of every file in my library I am just concerned about why it is giving these particular errors.


edit: in case you wonder why some of my music uses .wma, way back when (before linux) I didn't notice it was the default encoder for awhile and never found a nice enough batch converter so it wouldn't be a pain to convert them all to something a little less proprietary.

---

### Post by Strongman332 on 2009-07-23
well in that case it maybe a bug or maybe linking is not playing well with ntfs.

---

### Post by adempewolff on 2009-07-23
I just did some digging around on launchpad and found this: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/204566](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/204566), which addresses how it kept searching for codecs and made Rhythmbox useless.

It doesn't address though why this only happened with files when they are imported for the second time through a symlink that worked otherwise when the normal path is used. 

I think I'll put this in launchpad tomorrow unless anyone has some insight.  Definitely a low importance bug, but a bug nonetheless.

---

