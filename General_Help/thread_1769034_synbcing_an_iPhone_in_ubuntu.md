---
title: "synbcing an iPhone in ubuntu?"
date: 2011-05-27
forum: General Help
---

### Post by eltonw on 2011-05-27
With Natty Narwahl (11.4) now on my netbook, I was VERY PLEASANTLY SURPRISED to find that it loaded up Shotwell, and the [COLOR="DarkOrange"]**Banshee Media Player**[/COLOR]. The former to manage / import photos, the latter gives me options to manually or automatically **sync** music, audiobooks, and podcasts on my **iPhone 3GS**.\\:D/

[FONT="Verdana"]I wonder: is there a way _to sync my [COLOR="DarkRed"][U]address book and calender from the iPhone_[/COLOR] in Ubuntu[/U]?
[/FONT]
Evolution :-(does not 'automatically' do this.

Instead, I *manually* export my calendar.ics and address book .vcf to USB stick (on Macbook) then import them into Evolution on the netbook. 

Is there a linux app that will import / sync my contacts / calendar [COLOR="DarkRed"]from the iphone[/COLOR] in the manner that [COLOR="Dark Orange"]Banshee[/COLOR] offers? [...something that will recognize the phone when connected and offer to import this data].

A few days after my original post, I lost the ability to mount the iPhone.

**[COLOR="DarkOrange"]_UPDATE: [02 JUNE 2011]_[/COLOR]** Found a solution in this thread: 
[http://ubuntuforums.org/showthread.php?t=1670314]("http://ubuntuforums.org/showthread.php?t=1670314")
[-XHowever, this solution [COLOR="DarkRed"]*_NO LONGER WORKS_*[/COLOR]. I have left a comment for the developer of **pmcenery**
HERE: [https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=karmic]("https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=karmic")

... hoping that an update to **pmscenery** will restore this functionality

---

### Post by kyteflyer on 2011-06-14
Oh I got all excited when I started reading your post... until I got to the end :{  My iphone is recognised but Banshee crashes.  Shotwell works as well as ever it did.  Oddly, I get icons on the desktop, one of which says Documents on iPhone, and when opened, it shows a number of iphone app icons (presumably those which can have stuff drag-dropped via itunes).

However I want to be able to drag all my music from my iphone and I can't, because Banshee simply refuses to behave.

---

### Post by eltonw on 2011-06-14
Just recently, I did a clean NEW install of Natty, downloaded the *most recent* updates. 

[COLOR="Sienna"][FONT="Comic Sans MS"]**NOTE**: I did NOT add the pmcenery fix.[/FONT][/COLOR]

[FONT="Garamond"][COLOR="Green"]Oddly though, my iPhone now mounts ... _even after the most recent updates_.[/COLOR][/FONT]

I get two folders: the iPhone, and "Documents" (viz: documents _on the phone_).
Shotwell loads and imports photos

Banshee loads, but when I tried to do a sync, it only prompted if I wanted to *[COLOR="DarkRed"]delete[/COLOR]* my sound files.
It DID: it deleted all music files, ringtones, and audio books that were already on the phone.
An attempt to write **mp3** files from the library on my netbook failed with an error message saying that those files are 'not  playable on the phone'.
I was able to restore my sound files (music, books, ringtones) by syncing on my Macbook.

So for now, the only syncing that seems to work **properly** is with photos,

[COLOR="Sienna"][FONT="Comic Sans MS"].... pmcenery is still _not_ added to my system,[/FONT][/COLOR]

IMVHO, syncing an **iPhone** in Natty is (for now) *"mi figue, mi raisin"*.... IOW, it *might* work, but YMMV!

---

