---
title: "Banshee autoplay on login"
date: 2009-10-22
forum: General Help
---

### Post by CaptainMark on 2009-10-22
Im trying to get banshee to start and play automatically on login. ive posted in the Absolute beginners forum but i think i need more advanced help. Heres the first post [http://ubuntuforums.org/showthread.php?t=1293766](http://ubuntuforums.org/showthread.php?t=1293766). Any ideas to help?

---

### Post by vinutux on 2009-10-22
System > Preferences > Startup applications 

click Add button  

Name : Banshee

Command : Banshee

Comment : music player


add it..... done

---

### Post by Giblet5 on 2009-10-22
Open a terminal window. Take a look at ```
man banshee
```

You can add a startup application (System->Preferences->Startup Applications on Karmic and others, or System->Preferences->Sessions on some others) that executes ```
banshee --play-enqueued
```

As long as you have a play queue established, it should do it. Try it out first...

---

### Post by CaptainMark on 2009-10-22
thanks but i think maybe you missed in the other post im trying to run 
banshee --hide 
then
sleep 15 && banshee --play
ive got these from man banshee already, banshee runs hidden but wont play, i tried to add a bash script to run the sleep and play command, but this only works if i turn on, login, logout and login again, then banshee runs and plays hidden. Something about x being initialzied which i dont understand sorry.

---

### Post by Giblet5 on 2009-10-22
> **CaptainMark said:**
> thanks but i think maybe you missed in the other post im trying to run 
banshee --hide 
then
sleep 15 && banshee --play
ive got these from man banshee already, banshee runs hidden but wont play, i tried to add a bash script to run the sleep and play command, but this only works if i turn on, login, logout and login again, then banshee runs and plays hidden. Something about x being initialzied which i dont understand sorry.

Sorry, didn't read your other post.

I just tested it. I have a folder in ./ called Sounds. Under that folder I have a file, THX-Grand.mp3, that plays one of the THX trailers.

```
banshee --hide --play-enqueued Sounds/THX-Grand.mp3
```
starts Banshee minimized and playing the file.

I would call it a bug that --play-enqueued refers to filenames passed on the command line, but that does work and seems to match what the --help-playback documentation says it does.

---

