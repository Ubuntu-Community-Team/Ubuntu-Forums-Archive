---
title: "Transferring Music"
date: 2011-07-31
forum: General Help
---

### Post by snobored on 2011-07-31
I have songs I want to transfer from my laptop running ubuntu, to another computer running windows. The issue is that none of the songs have their file extension. Of course this is irrelevant to linux, but makes them unusable to windows. Is there anyway to transfer the music through rhythmbox, or any software, in such a way that extensions will be assigned? or is there anyway to give them extensions correctly without going through every song by hand? I tried a bash script
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


With no luck, would only apply to the first song in the folder, and immediately made it an empty text file. Any suggestions?

---

### Post by LemursDontExist on 2011-07-31
If you replace ```
file -i "$@" |
``` with ```
file --mime-type "$@" |
``` I think your script should work.  If you look at the output of file -i it includes the mime-encoding after the mime-type (which I guess should usually be charset=binary).

Out of curiosity, what does the '--' in the mv command do?  I've never seen that before, and it doesn't seem necessary to me, but it works, so I assume it does something!

---

### Post by snobored on 2011-07-31
my lack of familiarity with scripting is really the issue here. I made that edit to the file, and the exact same thing occurs. 
I'm invoking it by using "script /path/to/directory/{**/,}*"
It doesn't return errors, it simply says "Script started file is [first song]" and when I check to see if even that had the intended effect, I find a text file with the same name, that's empty.

---

### Post by AlphaLexman on 2011-07-31
The move command expects a directory as the final argument, to override this, add the '**-T**' flag to your command.
```
mv [COLOR="Red"]-T[/COLOR]i "$file" "$file.$ext"
```

---

### Post by snobored on 2011-07-31
edited to reflect that correction, still getting identical behavior. At this point, I'm honestly confused as to why this won't work. Thanks to both of you for input so far though.

---

### Post by snobored on 2011-07-31
I grouped them by type on Ubuntu, put them in separate folders, and did batch rename in windows. Frustrating, but this was the only solution I could put together.

---

