---
title: "flash player now opens  sound device in &quot;exclusive&quot; mode?"
date: 2011-02-23
forum: General Help
---

### Post by BertP on 2011-02-23
everything was working fine for years on my 8.04 LTS system until a recent system update using update manager :frown:

now it is as if flash opens the sound mixer in "exclusive" mode


for instance, 
now I get no sound in flash if it is started while a program using sound is already open (such as VLC, gnome MPlayer, etc.)   AND  
  i do get sound  with flash if all sound apps are closed when a flash browser is opened but if I start any program using sound while a flash browser is already open, that program plays no sound.   EVEN system->preferences->sound will not play the test tones 
with a flash browser already playing

Anyone know how to fix this???

---

### Post by BertP on 2011-03-02
bump

---

### Post by BertP on 2011-03-06
come om guys! As a former programmer (non-Linux) My intuition tells me that it is highly probable that this can be fixed by making some simple adjustments in some configuration file.... most  likely of  the flash component.    

Does anybody know about those settings?  or can tell me with confidence that my intuition is wrong here?   
-----------


I suppose is is still that case that after all these years that that  Ubuntu is **still not ready for the desktop of the "average" user;** . 

  Even if one gets his system set-up like he wants, the "Update Manager" is going to eventually throw a curve ball that the "average" user won't be able to handle  :frown:

---

### Post by peterpan7191 on 2011-03-30
having same problem,
vaio F series - core i7,
distro - lucid lynx

---

### Post by dwille on 2011-03-31
BertP,

I was struggling recently with getting the Adobe Flash Player to play sound from the correct device on my computer. Firefox itself would play sound out the correct device, but not Flash. I believe this may be because Flash talks right to the default ALSA device rather than going through the PulseAudio sound mixer as it should.

I edited /etc/asound.conf to include the following:

```
# Select PulseAudio as the default sound device
pcm.!default {
    type pulse
}
```

Then restarted. Then, I fired up Firefox and started a Flash app (Pandora, actually). Flash used my correct sound output. At this point, when I open System -> Preferences -> Sound and go to the Applications tab, I see an entry listed as "ALSA plug-in [npviewer.bin]" which controls sound volume for Flash, and if I go to the Output tab, I can use the radio buttons there to switch between my HDMI audio output and my bluetooth audio output.

Hopefully this will work for you! I found the following ALSA reference useful for figuring this out:

[http://en.gentoo-wiki.com/wiki/PulseAudio#Flash_support](http://en.gentoo-wiki.com/wiki/PulseAudio#Flash_support)

---

### Post by BertP on 2011-04-01
dwille    
 I may have made a mistake but the fix you described didn't seem to work  BUT I am still better off now!

First I didn't have an asound.conf in my etc directory and adding one didn't seem to have an effect after rebooting.  I deleted it and looked again at System->Preferences->Sound and changed all the combo boxes from "Autodetect" to "Alsa" and then rebooted.

Afterwards a flash-playing browser and VLC together have the same problem that I described in my fist message... BUT then I happened to press a "test" button in the "sound preferences" applet while playing a youtube video and I  heard both sounds at the same time! I then tried "totem" and it worked too,,,, so while the problem still persists I can work around by setting all my sound preferences to "Alsa" and by using totem instead of VLC to play those long podcasts that I listen to regularly. If I want to pause a podcast and watch (as well as listen) to a youtube video, I can do so once again!

Thanks!

---

### Post by jpaden on 2011-05-22
Kind of curious if anyone knows much more about this?  I noticed today after patching 10.04 LTS (been a while since patching this particular box) that Flash now wants to open my Line-In device from my sound card as an exclusive lock.  That's bad for me because, until today, I was using the box to record audio in Audacity and webcast the audio feed via Flash at the same time.  If there is a fix for getting Flash to read from the line-in in non-exclusive mode, that would be fantastic.  Otherwise, I'll probably have to attempt to use JACK to route the audio input to both programs.  Never used JACK before, so not sure how long it would take me to figure it out.

Any ideas?  Thanks!
-JP

---

### Post by linuxinstalledfromhdd on 2011-05-22
Bump!

---

### Post by Scoobie_snack on 2011-07-24
Got the same thing happening. Flash will play great if the browser opens before mplayer or vlc but if one of those are opened first, no sound in flash. If flash starts first, no sound in any other programs. I have to kill the browser to get sound back on the others :(

I'm running x64 Natty

---

