---
title: "Have Rhythmbox create .m3u not! .pls playlists for media device."
date: 2010-01-16
forum: General Help
---

### Post by LubindaMaim on 2010-01-16
Hi, i'm trying to get rhythmbox to copy playlists to my device, a cowon s9, as m3u files but instead it makes .pls files which my player cant read(?). I tried modifying the '.is_audio_player' file (horrible documentation on this yet quite useful), to do this but it doesn't seem to work (still making .pls files), it follows the playlist_path command just not the format command, any ideas? Thanks.

This is my .is_audio_player file :-
```
audio_folders=Music/,Recordings/
folder_depth=2
output_formats=audio/ogg,audio/wav,audio/flac,audio/mp3,audio/wma,audio/ape,audio/aa,video/svid,video/wmv,video/divx
playlist_format=audio/x-mpegurl
playlist_path=Playlists/
```

Note: I've tried using the manual method of creating the playlists rhythmbox, i.e. creating a play queue then saving it to file as m3u, problem is that m3u doesn't have the required #EXTINF per song for any of the songs. I'm going on a guess that when making a playlist for a device it adds that (I think I saw an example of an m3u created by it for a device somewhere, which i can't seem to find anymore).

---

### Post by jamesisin on 2010-01-16
I want to make sure I understand your problem.

When I right-click on a playlist I can choose "Save to File..." and this brings up a save-as dialog.  By default mine comes up as a .pls file and the Select playlist format drop-down "By extension" (with two other options being .m3u and .pls).

What happens when you do this?

---

### Post by LubindaMaim on 2010-01-16
Oh, I meant when making a playlist from the save as.. menu, then it creates a playlist that cant be read by the device, however I guessed that creating one for a device directly i.e. using the new playlist option when right clicking a device from the side menu, should make one that works.

Just confirmed this by comparing the .pls's files created both ways, the save as method creates one which lists file location for songs, the one on the 'device method' has identification/info of the file (track, album, etc) and the file location info. 

The specific problem is getting it to create .m3u files through the device method as it creates .pls files by default with no visible option to change that, hench im trying the .is_audio_player method that i believe is supposed to tell it what format to use but it doesn't. I hope this clarifies what i'm after, its not something I understand too well so its hard explaining it. Thanks

---

### Post by jamesisin on 2010-01-16
Are you saying then that using the method I proposed above, your m3u files show only file paths while the pls files include information which allows some relative file locating?  (Forgive my ignorance.)

---

### Post by LubindaMaim on 2010-01-16
All playlist created the save as method lack the info both .pls and .m3u, compared two .pls created both ways.

example off wikipeida for .pls 

'Full' playlist via device
```
[playlist]
NumberOfEntries=3

**File1**=http://streamexample.com:80
**Title1**=My Favorite Online Radio
Length1=-1

File2=http://example.com/song.mp3
Title2=Remote MP3
Length2=286

File3=/home/myaccount/album.flac
Title3=Local album
Length3=3487

Version=2
```

'Incomplete' via save as
```
[playlist]
NumberOfEntries=3

File1=http://streamexample.com:80

File2=http://example.com/song.mp3

File3=/home/myaccount/album.flac

Version=2
```

so for m3u 
```
#EXTM3U

#EXTINF:123,Sample Artist - Sample title
C:\Documents and Settings\I\My Music\Sample.mp3

#EXTINF:321,Example Artist - Example title
C:\Documents and Settings\I\My Music\Greatest Hits\Example.ogg

```

the ones created through the save as method lack the #EXTINF lines, i can add them manually but for a 200+ song playlist its impractical.

---

### Post by jamesisin on 2010-01-16
Here is one possible method for changing existing playlists.

Open your pls (the one with the additional information) in GEdit.  All of my entries begin as such:

File1=smb://

(All of my music is on a Samba share.)

Do a find and replace:

Find: File*=smb://
Replace: smb://

Then change the header information at the top of the file from:

[playlist]
X-GNOME-Title=[Some Title]
NumberOfEntries=200

To:

#EXTM3U

Save that file as an m3u.

You may have to add another find and replace if there is more than one line which begins File#= for each file, but it should be fairly simple to sort it out.

Let me know if you have questions about this.

---

### Post by LubindaMaim on 2010-01-16
Found that actually the .pls made by rhythmbox show file then title (wrong way round) which means I would have to manually switch each of them, guess i might just looking around for a program thats for making playlists. Also can i ask for future reference how could i replace say title1=, title2=, title3=, etc with #EXTINF: at once, tried title*= couldn't find them in gedit. Thanks for the help.

---

### Post by jamesisin on 2010-01-16
That might be a bit more of a challenge and something better handled by a script.  You'd have to align a list of Title#= results with a list of #EXTINF: results in a meaningful way.  Not sure how to go about it exactly.

Yeah, I just tried running a find in GEdit and then in OO Word Processor for File*= and came up empty.  [Shakes head.]  Thought that would work.  Must be nap time.

---

### Post by LubindaMaim on 2010-01-16
Yep so far nothing found, but tried banshee found that it creates m3u playlists which i can use (still need to convert / to \), but not a fan of it seems bloated and sluggish compared to rhythmbox, fails to eject the player and froze up twice, but if it works i cant complain, wonder if its a bug rhythmbox not reading the playlist_format option will have to look into it later, like you i'am also tired. Thanks for the help.

---

### Post by jamesisin on 2010-01-16
Yeah, I didn't care much for Banshee.  You'd think it would be a lot better than it is.

For me, I run an old iPod (60 GB) with Rockbox so I can't do any sort of playlist synking (or nothing that I've found so far).

---

