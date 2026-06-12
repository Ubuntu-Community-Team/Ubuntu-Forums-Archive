---
title: "Laptop internal speakers work with oss but not alsa"
date: 2009-07-30
forum: General Help
---

### Post by THE_DEATH_M on 2009-07-30
Hello
I recently installed ubuntu 9.04 on my HP Pavilion DV3000 and I was thrilled to find out that almost everything worked with a little push here and there. But, after I added the appropriate options for the sound card, unlike my previous linux experience with the same laptop, the internal speakers still wouldn't work with alsa - only annoying scratching is produced. Switching to oss makes them sound ok, but we all know oss' flaws. Do you thing a simple manual upgrade of alsa would do the job or...?

---

### Post by Zorael on 2009-07-30
That sounds like a driver quirk. Head over to [http://ubuntuforums.org/showthread.php?p=5017453#post5017453](http://ubuntuforums.org/showthread.php?p=5017453#post5017453) and see if anything applies. Skip the top bit about volumes.

---

### Post by THE_DEATH_M on 2009-07-31
Well, first of all the option I used for snd-hda-intel is not listed in your post so I'm not sure how correct it is. Anyway, I changed to 3stact and I'll see if there is a result. But I think that as the speakers work, it should be a driver problem, not incorrect hardware detection...
EDIT: removing any additional options apart from enable_msi=1 did the job; this is very strange, considering that other distros would require the model option...

---

### Post by martinbaselier on 2009-07-31
You could switch to OSSv4. It will at least improve the quality of the sound.

---

### Post by THE_DEATH_M on 2009-08-01
Ok, alsa screwed up again so I decided to install oss4 following the extensive guide at help.ubuntu.com But now, sound is completely gone, neither the internal speakers of the laptop nor the headphones are working! I was hoping this solution would help, as oss3 seemed to have no problem handling the sound. Can you please help me fix that oss4?

---

