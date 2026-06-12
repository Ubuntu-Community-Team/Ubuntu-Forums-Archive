---
title: "Accidentally moved 10k files to the trash with rhythmbox. Any hope for me?"
date: 2011-11-14
forum: General Help
---

### Post by oakdog8 on 2011-11-14
For some unimaginable reason, Rhythmbox does not give an 'are you sure?' prompt before moving files to the trash, and offers no undo option. As a result, I accidentally moved 10k files to the trash instead of removing them from a playlist. 

The handy 'Restore Files' button in the trash does not work, because Rhythmbox decided to also strip all directories, so the folders no longer exist in their old location or in the trash. When clicking restore, it tells me there is no such folder or directory, but there is no option to create the missing directory. WTF?? Is there an option I'm missing somewhere to recreate all those directories? I see the paths are still stored in the .local/share/Trash/info directory. If not, this is possibly the dumbest error of all time.

---

### Post by hansdown on 2011-11-14
Hi, oakdog8.

I can reproduce this problem.

Would love to give a fix, but haven't found it, so far.

Good candidate, for a bug report, on launchpad.

---

### Post by nothingspecial on 2011-11-15
Hi, assuming these are music files and they are correctly tagged you may have some success with guayadeque music player and it's built in copy to feature.

I've tested this with about 200 files.

Copy or move all your files from trash to somewhere else (I couldn't get guayadeque to see hidden directories). I'd back them up also just incase something goes wrong.

In guayadeque click view > files

A new tab will open up, you may need to click the show entire file system which is the right hand button of the 3 at the bottom of the files tab.

Navigate to your music files and select them all.

Then right click and select Copy To > Por Defecto (The developer is Spanish).

This will copy all your music files into folders Genre/Artist/Album/Track

If you don't like your music organised in this way you can change how they will be arranged in guayadeque's preferences (Library > Preferences > Copy To)

---

### Post by oakdog8 on 2011-11-15
I wrote a quick python script to go through the .local/share/Trash/info directory and rebuild any directory structure in each file's trashinfo. I think it worked. I'm currently re-checking that the files were restored correctly. If it was successful, I'll post the script for others.

---

### Post by hansdown on 2011-11-15
> **oakdog8 said:**
> I wrote a quick python script to go through the .local/share/Trash/info directory and rebuild any directory structure in each file's trashinfo. I think it worked. I'm currently re-checking that the files were restored correctly. If it was successful, I'll post the script for others.

Nice!

My news sounds, a little pathetic, compared, to that.:D

If you leftclick the trash, you can leftclick each item, then the 

```
restore selected items
```

box, is usable.

Good work, oakdog8.

---

### Post by oakdog8 on 2011-11-15
It wasn't that the button was unclickable, it's that the OS didn't see the directory anymore but instead of recreating on clicking "Restore Selected Items" it it just decided it was unfixable and threw an error, leaving the file in the trash.

Luckily, my script rebuilt the directories so that when clicking "Restore Selected Items," the OS could do what it wanted to. After re-checking files, it seems that all but about 20 files restored once I rebuild the directory structure with my python script. Some of the folders now have hex characters or something instead of accented letters or foreign language letters, but applications seem to recognize them just the same. 

Here's the script I wrote in case anyone else runs into the same problem:

```

import os, re

log = open('log.directory_restore', 'a')
direct = '/home/<username>/.local/share/Trash/info'
dirlis = os.listdir(direct)
for fname in dirlis:
    f = open('/home/<username>/.local/share/Trash/info/%s' % fname, 'r')
    text = f.read()
    npath = re.search(r'Path=(.*)', text).group(1)
    filepath = '/'.join(npath.split('/')[:-1]) #Removes the filename from the path
    try:
        os.makedirs(filepath) #Recursively makes directories
    except Exception, e:
        log.write('\n\t>>Error %s in file %s' % (e, fname))
    else:
        log.write('\nCreated: ' + filepath)
    f.close()
log.close()

```Just change <username> to your username.

> **hansdown said:**
> Good work, oakdog8.
Thanks :)

---

