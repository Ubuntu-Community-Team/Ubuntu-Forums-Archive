---
title: "CD Ripping"
date: 2006-04-16
forum: General Help
---

### Post by mcletter on 2006-04-16
I noticed that with the Juicer CD Ripper, the only available formats are .wav .ogg and some other one.. But is there a CD ripper I can use that rips them to mp3's?

---

### Post by Fysidiko on 2006-04-16
Goobox is an extremely capable CD player/ripper and will rip to MP3 if you've got LAME installed. It's in the universe.

---

### Post by ncappel1 on 2006-04-16
Sound Juicer **will** rip to .mp3, but you have to have the appropriate codecs installed, like lame, you can get them from synaptic in the universe repository.

---

### Post by ncappel1 on 2006-04-16
oops, i forgot to add that then you have to add an mp3 profile in sound juicer. 

go to edit-->preferences-->edit profiles, if mp3 isn't there, then click on new profile. and make the profile name,  description and file extension "mp3" (without the quotes :p ) 

the Gstreamer pipeline should have: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

the "active?" box should be checked.

hope that works!

---

### Post by bryanchapman9999 on 2006-04-18
Many thanks ncappel1.

That worked perfectly for me...

Cheers
Bryan

---

### Post by ronmarley1 on 2006-04-18
[QUOTE=ncappel1]oops, i forgot to add that then you have to add an mp3 profile in sound juicer. 

go to edit-->preferences-->edit profiles, if mp3 isn't there, then click on new profile. and make the profile name,  description and file extension "mp3" (without the quotes :p ) 

the Gstreamer pipeline should have: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

the "active?" box should be checked.

hope that works![/QUOTE]

Thanks!  I did not know this.  It's really true with Linux, you learn something new everyday!

---

