---
title: "Can't Restore Backed Up Files/Path Name Too Long"
date: 2011-04-28
forum: General Help
---

### Post by cfree220 on 2011-04-28
Hi,

Today I backed up my home folder and performed a clean install of Ubuntu 11.04. When I started restoring my files, I encountered several errors indicating that the file could not be copied due to the length of the filename. 

If I recall correctly, I was using ext3 for 10.10, and am now using ext4. Could this cause the problem?

What other information might I provide?

---

### Post by cfree220 on 2011-05-03
bump

---

### Post by dcstar on 2011-05-04
> **cfree220 said:**
> Hi,

Today I backed up my home folder and performed a clean install of Ubuntu 11.04. When I started restoring my files, I encountered several errors indicating that the file could not be copied due to the length of the filename. 

If I recall correctly, I was using ext3 for 10.10, and am now using ext4. Could this cause the problem?

What other information might I provide?

[LIST=1]
[*]What was used to back it up?
[*]Was it backed up to a Linux filesystem?
[/LIST]

---

### Post by cfree220 on 2011-05-10
Hi,

It was backed up manually by copying my home folder to an external drive, which was formatted as ext3.

---

### Post by SecretCode on 2011-05-10
The length of **filenames** should be max 255 on ext3 and ext4 (256 on ext4, perhaps). **Path** names do not have a limit afaik. In any case, it would be odd to have a *lower* limit on a new install with ext4.

What's the exact error? In the thread title you have "Path Name Too Long", in the OP, "length of the filename".

I'm suspecting this message is arising from some other cause.

---

### Post by cfree220 on 2011-05-10
Error while copying "15 - Mozart, Wolfgang A...cher Narr seing.flac".

There was an error copying the file into /home/cfreeman/Music/Mozart/Volume 27 - Bastien und Bastienne/Disc 1.

Error opening file '.home/cfreeman/Music/Mozart/Volume 27 - Bastien und Bastienne/Disc 1/15 - Mozart, Wolfgang Amadeus - Recitativ - Dein Trotz vermehrt sich durch mein Leiden - Dialog- Und sollte ich wohl ein solcher Narr sein.flac': File name too long

---

### Post by tredegar on 2011-05-10
You could try```
cd /media/device/.home/cfreeman/Music/Mozart/
cp [COLOR="Red"]"Volume 27 - Bastien und Bastienne/Disc 1/15 - Mozart, Wolfgang Amadeus - Recitativ - Dein Trotz vermehrt sich durch mein Leiden - Dialog- Und sollte ich wohl ein solcher Narr sein.flac"[/COLOR] /destination/directory 
```
And that's one *ugly* filename ;)

---

### Post by SecretCode on 2011-05-10
Many many music files end up with names like that!

cfree220 - what are you using to do the copy? cp? rsync? A GUI? 

Are you **sure** :) there are no fat32 or ntfs volumes involved here?

---

### Post by cfree220 on 2011-05-10
Using a GUI. There are no fat32 or NTFS volume here. I don't use Windows on the computer or drive in question. Both are ext.

---

### Post by tredegar on 2011-05-10
> Using a GUI.
Well, did you try using the terminal commands, as I suggested at post No. 7?

If you receive error messages, please post them *verbatim* and not just "it didn't work".

---

### Post by SecretCode on 2011-05-10
> **cfree220 said:**
> Error opening file '.home/cfreeman/Music/Mozart/Volume 27 - Bastien und Bastienne/Disc 1/15 - Mozart, Wolfgang Amadeus - Recitativ - Dein Trotz vermehrt sich durch mein Leiden - Dialog- Und sollte ich wohl ein solcher Narr sein.flac': File name too long

Does it really begin with a "."? Nothing wrong with that, but looks odd. What is the full path to that file, on the backup volume?

---

### Post by The Cog on 2011-05-10
I'm wondering if the comma in the filename is messing a command interpteter up somewhere.

---

### Post by Tomkit on 2012-02-26
Dear , 

Here is the solution of your problem. Get this software and your problem will be resolved. I have used this software and this rectified my problem of long file name in windows..

[http://LongPathTool.com](http://LongPathTool.com)

---

