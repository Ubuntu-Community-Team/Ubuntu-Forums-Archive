---
title: "Deleting Folders which contain no mp3's"
date: 2010-11-13
forum: General Help
---

### Post by roswell1211 on 2010-11-13
Hi,
I need a little bit of help  I'm pretty new to Ubuntu and it might not be possible to do what I want to do here. First I'll explain the situation.

Throught trying to tidy up my mp3 collection usign various pieces of software I now have a folder structure that I want (My Music\Artist\album\track)
However, in the process, I have been left with lots of other folders - these have had the mp3's removed but they contain other files (artwork, playlists, .nfo files - that kind of thing).

What I'm looking for is either a premade solution or help with a script to do the following : 
Check all folders in my music folder, if the folder doesn't contain any mp3's then check the subfolders, if none of them contain mp3's then delete the main folder (regardless of what otehr files are within it).

It seems like I should be able to do this - but not sure how.

Incidentally, I have backed up my music folder to an external disk - so I can't do any lasting damage:-)

---

### Post by kidders on 2010-11-14
Hi there,

Something like this ought to do the trick ...

```
find /path/to/mp3s -type d | while read -r f; do [ -z "`find "$f" -type f -iname "*.mp3"`" ] && rm -iRf "$f"; done
```

It's a bit inelegant, but here's a brief explanation ...

[LIST=1]
[*]**find /path/to/mp3s -type d** - Create a list of directories below /path/to/mp3s.
[*]**while read -r f** - Iterate over each one.
[*]**[ -z "`find "$f" -type f -iname "*.mp3"`" ]** - Test if there are no MP3s below a given subdirectory.
[*]**rm -iRf "$f"** - Delete the directory, all of its subdirectories & their contents.
[/LIST]

Some notes ...

[LIST]
[*]The obligatory warning to future readers: **The above command is destructive ... It will result in wholesale deletions. [COLOR="Red"]Never run it as root.[/COLOR]**
[*]If your MP3 collection is very large, this method may take some time to run. I went for easy to type rather than easy to execute ... My suggestion unnecessarily re-scans subdirectories a few times, which will slow it down a bit.
[*]Be sure to get all the spacing & quotes _exactly_ right.
[*]For safety, I've included an "i" in **rm -iRf** ... Once you're confident the command really does what you want, remove it, so you don't have to confirm every single deletion.
[*]You may get some "file not found" messages while the loop runs. You can safely ignore them ... It just means something lined up for an MP3 scan (step 3) has already been deleted.
[/LIST]

Anyhow, I hope that helps.

---

### Post by roswell1211 on 2010-11-14
Thanks - I'll give it a shot.

---

### Post by sleash78 on 2012-06-08
kidders's command works

---

