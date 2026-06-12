---
title: "Trouble with MIME types..."
date: 2010-10-14
forum: General Help
---

### Post by earthmeLon on 2010-10-14
I am writting a script to allow uploading of certain files.  I want to limit the files by their filename and mime type, and by making sure the two match up.

The first thing I need to do is make sure I've got all the mime types I need added.  I have never done this before, but I understand that 'file' (which is what PHP's mime-type finding is based off of) uses magic databases that tell at which point in the file should have signatures of the filetype.

My trouble started when I was unable to determine the filetype of any of my video files.  Currently, I have some .MOV and .MP4 files that I am using to test.

```
file --mime VID00003.MP4 
VID00003.MP4: application/octet-stream; charset=binary
```

I noticed a very generic listing for the file, so I tried researching how to add the files myself.  After reading tons of useless pages, I came across a program called assoGiate (available in the repos).  It is a GUI based tool to add/edit/remove mime types.  I was unable to add a custom MP4 mime-type because it already existed and after checking my file with gHex, I realized that my file does indeed contain the information needed to flag it as MP4...

My file
```
....ftypMSNV.).FM
```

Third entry for MP4's
```

type: string
priority: 50
value: ftypMSNV
Offset: 4
```

So, now, I am just really confused about all of this.
Since this was already in my System DB, I haven't needed to, but have indeed run **# update-mime-database /usr/share/misc/magic**

Any help or leads will be greatly appreciated.
Thanks :D

---

### Post by jkxx on 2010-10-14
I am not sure about a database of mime types, but if you know what types of files will be uploaded you can write the validation code yourself.

As an example, the file you used has the signature "ftypMSNV" near the beginning - you could code a simple function to check for that string in the first 20-100 bytes of the file when the extension provided is mp4.

Make sure you check that an ID string is in the file but do not expect it to be at a particular location within the file. Most of these files have tagging info and varying length headers so the signatures can really be anywhere in the file.

If you want to be more thorough there's probably a way to feed the test file into a player (mplayer,vlc, etc) and have the player validate the file for you and return a result indicating whether it thinks the file is legit. I'd discourage that though because people could upload shellcode or similar and get your test system hacked.

---

### Post by earthmeLon on 2010-10-14
Thank you for your suggestion, but the whole purpose of having MIME types and system functions that use them (ie: file) is so that people don't have to re-invent any wheels.

Also, I do not have every file type available and even if I did, many of them have different variations of signatures. This compilation has (in theory) already been done for me, and I would like to take advantage of the system in place, as well as learn more about it for future endeavors.

---

### Post by earthmeLon on 2010-10-14
I've noticed that Nautilus knows what type of file they are.  I was using assogiate to see what my mime-type rules were, but it and nautilus seem to use something different than that which file is using.

---

### Post by earthmeLon on 2010-10-14
Well, I am now trying to figure out how to export gnome mime-types (That both Nautilus and assogiate are aware of) to a magic mime file. 

```
# Magic local data for file(1) command.
# Insert here your local magic data. Format is described in magic(5).
#I really hope I don't have to do this...
20      string          mp4            \b, MPEG v4 system, part 12 revision
!:mime  video/mp4

```
```

file -m /etc/magic -ib VID00004.MP4 
video/mp4; charset=binary

```

I guess that's progress, but I'd really rather export gnome's list somehow.

Any information would be greatly appreciated :D

---

