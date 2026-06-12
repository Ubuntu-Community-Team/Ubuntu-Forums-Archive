---
title: "Speakers are very loud after Ubuntu install."
date: 2010-06-22
forum: General Help
---

### Post by MuradKakish on 2010-06-22
So, I just recently installed Ubuntu and I tried to go watch a YouTube video and I noticed my speakers weren't working. Then I raised the volume from Mute to "1", no sound, then to "2", again no sound. Then I went to "3" and the sound came on but it was *ridiculously* loud. 
It does this with all sounds from my computer, the first 2 notches don't emit any sound but the third and above emit sound at a *very* high level.

Any idea how I can fix this?

Running a Dell Precision M90 Notebook.

Never had a problem when running my Windows 7 boot, only my Ubuntu boot.

---

### Post by -humanaut- on 2010-06-22
Check the sound preferences and check the levels of PCM and MASTER lower the PCM until your sound is closer to what you want.

---

### Post by J V on 2010-06-22
I submitted a bug report... Whats actually happening: At 0 it's cut power to the speakers, at 1 it's powered but no signal, at 2 it's finally turned on...

[https://bugs.launchpad.net/hundredpapercuts/+bug/596705](https://bugs.launchpad.net/hundredpapercuts/+bug/596705)

This can also create a large pop if you turn down the volume to the point where it cuts the power...

---

### Post by Rodney9 on 2010-06-22
Thanks to LordRaiden

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Using alsamixer

    * Type this into a shell
      Code:

      alsamixer

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

    * To navigate around:
          o Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
          o
            Up and Down Arrow Keys - Increase and decrease volume respectively.
          o
            Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.

Saving Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.-

---

### Post by MuradKakish on 2010-06-22
> **Rodney9 said:**
> Thanks to LordRaiden

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Using alsamixer

    * Type this into a shell
      Code:

      alsamixer

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

    * To navigate around:
          o Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
          o
            Up and Down Arrow Keys - Increase and decrease volume respectively.
          o
            Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey.

Saving Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.-
So, I did this and I got my settings correct, but when I save them, I try and use the raise volume button on my computer and it goes back to the original settings.
Am I saving it incorrectly? When I am on the alsamixer screen in terminal, It does not give me a text field to enter "sudo alsactl store 0" and save it. It's just the alsamixer only.

---

### Post by WorMzy on 2010-06-22
Use that code after you've finished getting alsamixer how you want it and pressed Esc. Your soundcard's settings will persist even after alsamixer has been closed.

---

### Post by MuradKakish on 2010-06-22
> **WorMzy said:**
> Use that code after you've finished getting alsamixer how you want it and pressed Esc. Your soundcard's settings will persist even after alsamixer has been closed.
It still doesn't work, it keeps it at the levels I chose until I use my shortcut key again. Then it becomes very loud again.

---

### Post by MuradKakish on 2010-06-24
Up.. still need help.

---

