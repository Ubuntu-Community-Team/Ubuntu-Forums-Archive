---
title: "How to get XMMS to play 2channels mp3s on all speakers for 5.1 setup"
date: 2006-04-29
forum: General Help
---

### Post by Eroo on 2006-04-29
I have only been using Ubuntu for about 3 months now so I dont know too much about Linux. My problem was that while I could listen to a 5.1 DVD in totem with all speakers working in XMMS it only played on two rear speakers. I tried some other stuff on the forums with the asoundrc but it didn't work with my card.. it came out distorted. I finally found this on the alsa home page and I am posting it if it will help anybody else. Create a test file named .asoundrc in your home directory and paste this code in it

[COLOR="Red"]pcm.ch40dup {
    type route
    slave.pcm surround40
    slave.channels 4
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
}

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}[/COLOR]

Save the file and open XMMS and goto Options>Preferences>Output plugin
Choose Alsa plugin and configure. In device type either ch40dup or ch51dup depending whether u have a 4 channel or 6 chanel setup.See attachment for help on this


Note: this is not true surround music but rather making xmms play the mp3 on all speakers

---

### Post by n3tfury on 2006-04-29
IMO that's blasphemy, but that's pretty neat that you figured it out. Nice work.

---

### Post by hamil on 2006-05-07
Neat..
Thank you!

---

### Post by nmsa on 2006-05-14
works for me as well
I configured as device type ch40dup
my sound card is a NVidia CK804 - IEC958 ALSA Playback Device on board a ASUS SLI Deluxe.
Thank you

---

### Post by roderikk on 2006-05-28
[QUOTE=nmsa]works for me as well
I configured as device type ch40dup
my sound card is a NVidia CK804 - IEC958 ALSA Playback Device on board a ASUS SLI Deluxe.
Thank you[/QUOTE]

Hm, I've got the same soundcard (different mobo manufacturer, Gigabyte) but when I try this it plays over all 5 boxes but it 'crackles' a lot? Anyone else has this problem?

---

### Post by XomboX on 2006-06-05
Great! It also works with Mplayer! You have done a good job, Eroo!

---

### Post by He4oBek on 2006-06-09
I also get the crackling and the subwoofer doesn't work.

---

### Post by pemo on 2006-06-11
Where should this file be stored?
I'v stored it in /home/*user*, and nothing...

Thanks.

---

### Post by roderikk on 2006-06-11
[QUOTE=pemo]Where should this file be stored?
I'v stored it in /home/*user*, and nothing...

Thanks.[/QUOTE]

It is a while ago, but I believe I just put it in my homefolder as well. Did you restart XMMS/Gnome?

Good luck.

---

### Post by dp_wiz on 2006-07-15
> **roderikk said:**
> Hm, I've got the same soundcard (different mobo manufacturer, Gigabyte) but when I try this it plays over all 5 boxes but it 'crackles' a lot? Anyone else has this problem?

I'v got cracking on nVidia's internal.

---

