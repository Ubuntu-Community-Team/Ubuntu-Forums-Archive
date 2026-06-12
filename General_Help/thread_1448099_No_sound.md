---
title: "No sound"
date: 2010-04-06
forum: General Help
---

### Post by w3dge on 2010-04-06
Hi all,
just installed ubuntu as a dual boot with vista but to my dismay i have no sound.
i am a complete newb at linux so any help is greatly appreciated
cheers

---

### Post by nothingspecial on 2010-04-06
Well the first step would be to post what soundcard you have. Go to your menu and click accessories > terminal. Then type ```
aplay -l
```

Then copy and paste what it says here.

---

### Post by w3dge on 2010-04-06
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by w3dge on 2010-04-06
There has been no sound since I installed ubuntu 9.10 at all,not even at startup if that helps.

---

### Post by nothingspecial on 2010-04-06
Next step

Go system > administration > hardware drivers and see if there is anything in there.

Then (in your terminal again) type ```
alsamixer
``` and see if anything is muted. There will be a MM at the bottom if something is.

Navigate between the channels with the arrow buttons. Press M to unmute or mute. 

Turn everything up with the arrows again.

---

### Post by w3dge on 2010-04-06
i unmuted everything with mm and put it to full volume but I still cant get sound

---

### Post by nothingspecial on 2010-04-06
Make sure you are a member of the audio group


sudo adduser *your_username* audio

---

### Post by w3dge on 2010-04-06
ok i had to restart my pc so i could install driver updates but after i did i cant actually boot ubuntu. I had to go back to vista
this is the message i get after selecting ubuntu and the generic ubuntu option:

[ 1.772486] Kernel Panic -Not syncing :VFS: Unable to mount root FS on unknown Block (8,1)

Any ideas?
thanks in advance

---

### Post by nothingspecial on 2010-04-06
Do you have the option to boot previous kernels when you restart.

Ubuntu 9.10 then the lowest number

---

### Post by w3dge on 2010-04-06
I managed to boot into ubuntu using a lower kernel.
I added myself to the audio group but I still cant get any sound.
Sorry for being such a newb :(

---

### Post by nothingspecial on 2010-04-06
> **w3dge said:**
> I managed to boot into ubuntu using a lower kernel.
I added myself to the audio group but I still cant get any sound.

Ok, I`ve shown you the basic sound troubleshooting methods. Your next best step is to google the output of aplay -l with ubuntu, there`s some stuff out there, I`ll have a look myself if I have time.

> **w3dge said:**
> Sorry for being such a newb :(

Don`t appologise for that. I`m sorry your sound doesn`t work. And I`m especially sorry that a kernel update screwed your entire system. Do not remove the kernel that works, whatever you do.

---

### Post by lidex on 2010-04-06
For your kernel panic:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24")

---

### Post by w3dge on 2010-04-06
Ive tried looking at step by step guides to troubleshoot but all to no avail.
Im completely lost here

---

### Post by lidex on 2010-04-06
For sound problem:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by w3dge on 2010-04-06
Tried everything on that list and nothing has worked.
Really confused as to how nothing is working.

---

### Post by lidex on 2010-04-06
That's pretty much all of the basic stuff. We'll need more info to troubleshoot. If you would please, right-click on the alsa-info link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by w3dge on 2010-04-06
I tried updating alsa for a second time using one of the links you posted and i finally got it working.
Thanks for all the help guys!
Greatly appreciated!:P

---

