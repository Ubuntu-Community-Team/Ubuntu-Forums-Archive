---
title: "Sound was working, but now it isnt!"
date: 2010-10-21
forum: General Help
---

### Post by akber on 2010-10-21
I recently isntalled Ubuntu 10.04 Lucid on my HP Compaq Presario CQ42. Recently being around two to three weeks ago. 

The first day I had it I didnt have sound due to my alsa version not being updated to 1.0.23 (something like that, i just know .23 was the version i upgraded to) and then along with another fix this solved my audio problem. There were a few issues with the audio after that, such as vlc and other app sounds not working after playing audio in a browser, requiring (as far as i know) a restart every time. This wasnt a big deal and i was getting around to finding out how to fix it but then today...

While at school I closed my laptop lid (as i usually do), but when i opened it again the screen flicked back and forth between some screens that usually show at boot (not bios, something else). Then Ubuntu told me that it didnt detect any of my drivers and that i should start in low graphics mode, and i did, but i made sure to select the just for this session option. I think this may have happened because I was running on low bat at the time but i cant be sure. When i restarted it booted up normally, and graphics and everything were back to normal except...

Since that happened my audio has not been working at all. The sound icon is still in the notification panel but there is nothing next to it, eg. volume level. Its not even "--" to indicate mute, there is just nothing there and when i got to sound preferences there is no device under hardware, and when i run the command aplay -l it says there is no sound card found. 

When i run the lspci -v | less command an audio device is clearly listed :
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
        Subsystem: Hewlett-Packard Company Device 1425
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

---

### Post by akber on 2010-10-21
bumpity bump bump

---

### Post by eze1969 on 2010-10-21
My classmate had the same issue with his Compaq. I suggested upgrading to 10.10 due to a lack of a better answer for him. We did a clean install of 10.10 and his sound now works. I know that's not a great answer...but it worked for my friend :)

---

### Post by akber on 2010-10-21
Thanks, I was actually going to try that and see what happened last night, but I figured I should try for a fix before I go to my last resort. 

I'll upgrade and let you know how it goes, thanks.

---

### Post by akber on 2010-10-23
HAZAAAAA, IT HAS BEEN SOLVED. Thank you very much.

---

