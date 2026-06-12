---
title: "Does my thin client not have enough memory / horsepower for rsync?"
date: 2009-11-19
forum: General Help
---

### Post by spaceballl on 2009-11-19
Hi there,
I'm running a thin client with a very basic ubuntu install (no GUI, i just SSH into it). The goal is to have my music rsync to a 64GB usb flash drive plugged into the thin client w/ 800mhz CPU and 128MB of RAM. That computer is my squeezebox server. However, when I try to rsync, I get the following error:

```

Music/2Pac/Better Dayz [Disc 1]/1-13 Thugz Mansion [Acoustic].mp3
Music/2Pac/Greatest Hits (1)/
rsync: mkstemp "/media/usb-disk/iTunes Music/Music/2Pac/Greatest Hits (1)/..DS_Store.LxtOIC" failed: No such file or directory (2)

```

I think it's interesting to note, for whatever reason, that I get this error after a directory change. I've been banging my head against the wall, searching for some logical answer to this problem, and I haven't been able to find one. So as a sanity check, I figured I would try it on my laptop, which is running Karmic.

The laptop works like a charm! So it's obviously nothing wrong w/ the source or my syntax... I also thought it might be a bum USB flash drive, but it's working fine in the laptop. So yeah I'm just puzzled. The only thing I can think of is that my thin client is running out of memory, but... that doesn't seem to make sense to me.

Anyhow, I'd appreciate it if someone has some advice. I am rsync'ing the music over to the flash drive now via the laptop, and that's nice because at least i'll have the music, can plug it into the thin client, and then be off. But it's not an elegant solution. Help is much appreciated!

---

### Post by spaceballl on 2009-11-19
Well not that this solves much, but FYI now i'm doing the transfer of music, using the same basic syntax, on my macbook pro locally from my music DIR to the flash drive.

So the good news is that the problem isn't the actual flash drive hardware - I was concerned about that. The bad news is that there must be something wrong w/ the environment / configuration on my thin client. Would love some help, if anyone has insight. Thanks!

---

