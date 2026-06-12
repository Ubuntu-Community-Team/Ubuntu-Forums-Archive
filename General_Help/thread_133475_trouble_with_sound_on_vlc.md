---
title: "trouble with sound on vlc"
date: 2006-02-20
forum: General Help
---

### Post by drop_d33 on 2006-02-20
ive downloaded brokeback mountain thru azureus.. it is a .bin file. i played the .bin file using vlc.. the audio is terrible.. it sounds like it has trouble loading or something.. the audio skips every second, so bad, that i cant understand anything.. is there anyhing i can do to fix this?

---

### Post by engla on 2006-02-20
I have no idea. I have the same problem with some of my bin files -- the same file worked well with the same version of vlc but in another install.

I don't know any solution so far...

---

### Post by nanotube on 2006-02-20
well, to check if its a problem with the file, or with vlc - try playing it with mplayer, and see if that changes things. if its still screwed up with mplayer, probably its a bad file?

---

### Post by aeiah on 2006-02-20
the .bin may not adhere to (s)vcd standards and thats why its having trouble playing it. a test with other applications will be the best thing to start with, as was previously mentioned. if it is an (s)vcd .bin file (it could be a dvd, you never said) then you can access the .dat file inside that is really just a renamed .mpg file. it'll be the massive .dat burried a couple of directories inside the .bin image. try playing that, and that'll help you determine whether its a problem with the disc standards, the mpeg encoding, or the player.

---

### Post by WillFerrellLuva on 2006-02-28
try typing "killall esd" from the command line, and then open vlc and try your file.

---

