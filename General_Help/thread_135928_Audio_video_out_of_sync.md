---
title: "Audio video out of sync"
date: 2006-02-24
forum: General Help
---

### Post by motorbreath on 2006-02-24
When I play a DVD or other video file thru MPlayer the video & audio is slightly out of sync. 

Any ideas

---

### Post by ronmarley1 on 2006-02-24
Do you have DMA enabled for your DVD drive?  This might solve the problem with DVDs.  andrew's post below mentions a codec issue, and that may be the cause for other video files.  You may want to look at Automatix (here's the link: [http://ubuntuforums.org/showthread.php?t=66563)](http://ubuntuforums.org/showthread.php?t=66563)).  It will install just about all the codecs you need, and you can also have it turn on DMA at the same time.  I also agree with andrew, Xine with the Totem front end is what I use for DVDs.

---

### Post by andrewsawyer on 2006-02-24
This sounds like a codec issue.  Other than downloading all the codecs that you can from ubuntuguide.org, or trying a different player (give totem-xine a go) I don't really know what else to suggest.

---

### Post by motorbreath on 2006-02-24
DMA is definately on (thru Automatix) and all codecs are installed. 
Will try giving totem-xine a go.

Thank for the help

---

### Post by motorbreath on 2006-02-24
Beauty, totem-xine works perfectly

---

### Post by andrewsawyer on 2006-02-24
Great.  Thank you for letting me know.

---

### Post by PhoenixP3K on 2006-02-27
I had the same problem but then I changed the Audio Preferences in Mplayer I switched the sound from Alsa to ESD. You can also try turning ON AutoSync from the MISC tab. It did improve, it seems perfect (i guess)

---

### Post by ironmaiden6669 on 2006-02-27
Totem-xine is the only thing that worked for me, even just for mp3s.

---

