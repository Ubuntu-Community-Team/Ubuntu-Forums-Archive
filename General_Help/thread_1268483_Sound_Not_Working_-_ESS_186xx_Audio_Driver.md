---
title: "Sound Not Working - ESS 186xx Audio Driver"
date: 2009-09-17
forum: General Help
---

### Post by noobuntu7 on 2009-09-17
I installed Xubuntu 8.04 (only version that would work) on an old [_Compaq Presario 1245 Notebook_]("http://h10025.www1.hp.com/ewfrf/wc/product?product=94995&lc=en&cc=us&dlc=en&lang=en&tmp_track_link=ot_we/prodlink/en_us/94995/loc:0&cc=us"). Almost everything is working, but I can't get the sound to work. 

I've tried following every guide available from [_SoundTroubleshooting_]("https://help.ubuntu.com/community/SoundTroubleshooting") to the [_Comprehensive Sound Problem Solution Guide_]("http://ubuntuforums.org/showthread.php?t=205449"). I tried all the steps in both guides, re-installed alsa... [attempted to] compile the driver. [Here]("http://www.alsa-project.org/main/index.php/Matrix:Module-es18xx") is the ES18xx page on ALSA-Project.org.

Xubuntu isn't recognising my sound card at all (even after everything I did) I get
```
$ aplay -l
device_list: no soundcard found...
```

lspci -v doesn't list any sound card / multimedia controller. I tried sudo modprobe snd-es18xx and that didn't work. Could someone please provide me with a suggestion quickly? Thanks to everyone.

---

### Post by theozzlives on 2009-09-17
I had an old Compaq Deskpro that did that I had to do:
```
gksudo gedit /etc/modules
```
at the last line I put:
```
snd=ess18xx
```
it worked fine after that, don't remember if it was 8.04 or 8.10 I had to do that with, but it ran through Jaunty after I got rid of it, then the stupid lady put XP on it.

---

### Post by noobuntu7 on 2009-09-17
I tried doing that as well. It didn't work, but I noticed that now if I try to run modprobe snd-es18xx it gives me the error:
```
WARNING: /etc/modprobe.d/snd-es18xx line 1: ignoring bad line starting with 'options'
```

Could someone please help me out?

---

### Post by noobuntu7 on 2009-09-17
I finally got a fix myself. I was very worried I had messed up the whole system by guessing and performing all kinds of "sudo" I didn't even understand. I went to this thread: [http://ubuntuforums.org/showthread.php?t=148077&highlight=es1869+no+sound](http://ubuntuforums.org/showthread.php?t=148077&highlight=es1869+no+sound). This is what I did.

I edited the /etc/modules file and deleted the lines already in the file, and added the following lines:
```
lp
mousedev
psmouse
snd-es18xx
```

Then I edited the /etc/modprobe.d/alsa-base file and added the following lines to the beginning of the file:
```

alias char-major-116 snd
alias snd-card-0 snd-es18xx
options snd-es18xx index=0 enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
```

That's it! Super-simple fix, it just took me about 15+ hours to figure it out. Hope that helps someone else. :)

---

