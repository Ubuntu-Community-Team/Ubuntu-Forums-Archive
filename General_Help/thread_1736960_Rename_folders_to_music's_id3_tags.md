---
title: "Rename folders to music's id3 tags?"
date: 2011-04-22
forum: General Help
---

### Post by winchendonsprings on 2011-04-22
Anyone know of an application that will rename a folder to the contents id3 tags?

My music directory is a mess with folder names. Not a big deal since I use Banshee to library everything. I have a fairly large music collection on my main hard drive(140gb) but I keep id3 tags clean. 

I'm setting up an ftp server and it will be impossible to navigate the way the folders are now.

Something similar for movies would be cool too.

---

### Post by dearingj on 2011-04-22
Banshee does that for me. Check your preferences in Banshee (Edit->Preferences) and make sure that, on the General tab, the option "Update file and folder names" is selected.
It may take a long time, since your music collection is so big, for Banshee to get them all renamed. Be patient. It does this in the background, so you can keep on listening to music or whatever, just keep Banshee running.

---

### Post by kiddykoff on 2011-04-22
I like to use Picard to manage my music collection. I have my collection organized by album artist/albume (year)/track # title.mp3

Picard will look up the songs on the musicbrainz database. It will also grab cover art and save it as cover.jpg in the same folder. I believe Banshee will recognize this cover art.

Also Easytag will work. Easytag will rename your file and folders based off what is in the tags. It also works in the reverse. It doesn't compare anything to a database nor will it pull up cover art.

Both of these are in the repositories. Picard is my favorite.

---

### Post by winchendonsprings on 2011-04-23
Thanks. Easy

---

### Post by winchendonsprings on 2011-05-01
In Banshee I have Update file and folder names checked under preferences, but The folder names are not being update. Even after Rescan Music Library.

Any idea why?

I can see when I update an album or track it will update the file and folder names and move them from sub-directory I have them in to the Music folder.

So

- How can I have my entire library's folders renamed?

and

- How can I maintain the subdirectories I have now? (such as ~/Music/downloads or ~/Music/audiobooks)

---

### Post by kiddykoff on 2011-06-16
I just thought of this, but if you mess around in the gconf settings for banshee you can customize different things there.

For example, i have my mp3's renamed %albumartist/%album [%year]/%tracknumber %tracktitle.mp3 or something similar. I can't think of the exact naming at the moment.

I hope this helps you.

---

