---
title: "Music library: folder sorting"
date: 2006-05-15
forum: General Help
---

### Post by mikaPELL on 2006-05-15
Hi again, nice Ubuntu folks!
I have a pretty (what I find to be) advanced request. My music folder, "/home/mikapell/knato/mp3/" (where knato/ is a mounted hard drive), is incredibly messy. The folder names are kind of random, and the deepness of the tree structure varies as well. There are all kinds of files in there, but the music is mostly .mp3, a good share of .m4a (from my Windows + iTunes days) and a tiny bit .ogg. The other files are e.g. random videos, also from iTunes, and some other crap. *MANY* of the music files are duplicates.
I then wonder if someone could help me write a script, redirect me to an application, or generally help me ease the process of doing the following:

[LIST][*]Sort out the music files[*]Remove/sort out duplicates[*]Re-encode all non-duplicate, non-previously mp3 encoded music into mp3 @ 192 kbps[*]List the broken ID3 tags, and let me fix them, before[*]Making a new tree structure, like ./mp3/Genre/Artist/Album/song.mp3
[/LIST]

I would greatly appreciate all sorts of help, and I am looking forward to reading eventual answers :)

---

### Post by pillypoon on 2006-05-16
[QUOTE=mikaPELL]Hi again, nice Ubuntu folks!
I have a pretty (what I find to be) advanced request. My music folder, "/home/mikapell/knato/mp3/" (where knato/ is a mounted hard drive), is incredibly messy. The folder names are kind of random, and the deepness of the tree structure varies as well. There are all kinds of files in there, but the music is mostly .mp3, a good share of .m4a (from my Windows + iTunes days) and a tiny bit .ogg. The other files are e.g. random videos, also from iTunes, and some other crap. *MANY* of the music files are duplicates.
I then wonder if someone could help me write a script, redirect me to an application, or generally help me ease the process of doing the following:

[LIST][*]Sort out the music files[*]Remove/sort out duplicates[*]Re-encode all non-duplicate, non-previously mp3 encoded music into mp3 @ 192 kbps[*]List the broken ID3 tags, and let me fix them, before[*]Making a new tree structure, like ./mp3/Genre/Artist/Album/song.mp3
[/LIST]

I would greatly appreciate all sorts of help, and I am looking forward to reading eventual answers :)[/QUOTE]


I really like Easytag.. Its a little confusing at first but it will do 3/5 of your requests..  Once you get the hang of it , its very powerful. 

  I dont know of a program that finds dupes , I am sure someone in this forum can lead you in the right direction..

 As far as reenocing your files I heard soundconverter might do the trick.. I never used it myself so I dont know if you can do batch jobs..  Good Luck

---

### Post by mikaPELL on 2006-05-16
Thanks a lot, I'll check out sondconverter, I've used Easytag a bit before. The biggest problem seems to be the tree structure. Do you think I could use a shell script to delete the tree structure, or move all files into another folder, without the tree structure?

thanks

---

### Post by pillypoon on 2006-05-16
Easytag will move all of your files from the folders they are in and make new ones for you.. It can make new folders with artists names, albums ETC..

---

### Post by mikaPELL on 2006-05-16
Seriously? I must have not checked thoroughly enough. I'll do it now :)

---

### Post by pillypoon on 2006-05-16
make sure you test it on a few sample files first..  You dont want to f*up your whole collection.

---

