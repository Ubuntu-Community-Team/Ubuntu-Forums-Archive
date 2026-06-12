---
title: "Sound Problems - Constant Static"
date: 2005-03-10
forum: General Help
---

### Post by the Blow Leprechaun on 2005-03-10
I'm pretty much a linux newb, so I'm hoping this is really an easy fix and I've just done something stupid.

When I first installed ubuntu and turned on my speakers, I heard static. I put in a CD (Johnny Cash - The Man Comes Around, for those interested) and it worked, but I still had static. I played around with the Volume Controls for a little while and found that if I turned PCM all the way down, the static went away. Great, but on to uglier problems.

I can't get sound from anything BUT CDs. I've got the codec to play mp3s, I've got music player and xmms both able to run the files, but I don't get any music. I had debian a few years ago and experienced the same problem (a major reason why I gave up for a while). From lscpi:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)

If you need me to find out something else, you'll probably have to tell me how to get at it. I spent a couple hours reading all the threads that were returned by searching for mp3 (hey, at least I knew I needed the codec and how to get it!), and finally gave up on trying to find what I'm looking for and decided to just post the question. Any help will be greatly appreciated, and might be rewarded with cookies. (No guarantee, express or implied, of cookies).

---

### Post by the Blow Leprechaun on 2005-03-14
I'm a little disappointed, everybody looked so helpful when looking at other people's questions... nobody knows how to help me get my sound working so I can finally make a permanent switch?

---

### Post by kassetra on 2005-03-14
[QUOTE=the Blow Leprechaun]I'm a little disappointed, everybody looked so helpful when looking at other people's questions... nobody knows how to help me get my sound working so I can finally make a permanent switch?[/QUOTE]

Ok, most likely the pcm is muted which is why you wouldn't be able to get any sound from mp3s and such.

Let's see if we can fix it here:
1. Right click on the little speaker that's in the top panel.
2. Left click on "Volume Control"

[color=Red]-- IF the menu comes up --[/color]
3. Check to make sure that the "PCM" sliders are somewhere in the middle.

[color=Red]-- IF YOU GET AN ERROR --[/color]
4. Type this in a terminal (Applications->System Tools->Terminal)
 ```
gst-register-0.8
``` 
Then try to adjust the sliders again in steps 1-3.

Test your sound.
If you have sound, I'll help you fix the static.

---

### Post by kassetra on 2005-03-14
[QUOTE=the Blow Leprechaun]I'm a little disappointed, everybody looked so helpful when looking at other people's questions... nobody knows how to help me get my sound working so I can finally make a permanent switch?[/QUOTE]

(it was the weekend, the sound help people might have been away... I know I was)

---

### Post by telmo on 2005-03-14
Ok, here's the thing... I'm using Hoary's preview. I'm not quite sure what static means... i'm not english... but my sound is definitelly broken. I can hear music but i can't hear the gnome sounds (or flash sounds in firefox for that matter), only the drums in the beggining and the music, nothing else... only if i'm already listening to music. Is there any way i can fix this?

In Warty all i had to do was upgrading the kernel, but in Hoary i tried that, and it didn't work. :S

---

### Post by kassetra on 2005-03-14
[QUOTE=telmo]Ok, here's the thing... I'm using Hoary's preview. I'm not quite sure what static means... i'm not english... but my sound is definitelly broken. I can hear music but i can't hear the gnome sounds (or flash sounds in firefox for that matter), only the drums in the beggining and the music, nothing else... only if i'm already listening to music. Is there any way i can fix this?

In Warty all i had to do was upgrading the kernel, but in Hoary i tried that, and it didn't work. :S[/QUOTE]

Ok, what's happening is that your system is currently (it would appear) using just OSS instead of ALSA or OSS+ESD... 
Your system right now will not allow multiple sounds.

[here's the thread to convert you from OSS to multi sound ESD]("http://ubuntuforums.org/showthread.php?t=18296&page=2&pp=10")

Let me know if that doesn't help.

---

### Post by Xian on 2005-03-14
[QUOTE=telmo]I can hear music but i can't hear the gnome sounds (or flash sounds in firefox for that matter), only the drums in the beggining and the music, nothing else... [/QUOTE]
You may still have polypaudio installed. 
To remove it open synaptic and choose to install the esound package.

---

### Post by telmo on 2005-03-14
[QUOTE=kassetra]Ok, what's happening is that your system is currently (it would appear) using just OSS instead of ALSA or OSS+ESD... 
Your system right now will not allow multiple sounds.

[here's the thread to convert you from OSS to multi sound ESD]("http://ubuntuforums.org/showthread.php?t=18296&page=2&pp=10")

Let me know if that doesn't help.[/QUOTE]

I tried it and it didn't work.

[QUOTE=Xian]You may still have polypaudio installed.
To remove it open synaptic and choose to install the esound package.[/QUOTE]

Nop.. I don't have it installed.

I'm sorry but i forgot to mention i have a ATIIXP 150 AC'97 Soundcard.
If you ran out of ideas, can you please tell me... if i compile the Kernel can i make the sound working? And if so, where can i get the instructions to compile the Kernel?

Thx and sorry to annoy you. :)

---

### Post by macewan on 2005-03-14
are the sounds metalic & echo sounding?

---

### Post by telmo on 2005-03-14
No... let me see if i can explain...

When i start Ubuntu, the sounds work nicely but then the gnome sounds don't work unless i have music playing. If i go to gnome sounds (System, preferences, sound) i can't hear the login sound event (for example) unless i click it several times. The sound is literally broken.

---

### Post by kassetra on 2005-03-14
[QUOTE=telmo]No... let me see if i can explain...

When i start Ubuntu, the sounds work nicely but then the gnome sounds don't work unless i have music playing. If i go to gnome sounds (System, preferences, sound) i can't hear the login sound event (for example) unless i click it several times. The sound is literally broken.[/QUOTE]

It's not the sound.  It's the sound daemon.  
Ok, if you've followed the thread - you should now have esd as your sound daemon.  The ac97 is supported just fine in warty, so it should be ok in hoary.

Try this:
1. Applications->System Tools->Configuration Editor
2. Navigate the tree to desktop->gnome->sound
3. Make sure both, "enable_esd" and "event_sounds" are both checkmarked.

---

### Post by telmo on 2005-03-14
[QUOTE=kassetra]It's not the sound.  It's the sound daemon.  
Ok, if you've followed the thread - you should now have esd as your sound daemon.  The ac97 is supported just fine in warty, so it should be ok in hoary.

Try this:
1. Applications->System Tools->Configuration Editor
2. Navigate the tree to desktop->gnome->sound
3. Make sure both, "enable_esd" and "event_sounds" are both checkmarked.[/QUOTE]

They are. :(

Hey... i just made 100 posts! Not all is lost! LOL

---

### Post by kassetra on 2005-03-14
[QUOTE=telmo]They are. :(

Hey... i just made 100 posts! Not all is lost! LOL[/QUOTE]

Ok, let's try some more things:

In gstreamer-properties, change the Default Sink to output: ESD - Enlightenment Sound Daemon

are you using xmms for your music?

(p.s. CONGRATS!)

---

### Post by telmo on 2005-03-14
:) Done that too... I'm using xmms/rhythmbox. When i have sounds running, the gnome sounds work ok, when i don't they break!
Should i try compiling the kernel now? (please say no! :) )

---

### Post by the Blow Leprechaun on 2005-03-15
My problem isn't that PCM is muted, it wasn't muted when it didn't work initially and I've since unmuted it several times.

A friend of mine believes that it's because something else is trying to use sound and that's preventing other things from using it, but I haven't been able to isolate and turn off whatever might be doing that.

Any other ideas on what it might be?

---

### Post by the Blow Leprechaun on 2005-03-15
When I do:
```
lsof /dev/dsp
```

Nothing comes up, but I still don't get sound. I very possibly could be using lsof wrong, or it might not even be pertinent, but I figured I'd post that I tried it.

---

