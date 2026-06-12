---
title: "Amarok refuses to play"
date: 2010-02-18
forum: General Help
---

### Post by volatilepyro on 2010-02-18
I got amarok and it seems like it would be cool, however, it refuses to play any music. It acts like it plays but it will just show the bar like a 4 minute long song played in three seconds and then stops. Anyone else with this problem or a solution???

---

### Post by VastOne on 2010-02-18
> **volatilepyro said:**
> I got amarok and it seems like it would be cool, however, it refuses to play any music. It acts like it plays but it will just show the bar like a 4 minute long song played in three seconds and then stops. Anyone else with this problem or a solution???

Does any other player these same songs OK?

---

### Post by Vakman on 2010-02-18
By any music, are they all MP3 files? Or have you tried other formats. Be sure you have the Ubuntu Restricted Extras package installed if they are MP3s or other. If you do comment back here and I will try to be of further assistance.

---

### Post by volatilepyro on 2010-02-18
Yeah rhythmbox plays them all fine. I think they're all mP3s but there is a possibility of some being something else.

---

### Post by Vakman on 2010-02-19
Hm, if Rhythmbox plays them fine then it is not the restricted format. I have read that if you (in Amarok) go to preferences and then change the engine to Xine. Not sure if this is still an option as I do not use Amarok.

---

### Post by Swagman on 2010-02-19
```
sudo apt-get install phonon-backend-xine 
```

Google led to here... [http://ubuntuforums.org/showthread.php?t=1307762](http://ubuntuforums.org/showthread.php?t=1307762)

I remember having this problem as well but couldn't remember how I solved it. That code does sound familier.

---

### Post by volatilepyro on 2010-02-19
All right, I went into the configuration and it says Xine already.

---

### Post by volatilepyro on 2010-02-28
All right so I've tried the code and it's already running on Xine with the latest version and it still does the same thing.

---

### Post by mc4man on 2010-02-28
While I keep my distance from amarok 2 (except to test) try this and see if it's installed

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by volatilepyro on 2010-03-01
That did it, thanks man!!!

---

### Post by volatilepyro on 2010-03-01
I spoke too soon, it will play the song fine for a little while and then will start this poppling noise.

---

