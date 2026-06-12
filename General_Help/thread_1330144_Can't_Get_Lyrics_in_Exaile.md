---
title: "Can't Get Lyrics in Exaile"
date: 2009-11-18
forum: General Help
---

### Post by clevertomato on 2009-11-18
No matter what I do I can't get any lyrics to show up in Exaile. I'm running Karmic. I've made sure all the red and green packages are installed that are listed at packages.ubuntu and I've even added gmpc-plugins just for kicks. I've ticked the wiki lyrics and lyrics fly, one and both. I don't know what else to try. Having trouble with cover art, too, but I'll save that for another time I guess.

The Ubuntu experience has really been trying my patience lately. I'm an experienced geek; I can't imagine an average consumer getting everyday apps to work out of the box. I'd so much rather be spending my time listening to and organizing my music than fiddling with things to get apps to work.

---

### Post by clevertomato on 2009-11-20
bump

---

### Post by elgandoz on 2009-12-22
Hey, I had the same problem, then I find where the lyrics are.
Check If you have all packages installed, go to preferences --> plugin --> and activate "Context Info" and "lyrics xxx" (the one you want).
Now in the left sided tabs, the last one is context...it is like in Amarok. On the upper right corner (at the rigth of the song's cover) you have now a "lyrics" button..even if it doesn't fetch a lot of songs! It needs a lot of improovments!

PS (weird thing): I already had most of the plugins, even if the packages in synaptics were not installed...

---

### Post by elgandoz on 2009-12-22
I forgot it: in the preferences->plugins dialog, check the description...there are the dependencies! check if you're missing one. I'm running it in Karmic. Lyricsfly works definitively better.
Hope this could help you.

---

### Post by clevertomato on 2009-12-23
Nothing you've described matches my screen. I've enabled the Lyrics plugin (both & either). I never see a list of dependencies or anything that says "Context."

BTW, I'm running Exaile 0.3.0.2

---

### Post by nerdelicious on 2010-01-19
Any luck finding a solution? I have the same problem with Exaile 0.3.0.2 on 64-bit Karmic, it looks like there's simply no lyrics support in Exaile.

---

### Post by clevertomato on 2010-01-19
No, no solution that i've found.

---

### Post by cheyo on 2010-01-29
Hi, was having this problem too, but i found the solution:

1.- Install exaile from ppa, version 0.3.0.2
2.- install VIA SYNAPTIC or VIA TERMINAL the "exaile-plugin-contextinfo"  plugin:

```
sudo apt-get install exaile-plugin-contextinfo
```

3.- Enable on the exaile plugins dialog the newly avaiable "context info" plugin, note that it has dependencies that you can find also on synaptic. 

The trick is install  the plugin via synaptic, not via the plugins dialog on exaile...

Sorry for my English guys!

---

### Post by clevertomato on 2010-01-30
That seems to work. Thank you. I must say that Exaile's interface is pretty misleading in this regard. It clearly shows lyric options in it's own plugin list. One would presume that by enabling those, one would have lyric support.

Anyway, thanks.

...so it appears this doesn't help in Jaunty. Apparently exaile-plugin-contextinfo is not available for Jaunty. Yet, like I said, Exaile has claimed to support lyrics since before Karmic. I'm not feeling the love for Exaile right now.

---

### Post by itisbasi on 2010-03-29
I can get the lyrics tab on Exaile but the lyrics don't get displayed. Any ideas?

---

### Post by jsriz on 2010-03-29
> **itisbasi said:**
> I can get the lyrics tab on Exaile but the lyrics don't get displayed. Any ideas?
I usually get lyrics for original music (which i bought at the store)
The ones I downloaded from net have all the names edited(artist,track etc) hence don't give any lyrics 
damn these uploaders guess nothing can replace  original cds......

---

### Post by clevertomato on 2010-03-31
itisbasi: sorry, no ideas from me. I'm all out. Hopefully someone else can help.

---

### Post by apsot on 2010-04-03
Same problem here. My lyrics tab appears, my context tab seems to be working like charm but i always get the message no lyrics found even for songs rhythmbox does find lyrics. If anyone has an idea it would be appreciated

---

### Post by OwnSurname on 2010-04-10
Same problem here. I like Exaile, lyrics were working until few weeks ago, now they don't anymore. Not the first time it happened, I'm so annoyed I decided to give another player a chance: Guayadeque [1], give it a try.
I'm looking for a light simple player that will show me lyrics, will permit me to create playlists, and that's it. All the other options are meaningless to me, although the cover can be a small plus. I don't want a player that will delete my files, or that will order them, or that will modify them in any way (unless asked), or that will suggest me similar songs.
Also, I'd like to have a player able to retrieve the information directly from the folder where the files are in, and eventually if asked will check against a database to fill the empty ones. Anyone interested in starting a new project (YAMP: yet another mp3 player)? :)

1. [http://ubuntuforums.org/showthread.php?t=1380811&highlight=exaile+lyrics]("http://ubuntuforums.org/showthread.php?t=1380811&highlight=exaile+lyrics")

---

### Post by itisbasi on 2010-07-31
I added the lyrics to the ID3v2 tags of my mp3s using songbird and exaile now displays those lyrics. Looks like exaile doesn't allow us to add the lyrics to the songs and only displays lyrics which are already there.

---

### Post by nbubis on 2010-08-07
I got lyrics working in 10.04 without adding the lyrics manually to the tags. Solved it by checking (in the plugin menu):

1. Enabling "Lyrics Viewer" & "Lyrics Wiki".
2. Disabling "Lyrics Fly" .

Until I disabled "Lyrics Fly" I couldn't see any lyrics either.

Hope this helps someone,

Nathaniel.

---

### Post by itisbasi on 2010-08-09
> **nbubis said:**
> I got lyrics working in 10.04 without adding the lyrics manually to the tags. Solved it by checking (in the plugin menu):

1. Enabling "Lyrics Viewer" & "Lyrics Wiki".
2. Disabling "Lyrics Fly" .

Until I disabled "Lyrics Fly" I couldn't see any lyrics either.

Hope this helps someone,

Nathaniel.

Hell yeah!! That works perfectly. Thanks!

---

### Post by Jombib on 2011-06-10
> **nbubis said:**
> I got lyrics working in 10.04 without adding the lyrics manually to the tags. Solved it by checking (in the plugin menu):

1. Enabling "Lyrics Viewer" & "Lyrics Wiki".
2. Disabling "Lyrics Fly" .

Until I disabled "Lyrics Fly" I couldn't see any lyrics either.

Hope this helps someone,

Nathaniel.

That worked for me. Had to install a dependency before it would allow me to enable lyrics wiki but worked perfectly after that.

Thanks

---

### Post by Someone in time on 2011-08-15
> **nbubis said:**
> I got lyrics working in 10.04 without adding the  lyrics manually to the tags. Solved it by checking (in the plugin menu):

1. Enabling "Lyrics Viewer" & "Lyrics Wiki".
2. Disabling "Lyrics Fly" .

Until I disabled "Lyrics Fly" I couldn't see any lyrics either.

Hope this helps someone,

Nathaniel.
Totally works man... thanks.. :D

---

