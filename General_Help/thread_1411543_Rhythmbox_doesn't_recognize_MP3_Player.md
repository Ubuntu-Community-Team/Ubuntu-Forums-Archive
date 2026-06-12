---
title: "Rhythmbox doesn't recognize MP3 Player"
date: 2010-02-20
forum: General Help
---

### Post by JugglinPhil on 2010-02-20
No media player recognizes my Philips MP3 Player as such, I've put all my hopes into Rhythmbox, it seems to be the most likely one to work. 
Anyway, I have created the empty .is_audio_player file but still the player does not show up in RB. 
I can access the player just fine through Nautilus, and syncing it actually worked for a while, but now for some reason it has stopped.
Can anybody assist me with this one?
Thanks

Edit: Almost forgot, the player is called 'Phillips HDD1420'  (4Gig) if that is of any relevance..

---

### Post by JugglinPhil on 2010-02-20
MTP-support is activated in Rhythmbox, but clicking on 'Scan removable medai' doesn't seem to do anything at all.

---

### Post by JugglinPhil on 2010-02-21
Bump

---

### Post by JugglinPhil on 2010-02-22
Just wondering, is this thread not being viewed or is it just that no one knows a solution?

---

### Post by Giwex on 2010-02-22
Is MTP activated in your MP3 player as well?

---

### Post by JugglinPhil on 2010-02-22
I don't know, but there doesn't seem to be an option to switch it on or off.

---

### Post by JugglinPhil on 2010-02-22
Update: I restored factory settings on the player and removed everything that was not originally on it, still no luck. In Rhythmbox I can see the player when I go to 
"Music -> Import Folder..."
but I again that's only Nautilus and does not help with the issue.

---

### Post by NCLI on 2010-02-22
> **JugglinPhil said:**
> Just wondering, is this thread not being viewed or is it just that no one knows a solution?

The problem is that the solution usually changes with the hardware. If no one here has the same MP3-player as you, it's hard to give advice.

---

### Post by JugglinPhil on 2010-02-22
> **NCLI said:**
> The problem is that the solution usually changes with the hardware. If no one here has the same MP3-player as you, it's hard to give advice.
Hm yeah good point. Anyway, maybe I'm lucky.

---

### Post by JugglinPhil on 2010-02-23
bump

---

### Post by JugglinPhil on 2010-02-24
Maybe I should just buy an iPod...

---

### Post by Giwex on 2010-03-08
If you want to be free from closed source solution forget the ipod. My suggestion is to go to a Cowon. I have an I7 and it's fully compatible with Linux, it has a superb sound and plays ogg. :p

---

### Post by JugglinPhil on 2010-03-09
The thing is I don't want some fancy touchscreen thingy with video and whatever features because I can't afford it, I just want to listen to some music, which is why I am so desperately trying to revive my old one.

---

### Post by chutem on 2010-11-21
Maybe this could help find a solution. I am new to Ubuntu, and really want it to work out, however i have similar issues with my GoGear Aria 4gb.

The thing is, if I set it to use MTP, it comes up in Rhythmbox and recognises all the music I have on it, however when I try to play any file, it says it can't find the path. With MTP, it does not show up anywhere else.

If I set it to use MSC, it does show up as a usb device, and I can play music through the file browser with Rhythymbox etc, but it does not show up in Rhythymbox as an mp3 player, I have looked around and tried the ".is_audio.player", but that did not work.

Looking forward to possible solutions.

---

### Post by needeffexor on 2011-01-02
> **chutem said:**
> Maybe this could help find a solution. I am new to Ubuntu, and really want it to work out, however i have similar issues with my GoGear Aria 4gb.

The thing is, if I set it to use MTP, it comes up in Rhythmbox and recognises all the music I have on it, however when I try to play any file, it says it can't find the path. With MTP, it does not show up anywhere else.

If I set it to use MSC, it does show up as a usb device, and I can play music through the file browser with Rhythymbox etc, but it does not show up in Rhythymbox as an mp3 player, I have looked around and tried the ".is_audio.player", but that did not work.

Looking forward to possible solutions.

@chutem:  Did you try .is_audio_player (instead of .is_audio.player) in the parent directory of the device?  I have had success with several obscure devices by adding this file, but it does not work if you put the file in the music directory of the device.  I am using rhythmbox 0.13.1 (Ubuntu 10.10) but it has also worked with previous versions.  I know that these posts are old, but I hope that it helps.

---

### Post by Toxicbits on 2011-01-06
Thank alot! Adding the .is_audio_player file helped

---

