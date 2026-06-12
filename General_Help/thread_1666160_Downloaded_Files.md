---
title: "Downloaded Files"
date: 2011-01-13
forum: General Help
---

### Post by SuperFreak on 2011-01-13
If I rename folders that I have downloaded from torrent sites they are not recognized by all my software. Specifically although Amarok will recognize music files in these renamed folders SqueezeboxServer will see the files in the folder as an unrecognized format. If I rename the individual files in the folder but not the folder then the files  are recognized by both programs. Is there something I need to know about renaming downloaded folders that doesn't apply to files?

---

### Post by cmoraes on 2011-01-13
Could you post an example of renaming the directories.  In general, renaming a directory should have no connection with an application being able to read a file format.   The only thing I can think of is if the application expects the files to have names similar to the directory.  e.g.  
Directory is <ArtistName> and files have to be <ArtistName>_<SongName>

Even in that case, it would seem to be an application bug.

---

### Post by SuperFreak on 2011-01-13
OK I will try it on this folder of music called "Robin Trower Long Misty Days(rock)(flac)". I would like to change that to "Long Misty Days". Right now my SqueezeboxServer recognizes all the files in that folder("Robin Trower Long Misty Days(rock)(flac)") and will play them on my stereo (The Squeezebox is a media player that interfaces between computer and stereo via ethernet and plays any music files from the computer on the stereo). OK now I have renamed the folder "Long Misty Days" and the squeezebox shows the folder but the music files can't be played and are shown as File Format: Unknown . I know from prior experience if I were to now rename the folder with the original folder name "Robin Trower Long Misty Days(rock)(flac)" that Squeezeboxserver would then recognize the folder and play the music. Now if  I did things a little differently and I make the initial changes to the folder name in Win XP(I have a dual boot and the folder in on a NTFS partition)) and then boot back into Ubuntu the new folder name does not affect playback on SqueezeboxServer.


Directory Structure:   Genre/Artist/Album/Song

Changing the Artist name  or Song name doesn't affect the ability to play the song Changing Album name does but only for SqueezeBoxServer application

---

### Post by cmoraes on 2011-01-13
Does SqueezeboxServer have an option to rescan your media files?   I suspect this could be a bug in the application.   Re-scanning your media may build the SqueezeboxServer database.

EDIT:  Looks like someone else has the same problem you do [http://forums.slimdevices.com/archive/index.php/t-83351.html](http://forums.slimdevices.com/archive/index.php/t-83351.html)

---

### Post by Slim Odds on 2011-01-13
> **cmoraes said:**
> Does SqueezeboxServer have an option to rescan your media files?   I suspect this could be a bug in the application.   Re-scanning your media may build the SqueezeboxServer database.

Exactly!

Most applications that have to deal with a large number of files (especially ones with embedded data in them, like MP3 files), will create their own database of these files and their data. Otherwise the rescanning at start-up will take WAY too long.

---

### Post by SuperFreak on 2011-01-13
I did try a rescan of squeezebox server but the folder and it's files were not recognized. It seems strange as I can rename the individual files (songs) anything I like and it doesn't affect the outcome. I can also rename the directory above the folder and it doesn't matter but if I rename the Deluge folder any differently then it was named in the download it won't work. It also is a mystery why I can rename the folder in Win XP and then open up Ubuntu and the folder is recognized by Squeezeboxserver.

---

