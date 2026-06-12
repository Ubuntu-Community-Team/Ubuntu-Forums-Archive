---
title: "Sound problem Ubuntu 10.10"
date: 2010-10-28
forum: General Help
---

### Post by scrubba777 on 2010-10-28
Hey

on a Toshiba Satellite M200
with Realtek ALC268 soundcard

started out with a problem using Ubuntu 10.04
On skype - one day my mic input went distorted, like digital clipping and i couldn't find out why or fix
I followed lots of discussion threads, and installed and reinstalled a bunch of things but nothing worked. 
Thinking i was in a bit of a mess, i decided to upgrade to latest
Ubuntu 10.10
still no better result - but now I notice I cannot easily change volume
- this may have already been happening in 10.04 - not sure..

When I click volume icon i get pop up
"waiting for sound system to respond"
then nothing. 

When I go to System / prefereces / Sound i get the same popup as above.

My volume control at front of computer no longer does anything

When I go to Applications / Sound & Video / Pulse Audio Volume COntrol
I get pop up - 
Connection failed: Connection refused

And still Skype is mic distorted..

Again i have tried trawling the forums, but have not been able to find anything that works

Any help greatly appreciated

---

### Post by matt_symes on 2010-10-28
Hi 

Can you remember what you have tried up until this point ?

Kind regards

---

### Post by scrubba777 on 2010-10-28
thanks for reply
I think in the main i have tried to reinstal ALSA and pulseaudio
plus tried a bunch of different addons 
like GNOME ALSA mixer which actually does allow me to change the volume.
but as i worked on this from time to time over the past month or so i may have forgotten some things,
thats why i tried the update to 10.10 - hopeing that may fix essentials i may have broken or left out..

---

### Post by matt_symes on 2010-10-28
Hi

Have you tried renaming the .pulse hidden folder (maybe .pulse_backup) in your home dir and rebooting your PC? Was your update to 10.10 a fresh install or an upgrade?

Kind regards

---

### Post by scrubba777 on 2010-10-28
yeah tried deleting .pulse folder - just tried to rename then, no change, and as expected it has created a fresh folder.

As for Ubuntu it was an upgrade from 10.04

---

### Post by scrubba777 on 2010-10-28
ANy new ideas would be greatly appreciated :)

---

### Post by matt_symes on 2010-10-28
Hi 

Have you tried using Alsa mixer. From the terminal type

alsamixer

For some people adjusting these controls have eliminated clipping.

Kind regards

---

### Post by scrubba777 on 2010-10-28
Thanks for the responses Matt

i have tried a little to play with it - with no immediate success- but will now look into it in more detail, and report back

---

### Post by tilugulilwa on 2010-10-29
i have a similar problem. i upgraded my ubuntu from 10.4 to 10.10 and i keep getting the message ....waiting blah blah ..

alsamixer seems to work though

Frank
TANZANIA

---

### Post by tsh on 2010-11-15
check the permisions on your home directory (ls -l /home). The owner (first name column after the d--------- nnn) should be your user name. 'sudo chown <username> /home/<username>' should fix it. Don't know how it happens, but mine seems to have been changed as part of an upgrade.

---

### Post by Crimbo on 2010-12-01
I can't seem to change my home folder permissions tsh. As much as I've tried entering in the line of code...

```
sudo chown <username> /home/<username>
```
(with my username in place)

It doesn't seem to change the permissions.

Am I typing it right?

I recently moved my Home folder to another partition, so I'm guessing that's why I'm having the same problems as scrubba777.

---

### Post by Crimbo on 2010-12-03
I've now noticed it's also affecting my Wine apps, and a couple other software. So it must be the permissions of the home folder.

If it helps, when I enter in 'ls -l /home', for my home directory it says...
```
d--------- 1 root root
```

How ever many times I type in (with my username in place)...
```
sudo chown <username> /home/<username>
```
...It won't budge.

It's so annoying not being able to control the volume, and now I've noticed the Wine apps aren't working, it's starting to really bother me. Anyone know what's going on?

**Edit:** Realised it is because my home folder is on a NTFS drive. Reason why I have put it on a NTFS is so my Windows 7 can read the same documents. I've looked to see if I can instead up it all on a FAT32 partition, but can't seem to find a valid answer. Anyone suggest the best way to share your documents between Windows and Ubuntu when you have a dual boot setup?

---

