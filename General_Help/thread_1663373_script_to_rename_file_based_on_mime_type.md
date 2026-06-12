---
title: "script to rename file based on mime type"
date: 2011-01-09
forum: General Help
---

### Post by RussellEngland on 2011-01-09
I have a folder containing the output from Windows XP "File and Settings Transfer Wizard" - the folder refuses to be imported into any flavour of Windows and the original windows system is no more - so I found a little program called fastconv [http://www.fastconv.org](http://www.fastconv.org) which extracted all the files but fails to rename them - been working on this solidly for 3 days now, there are 47,000 files in 20gb, so naturally the customer is very concerned.

I noticed that Ubuntu cleverly recognises the type of file, assuming its looking at the contents of the file rather than the extension.

Is there any way I can automatically rename the files based on the mime type?

Many thanks, Russ

---

### Post by TeoBigusGeekus on 2011-01-09
...wrong thread...sorry!

---

### Post by RussellEngland on 2011-01-09
Phew... Thought I was going mad then... :)

I found this thread [http://askubuntu.com/questions/7321/rename-music-files-with-missing-file-extensions](http://askubuntu.com/questions/7321/rename-music-files-with-missing-file-extensions)

Which has this code 
```
#!/bin/bash
file -i "$@" |
while read -r line; do
  file=${line%:*}
  type=${line##* }
  case $type in
    audio/x-flac) ext=flac;;
    audio/mpeg) ext=mp3;;
    application/ogg) ext=ogg;;
    *) continue;;
  esac
  [[ $file = *.$ext ]] || mv -i -- "$file" "$file.$ext"
done

```

I don't know what the type of file will be though. So Ideally, I would like to use the $type variable and grab the text between / and ) eg: use mpeg as $ext from audio/mpeg)

I've no idea how to do that though. 


I also found this [http://mark0.net/soft-trid-e.html](http://mark0.net/soft-trid-e.html) which I'm running through "wine cmd" but I'm not sure how accurate it will be compared to ubuntu.


Cheers, Russ

---

