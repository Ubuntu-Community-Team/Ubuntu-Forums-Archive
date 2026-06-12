---
title: "Decibel Audio Player / Conky"
date: 2009-07-21
forum: General Help
---

### Post by sbisset on 2009-07-21
Hello, I'm trying to get Conky to display "now playing" info for Decibel audio player.  There's a plugin for Decibel that generates a text file containing this information, it looks like this:

         {title} by {artist}


Using "${execi 5 cat ~/.config/decibel-audio-player/now-playing.txt}", Conky reads this file fine, having no trouble with the actual output of the file but I want to customize it further. For example, I want the song title in a bigger font than the rest of the text, but if I change the settings for the "now playing" text file to read something like "${font Arial Black:size=24}{title}$font by {artist}" Conky just ignores the font tag and prints the whole thing out, so I have 

"${font Arial Black:size=24}Track 01 $font by Artist"      sitting on my desktop and ruining my lovely new conky display. :'-(

Is there any way to make conky read the tags as tags, not as text? I've googled and checked the forums but can't find anything to help me, I imagine it's a question of writing a simple bash script, but I'm a linux novice and don't know where to start. Any help would be greatly appreciated :-D

Thanks in advance

---- UPDATE
Never mind I got it sorted.

---

