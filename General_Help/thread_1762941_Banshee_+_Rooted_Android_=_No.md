---
title: "Banshee + Rooted Android = No"
date: 2011-05-19
forum: General Help
---

### Post by .psd on 2011-05-19
Banshee doesn't recognize my device or list any media on it. Banshee doesn't even *see* my HTC Evo unless I switch the Evo into Disk Drive mode, then Banshee sees the Evo as "8.0 GB Filesystem" instead of what I see in screenshots where Banshee recognizes the phone: "HTC Android Phone". Banshee categorizes all the used space on the Evo as "other" (i.e. not audio/video). In Banshee's device properties for the 8gb filesystem, it properly lists the product as "Android_Phone" and the Vendor as "HTC", but none of the folders listed for music or video are correct.

I got the impression that if the Android device is rooted, then it needs a .is_audio_player file, so I tried a few different .is_audio_player with different code copied from various sites. Nothing. Perhaps I'm putting the wrong code into the .is_audio_player file?

Ubuntu 11.04
HTC Evo, rooted if that matters, running MikFroyo 4.62 ROM if that matters

---

### Post by .psd on 2011-05-19
Is the problem with Ubuntu or Banshee, or with all media players for Ubuntu (i.e. Rhythmbox etc.)?

---

### Post by johnnybgoode83 on 2011-05-19
Try Rhythmbox.  It picked up my HTC Desire with no problems

---

### Post by .psd on 2011-05-19
Will do, although I see a lot of comments about the Desire being recognized even by Banshee, straight OOTB.

Is your desire rooted? It may be important to note that mine is, and where I've seen this discussed the problem tended to be with rooted phones.

Is Rhythmbox lightweight, and does it integrate with the volume control in the notification area the way Banshee does?

---

### Post by .psd on 2011-05-19
I ended up getting the .is_audio_player solution to work.

Instead of what other people said, I simply made the file empty to see what happens. By default it will cause music to be found in the Music folder. So I added this single line to direct it to more folders.

```
audio_folders=Music/,mp3download/,PC2EVO/
```

Of note, it also finds video files (the only ones I have so far are mp4, but they are definitely listed in Banshee under the Videos menu for my device.

---

