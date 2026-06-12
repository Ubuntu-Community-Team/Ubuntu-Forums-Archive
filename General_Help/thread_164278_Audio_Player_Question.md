---
title: "Audio Player Question"
date: 2006-04-22
forum: General Help
---

### Post by BoboChimp on 2006-04-22
first of all, i don't know if this is the right forum for this.  please move it if not.

i'm trying to move away from Windows slowly.  one of the things i'm missing is my Musicmatch Jukebox.  The feature i like is that when you double click a song while another is playing, it doesn't automatically start playing the new song.  It puts the new song up in the bottom of the playlist.  Does anyone know of a linux player that has that functionality?  The players i have (Beep, Listen, Rhythmbox & VLC) don't offer that as far as i can tell.  Yeah, i know it's not something that can be worked around by dragging and dropping but when i have a get together, i like to leave the laptop out and available for others to come up and choose some music.  most people just double click what they want to hear and that messes up the flow.

I know very little about programming, but maybe that is something that could be altered in the code relatively easily too.  just a thought.

---

### Post by Sutekh on 2006-04-23
Two players I like to use, Rhythmbox (later versions) and [Quod Libet](http://www.sacredchao.net/quodlibet), allow you to add songs to a queue, but not by double-clicking.  You have to right-click and add to queue.

I'm sure that the coding could be changed so that double-clicking adds to queue rather than playing now.  I would have no idea how to do that though.

---

### Post by hugmenot on 2006-04-23
In quodlibet you add stuff to the queue by double click when you do that aside from the main play list. Ie. you open another browser and fill the queue in the main window by double clicking. You can also hit Q in all places to enqueue the selected songs.

---

### Post by Sutekh on 2006-04-23
[QUOTE=hugmenot]In quodlibet you add stuff to the queue by double click when you do that aside from the main play list. Ie. you open another browser and fill the queue in the main window by double clicking. You can also hit Q in all places to enqueue the selected songs.[/QUOTE]
Ahhh, now I love Quod Libet even more!

---

### Post by BoboChimp on 2006-04-23
Hugmenot - how do you open another browser like you talked about?  do i open another instance of quodlibet?

Hey, on another note, do any of you know of an open source site/database that will do automatic tag matching with the correct info (again, like Musicmatch).  If i give it the artist and title (or part of the title) it will bring up a list of all the matched tags available.  i can then pick which tag has the correct info (album, correct song title etc) and it will re-tag it for me.

---

### Post by hugmenot on 2006-04-24
[QUOTE=BoboChimp]Hugmenot - how do you open another browser like you talked about?  do i open another instance of quodlibet?[/quote]
No no, go to Music > Search Library > pick your preferred browser.

> Hey, on another note, do any of you know of an open source site/database that will do automatic tag matching with the correct info (again, like Musicmatch).  If i give it the artist and title (or part of the title) it will bring up a list of all the matched tags available.  i can then pick which tag has the correct info (album, correct song title etc) and it will re-tag it for me.
Quodlibet offers you to query FreeDB (tracks have to be in the correct order like on the original CD; the matching CD is figured out by the tracks and their lengths) or Musicbrainz (you have more fuzzyness here I think and you can enter an album title when nothing matches at first).
Select all tracks first and then right-click to select the plugins CDDB or Musicbrainz.

---

### Post by BoboChimp on 2006-04-24
i started looking into those things last night.  i realized that the repositories don't have the latest version of Quod and that the latest version requires Gstreamer 0.10.  Now i've got to figure out if you can use Gstreamer 0.10 in Breezy easily or if i should wait until early June when Dapper comes out.  Then I've got to figure out which Quod to download.  Didn't see one for Ubuntu on the site and the Debian d/l said "experimental".

I've got some work to do but it's fun for me so no big deal.

---

### Post by hugmenot on 2006-04-24
[QUOTE=BoboChimp]i started looking into those things last night.  i realized that the repositories don't have the latest version of Quod and that the latest version requires Gstreamer 0.10.  Now i've got to figure out if you can use Gstreamer 0.10 in Breezy easily or if i should wait until early June when Dapper comes out.  Then I've got to figure out which Quod to download.  Didn't see one for Ubuntu on the site and the Debian d/l said "experimental".

I've got some work to do but it's fun for me so no big deal.[/QUOTE]

The stuff I mentioned must be present in the QL from Breezy, no?

---

### Post by Runefox on 2006-04-25
If you want to use Beep Media Player and have your files enqueue instead of clearing the playlist, you can do the following:

Right-click a file you want to play (MP3, Ogg, etc; You need only do this once per filetype) and go to properties. Under the Open With tab, click the Add button. In the new window, under the listing, click the expander called "Use a custom command". In the box type:

beep-media-player -e

And click Add. Choose the beep-media-player that you just added and try it out. Files are now enqueued instead of taking over the playlist. The only drawback (if you see it that way) is that the playlist you last had open will still be there, and you will have to press the play button manually if nothing is already playing.

Other players' options (follow all previous instructions; Type this in the box instead):

With XMMS:

xmms -e

With Audacious:

audacious -e

With AmaroK:

amarok -a

---

### Post by BoboChimp on 2006-04-25
i'll have to try that.  thanks.

---

