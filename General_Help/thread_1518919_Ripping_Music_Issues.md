---
title: "Ripping Music Issues"
date: 2010-06-27
forum: General Help
---

### Post by uRock on 2010-06-27
I recently ripped an album using Rhythmbox and tried to copy the music to my Sony MP3 player. It copies the files over, but the Sony does not show the music. I have never had this problem before with music ripped via other methods.
I have deleted everything on the MP3 and recopied my music to it and all files play, except the ones from the newly ripped album.

Does anyone know of a fix for this? I haven't tried ripping with Windows and loading the music. I was hoping to be able to do this within Ubuntu.

Thanx,
uRock

---

### Post by uRock on 2010-06-28
I would like to add that I have had the same results copying the same album from a second ubuntu system to the MP3 player. I ripped the files in MP3 format using Rhythmbox.

---

### Post by samfuzz on 2010-06-28
perhaps it's related to tag id3 v2.4 utf8 not supported by your hardawre player
[http://ubuntuforums.org/showpost.php?p=1184248&postcount=16](http://ubuntuforums.org/showpost.php?p=1184248&postcount=16)

---

### Post by samfuzz on 2010-06-28
in gnome-audio-profiles-properties (in a console)

replace id3v2mux by id3mux

in the gstreamer pipeline

---

### Post by uRock on 2010-06-28
That fixed it! Thank you very much Samfuzz! =D>

---

### Post by samfuzz on 2010-06-28
just for info :

gstreamer lame is now deprecated accordind to this bug :

[https://bugzilla.gnome.org/show_bug.cgi?id=494528](https://bugzilla.gnome.org/show_bug.cgi?id=494528)

if you want quality mp3 rip use instead
gstreamer lamemp3enc :

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/195483](https://bugs.launchpad.net/ubuntu/+s...er/+bug/195483)

example :
audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc quality=6 ! xingmux ! id3mux


[http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME)

---

### Post by uRock on 2012-06-03
Sound Juicer in 12.04 does not have the button to edit sound profiles. Does anyone know how to get this done?

Thanx!

---

### Post by mc4man on 2012-06-04
Assuming Sj will run without segfaulting (last time I tried in 12.04 it would

Both RB & SJ now can only set encoding parameters thru the use of a preset which is currently not enabled. Also for ogg/vorbis gnome has lowered the default to a q of 3 which is pretty poor

To set up is fairly easy once you get the idea  - 
I go thru it for RB in this thread, both for creating an mp3 & vorbis preset.

Both RB & SJ will use the same preset, you can only have one preset per encoder, so to alter you edit the preset itself

To enable SJ to use those presets you need to edit the rhythmbox.gep in SJ's folder just like the one in RB's folder as shown in link

 ```
sudo gedit /usr/share/sound-juicer/rhythmbox.gep
```

The preset parameters in the linked thread are based on what's avail. for gstreamer, some may be redundant because they are the default anyway

To see available settings for mp3 run
```
gst-inspect lamemp3enc
```

how to set up preset(s)
[http://ubuntuforums.org/showthread.php?t=1965432](http://ubuntuforums.org/showthread.php?t=1965432)

my bug report, seems to be languishing a bit due to upstream disinterest
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/945987](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/945987)

To re-mention - at least here SJ can no longer retrieve track info & segfaults. Myself use rubyripper or abcde, both are easy to set up & superior.
I mainly took interest because of RB being set back to default...

---

### Post by uRock on 2012-06-04
Thanks mc4man. I gave my one-up to the bug report. Hopefully they will take care of it.

---

### Post by Erik1984 on 2012-06-04
In the meanwhile you might try an alternative program for ripping music. If you're not afraid of pulling in KDE packages K3B has a decent ripping function. I used it several times now and never failed to fetch the right results and it easily allows configuring format and quality.

---

### Post by mc4man on 2012-06-04
RB has fixed this today in 12.10 by enabling a 'Custom Setting'
What is does is then dynamically edit the quality settings in the .prs that is auto-created in `~/.gstreamer-0.10/presets
It only adjust the quality= line, if desiring other parameters then one can probably self edit
(but if doing so & then re-opening the settings dialog in RB  I'd check the file just to see if anything unwanted was written

Whether SJ will likewise be set up to use these prests and or edit don't know yet, but again if not it only would need the presets  name to be added to it's .gep to use that preset, RB no longer needs the "preset=" line in it's .gep

The preset name being used are - rhythmbox-custom-settings for all enabled profiles

Whether this gets SRU'd to 12.04 don't know, really should be.

screen shows the preset as Default supplied, by changing it has been moved to a .bak & there will be a new one
screen 2 the new preset @ quality=1


Note - if this does show up in 12.04 & one had previously created .prs or 2 then delete it  or you'll end up with 2 presets in the .prs which wouldn't be good

---

### Post by uRock on 2012-06-04
I ended up installing Asunder CD Ripper with the add-ons listed in USC. It worked great and the music plays with my Walkman.

iHappy

---

### Post by uRock on 2012-06-04
> **mc4man said:**
> Whether this gets SRU'd to 12.04 don't know, really should be.

I hope so. It is always better when one doesn't have to install multiple programs to similar tasks.

---

### Post by mc4man on 2012-06-04
It seems That RB has decided to change it's toolbar a bit, not sure how well received that's going to be..

They've moved album art to the toolbar, so to accommodate have increased the width & added text under icons. Atm when there is no art avail. the placeholder icon is terrible, that should be fixed though overall the look is heavy

 The source built fine in 12.04 & other than that small icon regression can go into 12.04 easily. (actually one could probably just use the _current_ 12.10 RB packages in 12.04

Or just the preset code could be applied & RB's interface changes left for 12.10
Though it's also possible that nothing will be done in 12.04 officially..

---

