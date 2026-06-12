---
title: "Sound problems with spotify? Here's a SOLUTION"
date: 2011-02-23
forum: General Help
---

### Post by Spyderkid on 2011-02-23
[SIZE="4"]You need to go into
[/SIZE]
[SIZE="3"][COLOR="Red"]Wine[/COLOR] > [COLOR="Blue"]Wine 

[SIZE="2"][/SIZE]configuration[/COLOR] > [COLOR="Orange"]Audio[/COLOR] [COLOR="Blue"]THEN...[/COLOR][/SIZE]

[COLOR="SeaGreen"]> Tick the ALSA driver[/COLOR]
[COLOR="Purple"]> choose Emulation on Hardware Acceleration[/COLOR]
[COLOR="Blue"]> Make the default sample rate 44100 (IF IT ISN'T ALREADY)[/COLOR]
[COLOR="Red"]> Make the default bits per sample 16 (IF IT ISN'T ALREADY)[/COLOR]

_**If it doesn't seem to work you may need to re-install spotify then it will. **_






[SIZE="3"]**_[COLOR="Red"]Have any problems with installing?... [visit here]("http://ubuntuforums.org/showthread.php?t=1692341")[/COLOR]_**[/SIZE]






_Any questions or comments i'm happy to listen to._

---

### Post by thebrandon on 2011-08-31
I have followed the instructions and I still keep coming up with the same error "There is a problem with your soundcard.  Spotify cant play music".  I know that sound works on my laptop but I havent used wine for anything else really so I dont know if I have it set up wrong.

---

### Post by Spyderkid on 2011-09-04
did you re-install spotify?

---

### Post by thebrandon on 2011-09-06
Yes I have reinstalled multiple times with the same result.  I went back and made extra sure I had everything in the audio tab correct and still nothing.  I am doing the uninstall through the wine uninstaller and also when I rebooted my system because I killed spotify but wine wouldnt let me reopen it the audio settings for alsa and oss were checked when I looked again.  As a side note it also refuses to play local mp3's saying unsupported format.

---

### Post by Spyderkid on 2011-10-19
im not quite sure then, sorry.

all i can suggest is that you've got emulation on and got the sample rates right.

---

### Post by realitykid on 2011-10-27
Well, if you can't get Spotify to work in WINE (I couldn't either), then you could try what I did, which seems to work.

Install VirtualBox and create a virtual machine with Windows XP, Vista, or 7 and install Spotify inside the virtual machine. It's working pretty well for me, aside from a few artifacts in the audio.

I sure hope they can make a Linux client available for the Free users soon.

---

### Post by cespinal on 2011-10-27
TRUE solution:

Grooveshark.

---

### Post by realitykid on 2011-10-27
> **cespinal said:**
> TRUE solution:

Grooveshark.

And the Pandora desktop client for Linux, Pithos.

However, the music on Spotify is higher quality sometimes, and they have more content, and an easier to use interface than Grooveshark,

Grooveshark also has a lot of duplicate content and crappy search function. Makes it hard to find what you want. But I do use it from time to time.

And there is a Linux command line client for Spotify if anyone wants to take a look at that.

[http://www.makeuseof.com/tag/spotifys-free-version-working-linux/](http://www.makeuseof.com/tag/spotifys-free-version-working-linux/)

---

### Post by Spyderkid on 2011-10-28
I'm still not sure why spotify wont work with you, it works fine for me, you wouldn't be able to tell the difference from windows. :S

---

