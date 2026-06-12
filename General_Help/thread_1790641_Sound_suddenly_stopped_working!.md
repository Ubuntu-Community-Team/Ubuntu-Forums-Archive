---
title: "Sound suddenly stopped working!"
date: 2011-06-25
forum: General Help
---

### Post by leilei1 on 2011-06-25
Hi,
I'm running 64-bit Ubuntu 11.04. I recently updated virtual box and wine. I also installed the expansion kit for the virtual box. 
Now Ubuntu doesn't read my sound card. I tried reinstalling alsa and pulseaudio but that did not help. 

aplay -l shows no sound cards. 

I have a Realtek ALC892 8-Channel HD Audio sound card.

Your help is much appreciated
   -Harry

---

### Post by Abir Valg on 2011-06-25
Does lspci recognize the sound card?

---

### Post by leilei1 on 2011-06-25
Yes this is the output for my sound card.

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

---

### Post by Abir Valg on 2011-06-25
Great news, your hardware seems to be intact. Can't help you further, though.
If I was you I'd go to [http://startpage.com]("http://startpage.com")
and searched the string that lspci gave you.

---

### Post by leilei1 on 2011-06-25
I found that I needed to install the OSS4 driver but when I checked synaptic it was already installed so I tried reinstalling it but that did nothing and I removed virtualbox followed by a reboot and still I have no sound.

It's very strange because my sound was working yesterday and now it suddenly stopped after the installs.

---

### Post by SoFl W on 2011-06-25
For the past few days I started my WindowsXP virtualbox (twice) and it gave me the error that there was a problem with the sound card in the host machine.  I wasn't sure what was going on, so I closed all virtual machines, and the Virtualbox (4.0.8)  program.  I then started up Banshee and it played a song fine.  The next time I started up Virtualbox and my Windows machine it played the Windows start up music and didn't give me an error. 

So is the sound problem you are having related to Virtualbox, or with the entire system?

---

### Post by leilei1 on 2011-06-25
This is in regards to my whole system, I was just stating that I recently updated virtualbox just in case that was the cause of the issue.

---

### Post by leilei1 on 2011-06-25
So I just ran a live cd of ubuntu, as a check if it was ubuntu or my sound card with the issue, and the audio was working from the live cd. After I rebooted my system back into Ubuntu on my HD the sound was magically working again!! :-o !! 

No idea as to why or how it just started working again. 
I'd still like to say thanks to those of you who tried to help me :)

---

### Post by lidex on 2011-06-26
if your audio just 'disappears', try removing the cruft from pulseaudio configuration:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

