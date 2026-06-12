---
title: "My Philips MP3 player is giving me a hard time"
date: 2009-10-17
forum: General Help
---

### Post by JugglinPhil on 2009-10-17
Hi everybody, I've got a Philips HDD14XX GoGear Mp3 player, it is kinda old and has only got 4gig of memory. However I'm happy with it and don't really have the money to get a new one right now. 
Now my problem: When I plug it in it is recognised and shows up on the desktop with the correct labelling and everything, however no music player I tried was able to sync with it. My preferred player is Songbird, and on the official site it says that the player is supported, but unlike my brothers ipod it does not show up.. 
Btw I've got access to the player's content via nautilus, but thats no real solution..

---

### Post by wilee-nilee on 2009-10-17
This might help, <a href="http://ubuntuforums.org/showthread.php?t=570121The" target="_blank">[http://ubuntuforums.org/showthread.php?t=570121](http://ubuntuforums.org/showthread.php?t=570121)

---

### Post by JugglinPhil on 2009-10-17
Yes I have already seen this thread, but my problem is different. I am able to mount it and I do have access to it, but it doesn't show up in any media player, so I can't sync it...

---

### Post by StuartN on 2009-10-17
> **JugglinPhil said:**
> I am able to mount it and I do have access to it, but it doesn't show up in any media player, so I can't sync it...

Is it supposed to show up? The Philips SA32xx is just a USB mass storage device, not MTP, so I am not sure how the media player is supposed to recognise that it is not just a disk.

I have one of these and I occasionally delete some space and copy fresh stuff on. I never expected it to synch.

---

### Post by JugglinPhil on 2009-10-17
Not sure, I thought it was MTP because it's an MP3 player and not an ipod, but looks like i'll have to look up the right definition... ;) Anyway, it used to sync with wmp back in windows so i tried running that under wine, which was quite a fail, but it looks like there's no substitute. I'll try just copying and will report back.

---

### Post by kostkon on 2009-10-17
Create a empty file called *.is_audio_player* on your device to make the various media players see it as an audio device.

---

### Post by JugglinPhil on 2009-10-17
> **kostkon said:**
> Create a empty file called *.is_audio_player* on your device to make the various media players see it as an audio device.
Wow thanks a lot that worked, it does not in Songbird, but that is rather minor. At least it works. :) Copying the files works as well by the way, just tested that, but of course this is way better.

---

### Post by wilee-nilee on 2009-10-17
Good to see that you have found a working solution, I have a gogear as well, and it syncs through rhythmbox by by just linking it via edit-preferences music then loading the player.

---

