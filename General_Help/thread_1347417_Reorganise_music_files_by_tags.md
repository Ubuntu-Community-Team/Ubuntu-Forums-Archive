---
title: "Reorganise music files by tags"
date: 2009-12-06
forum: General Help
---

### Post by blazemore on 2009-12-06
It seems there's apparently a plethora of options to do this, but none of them seem to work.
What I want to do is rename everything in my large music collection according to ID3 tags.
For example:
```
~/Music/Cute_Is_What_We_Aim_For-The_Same_Old_Blood_Rush_With_A_New_Touch-2006-MP3/01-cute_is_what_we_aim_for-newport_living.mp3
```
would become
```
~/Sorted/Cute Is What We Aim For/The Same Old Blood Rush With A New Touch/01 Newport Living.mp3
```
(yes I know spaces don't work in Unix filenames as they are, but I just want to show you what I mean)

Is there ANYTHING that can do this? I even tried teaching myself PYTHON to get it to work, but it won't.

---

### Post by StuartN on 2009-12-06
> **blazemore said:**
> It seems there's apparently a plethora of options to do this, but none of them seem to work.

id3v2 [http://sourceforge.net/projects/id3v2/](http://sourceforge.net/projects/id3v2/) inside a mv command could do it, but Easytag [http://easytag.sourceforge.net/](http://easytag.sourceforge.net/) is probably simplest.

Edit: and here is a completed script [http://www.linuxquestions.org/questions/linux-general-1/bash-script-for-sorting-and-renaming-multiple-mp3-files-by-id3-tags-602105/](http://www.linuxquestions.org/questions/linux-general-1/bash-script-for-sorting-and-renaming-multiple-mp3-files-by-id3-tags-602105/)

---

### Post by blazemore on 2009-12-06
Thanks, but I need some help with Easytag.
I have made the mask
/home/james/Desktop/Sorted/%a/%b/%n %t
Which would produce an example filename in the format I wanted
But when I run through, it goes through really quickly, too quickly to be working. And when I check, it hasn't renamed anything!
I think easytag can only rename files within their current directory :-(

---

### Post by StuartN on 2009-12-06
> **blazemore said:**
> Thanks, but I need some help with Easytag.
I have made the mask
/home/james/Desktop/Sorted/%a/%b/%n %t
Which would produce an example filename in the format I wanted
But when I run through, it goes through really quickly, too quickly to be working. And when I check, it hasn't renamed anything!
I think easytag can only rename files within their current directory :-(

I haven't used Easytag for a while, but it definitely renames and moves. It now has several modes for renaming (manual, scanner, cddb) and the mode that relocates files is scanner - "With the scanner mode “Rename File and Directory”, you can easily fix names of lot of files and move them into new directories. As the new file names will be based on the tag values, it is important to have correct tags." [http://easytag.sourceforge.net/EasyTAG_Documentation.html](http://easytag.sourceforge.net/EasyTAG_Documentation.html)

---

### Post by g.a. on 2009-12-12
a command line approach might be

mp3rename

i used for my collection and it was ok

g.

---

### Post by blazemore on 2010-01-26
Can I bump this?
I want to use this with rsync to put files on my mp3 player.
I can't get mp3rename to work.

I want to rename files like this

```
/media/IPOD/Enter\ Shikari/Take\ To\ The\ Skies/03\ Mothership.mp3
```

"\ " is a space

---

### Post by woodyson on 2010-01-26
> **blazemore said:**
> Thanks, but I need some help with Easytag.
I have made the mask
/home/james/Desktop/Sorted/%a/%b/%n %t
Which would produce an example filename in the format I wanted
But when I run through, it goes through really quickly, too quickly to be working. And when I check, it hasn't renamed anything!
I think easytag can only rename files within their current directory :-(
With Easytag the scan will run quickly but the files are not renamed until the SAVE button is pressed (with all relevant files selected).

---

### Post by blazemore on 2010-01-26
Alright I will have another look at Easytag.
I'm going to work on a python script to do this as well.

---

