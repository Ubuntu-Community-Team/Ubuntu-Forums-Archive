---
title: "No sound out of headphones, just speakers"
date: 2009-08-13
forum: General Help
---

### Post by Lil Jimmy on 2009-08-13
Hello, I have a problem where the sound only comes out of my speakers and never out of my headset. In gnome-volume-control, I have my headset selected. In alsamixer, it also has my headset selected. I don't know how to fix this. It's a USB headset.

```
james@home:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

 Any suggestions? Thanks!

---

### Post by Ranax on 2009-08-13
Which version of Ubuntu are you using? I had this issue when I tried Karmic.

---

### Post by soratheultima on 2009-08-13
im using mint 7 and its giving me this problem too *have the same headphones* and im thinking of going back to ubuntu :3

---

### Post by Ranax on 2009-08-13
> **soratheultima said:**
> im using mint 7 and its giving me this problem too *have the same headphones* and im thinking of going back to ubuntu :3

Ubuntu and Mint are the same thing underneath. Mint 7 is based on Ubuntu 9.04, so if you have this problem on Mint, it is virtually guaranteed to happen on Ubuntu!

---

### Post by Lil Jimmy on 2009-08-13
I'm actually using CrunchBang, but it's built on ubuntu, so I figured I could ask here :P

---

### Post by feffer on 2009-08-13
I'm sure you've tried unplugging your speakers to see if the headphones will now work. Right? I had this issue on an old Dell box, and didn't realize it at first.

---

### Post by Lil Jimmy on 2009-08-13
> **feffer said:**
> I'm sure you've tried unplugging your speakers to see if the headphones will now work. Right? I had this issue on an old Dell box, and didn't realize it at first.

Yes I have tried. It's not that.

---

### Post by Lil Jimmy on 2009-08-14
Bump? ;-;

---

### Post by Codix121 on 2009-08-14
> 
I am using ubuntu(9.04). I had the same problem before, headphone jack was not working. Then I found this solution from one of the forum sites:

Headphone not working in Toshiba

Add this line to the end of "/etc/modprobe.d/alsa-base"

Code:
```
options snd-hda-intel model=lenovo
```

Then run this command:

Code:
```
sudo alsa force-reload
```

Now you can even mute the laptop speakers from alsa mixer while listening from headphone if you want.

I hope it works for you too...


Some guy posted this and It fixed my headphones!
I went through all these stupid long tutorials and code alterations,
downloads none fixed my headphones, but adding this simple line made
my headphones work...

this worked for me,
i'm running a toshiba satellite.

---

### Post by Codix121 on 2009-08-14
by the way to bring up your /etc/modprobe.d/alsa-base.conf,
the command in terminal is:

```

gksu gedit /etc/modprobe.d/alsa-base.conf 
```

---

### Post by Lil Jimmy on 2009-08-14
Nope, it didnt work :( Any other suggestions?

---

### Post by Lil Jimmy on 2009-08-14
Bumpabump

---

