---
title: "Not working??"
date: 2012-06-10
forum: General Help
---

### Post by alphaamanitin on 2012-06-10
[s]Any ideas why this isn't working correctly?
```
find / -iname "*.mp3" -exec cp "{}" my_music \;
```It only copies one of the thousands of mp3 files it finds.  I checked the to make sure I had the find correct, used this command:```
find / -iname "*.mp3" >music_path_list.txt
```Makes a list of over 15,000 mp3s I have but won't compy them.  I waited twenty minutes and it had only copied one file.  Tried again and waited forty minutes, again only the one file (same file both times).  

Did I do anything wrong?  I really want to use mv command, but I decided that cp was safer. [/s]

Solved code should have been ```
find / -name "*.mp3" -exec cp '{}' /my_music/  ';'
```  Discovered it was rather STUPID of me to have the folder I am trying to copy the files to is inside the directory I am using the find command in to find the music and then copy it.  As I say, a just a *wee bit* stupid.  Still I would take any suggestions.

AlphaA

---

