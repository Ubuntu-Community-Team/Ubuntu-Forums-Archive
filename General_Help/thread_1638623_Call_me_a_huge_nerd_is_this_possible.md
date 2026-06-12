---
title: "Call me a huge nerd: is this possible?"
date: 2010-12-05
forum: General Help
---

### Post by 0949er on 2010-12-05
Ok guys call me a huge nerd, but I have official control of my computer on my HTC Evo (via ssh) and I am ecstatic. I seirously just rebooted my computer for the hell of it.

Anyways, I am trying to figure out some creative uses of this little trick. I listen to music a lot, and figured "hey, wouldn't it be cool to be able to change the song playing on my computer with the command line some how?" I use rthymbox to play songs, however, am not sure if this is/will be possible.

How can I go about changing the current playing song with the command line? Is there perhaps a shell based music player that can play audio though the computers audio output (while I run the command from my phone)?

Lots of questions. Please help!

---

### Post by Foxheadz on 2010-12-05
[http://ubuntuforums.org/showthread.php?t=326350](http://ubuntuforums.org/showthread.php?t=326350)

---

### Post by Girya on 2010-12-05
cmus is a great console music player. I'm not sure that you can ssh in and control audio output to your desktop.

---

### Post by loell on 2010-12-05
heh, your nerd level didn't even registered in the nerd scale. :P


[http://code.google.com/p/rhythmote/](http://code.google.com/p/rhythmote/)

of course, Evo comes with a browser surely. :)

---

### Post by 0949er on 2010-12-05
> **loell said:**
> heh, your nerd level didn't even registered in the nerd scale. :P


[http://code.google.com/p/rhythmote/](http://code.google.com/p/rhythmote/)

of course, Evo comes with a browser surely. :)

yeah that is what I want to do.... but I want to do it remotely from my phone w/out the browser. I trust the security better over ssh.

Big question, does a user have to be part of a specific "group" to be able to play music?

---

### Post by smeggs on 2010-12-05
> **0949er said:**
> yeah that is what I want to do.... but I want to do it remotely from my phone w/out the browser. I trust the security better over ssh.

Big question, does a user have to be part of a specific "group" to be able to play music?


No, I don't think they do. Even minimal users can use rhythmbox, but it's the location of the music files and the permissions of them that matter. I set my music directory to /usr/share/Music and give everyone +r.

---

### Post by Vaphell on 2010-12-05
if you really want to control rhythmbox from command line [http://ubuntuforums.org/archive/index.php/t-436392.html](http://ubuntuforums.org/archive/index.php/t-436392.html)

---

### Post by 0949er on 2010-12-05
> **smeggs said:**
> No, I don't think they do. Even minimal users can use rhythmbox, but it's the location of the music files and the permissions of them that matter. I set my music directory to /usr/share/Music and give everyone +r.

when I run(From phone):

```

xxxxxx@power-house:~$ mpg123 1.mp3

```It acts like it is playing the song (with no errors) but I hear no sound on my speakers. If I run the same command in the terminal on my physical computer (as another user) it works perfectly.

```

swooshonln@power-house:~/Music$ groups swooshonln
swooshonln : swooshonln adm dialout cdrom plugdev lpadmin admin sambashare

``````

swooshonln@power-house:~/Music$ groups xxxxxxxx
xxxxxxxx : xxxxxxxx

```

So which group will allow output of audio?

---

### Post by 0949er on 2010-12-05
> **0949er said:**
> when I run(From phone):

```

xxxxxx@power-house:~$ mpg123 1.mp3

```It acts like it is playing the song (with no errors) but I hear no sound on my speakers. If I run the same command in the terminal on my physical computer (as another user) it works perfectly.

```

swooshonln@power-house:~/Music$ groups swooshonln
swooshonln : swooshonln adm dialout cdrom plugdev lpadmin admin sambashare

``````

swooshonln@power-house:~/Music$ groups xxxxxxxx
xxxxxxxx : xxxxxxxx

```So which group will allow output of audio?


If i SSH in with the current logged on user (swooshonln) and run:

```

swooshonln@power-house:~$ mpg123 1.mp3

```

I get sound!!! now how do I make it so that the other user "xxxxxxx" can now play audio over the speakers that swooshonln is using?

---

### Post by 0949er on 2010-12-05
> **0949er said:**
> If i SSH in with the current logged on user (swooshonln) and run:

```

swooshonln@power-house:~$ mpg123 1.mp3

```I get sound!!! now how do I make it so that the other user "xxxxxxx" can now play audio over the speakers that swooshonln is using?


OK! Fixed it, xxxxxx can now play sound over the speakers. Had to add the user to the "audio" group.

```

xxxx@power-house:~/$ sudo gapsswd -a xxxxxx audio

```*Must be a member of /etc/sudoers to use sudo

Thanks for the brain storm.

---

### Post by loell on 2010-12-11
should you feel tired on typing those music files, you can also try

[http://sourceforge.net/apps/trac/android-tesla/]("http://sourceforge.net/apps/trac/android-tesla/")

---

