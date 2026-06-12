---
title: "Rotate Image (Script) without changing &quot;modified&quot; date"
date: 2010-11-19
forum: General Help
---

### Post by tg3793 on 2010-11-19
Hello everyone, Joe Newbie here. *Welcome to my first script*; well sorta. I am actually modifying someone else's script and I need some help. The original script rotated image files to the left but it changed the "modified date stamp" which is something I didn't want. 

```
#!/bin/bash
while [[ -n "$1" ]]; do
    #if a file and not a dir
    if [[ -f "$1" ]]; then
        [COLOR=Blue]#the images that I copy from my cell phone don't have exif headers
        #so I am using the -mkexif switch first to match the exif information
        #to the "created date" in the .jpg file. 
        jhead -mkexif "$1"[/COLOR]

        #by default, jpegtran will only copy some
        # Exif data, so we'll specify "all"
        jpegtran -rotate 270 -copy all -outfile "$1" "$1"

        [COLOR=Blue]#Then the next line uses the -ft switch which will match the "modified date" 
        #using the exif date and time previously matched from the first line
        #of this script.
        jhead -ft "$1"[/COLOR]
        
        #clear rotation/orientation tag so that
                # some viewers (e.g. Eye of GNOME) 
                # won't be fooled
        jhead -norot "$1"
    fi
    shift
done
```
I've done batch files in DOS years ago so there are a lot of similarities of course. And I'm not looking for someone to just fix this for me but to also explain to me what I'm doing that is causing the incorrect behavior. Is there a more elegant way of doing this?

And BTW, it actually does what I'm asking it to do but only when I do something I consider quite odd.

1) I right click on the .jpg and select rotate left.
2) The file responds by flipping 180 degrees 'instead' of 90 degree counter clockwise.
3) I refresh the file manager and nothing happens.
4) I 'touch" the file with my pointer (it doesn't matter if I "touch" it with a left or a right mouse click) and it correctly orients itself.

It's important to note that the original script, before I made any edits, did not have this quirk whereas I needed to "touch" the file to get it to orient itself correctly. The 'original' script is in black; my additions are in blue.

Thanks,

---

### Post by tg3793 on 2010-11-19
And if it helps any here is a four step outline of what the script does:
 
1) Adds exif header information where none previously existed.
... this exif information is coming from the 'current' modified  date/time information which ideally I would not want to have changed at  all.
2) Rotates the files 270 degrees (essentially a 90 degree counter  clockwise rotation)
... this step unintentionally and unavoidably changes the modified  date/time
... however I am gratefully that it doesn't touch the exif date/time
3) And next I put the originally modified date/time back by retrieving  it from the exif information.
4) I'm not sure why clearing the rotation/orientation tag is important  however it was in the original script.

---

### Post by aeiah on 2010-11-19
the file is probably correctly rotated. touching it probably refreshes the thumbnail, which is wrong. perhaps the clearing of the orientation tag is doing something strange. comment it out and see if the problem persists

---

### Post by tg3793 on 2010-11-19
> **aeiah said:**
> the file is probably correctly rotated. touching it probably refreshes the thumbnail, which is wrong. perhaps the clearing of the orientation tag is doing something strange. comment it out and see if the problem persists

Thanks; will try that in the morning when I wake up (it's about 11pm here). And GREAT blog BTW. Wow; "'back in time' snapshots", merging and bursting PDFs, searching a bunch PDFs at once ... I checked it out and it looks like I should caution myself from an addiction :-)

---

