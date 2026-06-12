---
title: "Can't play music from FrostWire any more"
date: 2010-06-05
forum: General Help
---

### Post by steve509 on 2010-06-05
Hello all, I'm running ubuntu 9.10 and I used to be able to play the downloaded music from FrostWire. Now when i try I get an error message saying: FrostWire could not launch the specified file.
                Executed command: vlc /home/steve/FrostWire/saved/Pink Floyd -Welcome to the Machine.mp3

Anybody know why this might be happening now?? Any help would be greatly appreciated

---

### Post by tgalati4 on 2010-06-05
You need quotes around the filename if it contains spaces.

Open a terminal:

vlc "/home/user/music/pink floyd hole in the       wall.mp3"

---

### Post by steve509 on 2010-06-05
Shouldnt it just play from inside FrostWire like it always did??
I'm not typing that into terminal if thats what you are thinking...Please be gentle, i'm still a newbee lol

---

### Post by Spr0k3t on 2010-06-05
What he is saying is the filename needs to be escaped.  So sending VLC the filename "pink floyd hole in the wall.mp3" without the quotes will look like "pink" the next file will be called "floyd" and so on until it reaches "wall.mp3".

So, escaping the filename can be done with quotes around the filename, or by using an escape sequence such as: pink\ floyd\ hole\ in\ the\ wall.mp3 will work without quotes.

I don't use frostwire, so I'm not sure what the settings are to change the external players.  Dig around in the preferences to see if you can find it and then put quotes around the filename argument.

---

### Post by tgalati4 on 2010-06-05
Obviously, something changed in the file handling that frostwire uses to pass music to vlc.  vlc is just the player.  When you click play in frostwire, it sends the name of the file to vlc to play.  I don't use frostwire either, so you will have to do some more research.  Spr0k3t's explanation is more appropriate than mine.  Try to cut and paste the command from the error message and you will see why linux is not happy with it.  The put quotes around it.  Like this: 

($ is your prompt at the terminal.)

```

$vlc /home/steve/FrostWire/saved/Pink Floyd -Welcome to the Machine.mp3

```

Now try:

```

$vlc "/home/steve/FrostWire/saved/Pink Floyd -Welcome to the Machine.mp3"

```
What changes have you made to the system recently?  Check if vlc is installed.

```

sudo apt-get install vlc

```

My previous response was on a mobile device (n800)--difficult to make detailed replies. Can I have my puddin' now?

---

### Post by steve509 on 2010-06-05
Thank you all for replying. I looked in the otions menu  and it seems that under the "Player", the "Use FrostWire Media Player" was unchecked. When I checked it, it worked just fine...Thanks so much for all your help.

God I love this place...keep up all the great work in helping idiots like me
Steve509

---

### Post by steve509 on 2010-06-05
Sorry but I'm not sure how to make this appear as solved...can someone please explain?

---

### Post by Spr0k3t on 2010-06-05
Just above your first post is a drop-down labeled "**[COLOR="Red"]Thread Tools[/COLOR]** [IMG]http://ubuntuforums.org/images/misc/menu_open.gif[/IMG]".  Click that and you should see the "Mark thread as solved" option.

---

### Post by tgalati4 on 2010-06-06
So it looks like you have found a bug in frostwire.  The work-around is to use the built-in player.

There are no idiots in open source only those who don't know.  It's up to you to share what you know and help others.  In a year's time, you will be an expert.

---

### Post by z-itou16 on 2010-07-28
Hello folks,

I have experienced the same issue with Karmic and Lucid now. So, I troubleshooted a little the problem and definetely is not a codec issue (of course if you have the proper codecs for your PC).
Second, I do not believe is my ALSA/OSS/PulseAudio that is not working correctly, as I have audio with multiple apps (chrome/firefox/opera/rhythmbox) all at the same time.

So then I decided, why not test it while all apps are not using audio API. Then I found something interesting, the internal Frostwire player played just fine but then, I tried to open another app, no audio on the other app.

To continue, I close Frostwire and Java process and then restart my other apps and got audio on my apps again.

So it seems to be that ALSA does not handles well Java calls or vice verse.

Wish I could say more specific but that is all could find myself. If I could try to read code more in depth, maybe I could come out with something better.

Give a test folks.

---

