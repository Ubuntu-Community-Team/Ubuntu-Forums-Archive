---
title: "No sound, please help"
date: 2010-01-28
forum: General Help
---

### Post by Gabri3l on 2010-01-28
I'm sorry if this was alredy posted, but I recently installed ubuntu 9.10, today actually, and I can't seem to make the audio work. I read a lot of threads, but no luck with this... Please someone help, I'm just starting and don't know much of this things 
Following some help and other posts This is what I did:
This is the original thread btw: [http://ubuntuforums.org/showthread.php?t=1390787](http://ubuntuforums.org/showthread.php?t=1390787)

Codec: Realtek 662 rev1

Found the ALSA documentation:
3stack-dig 3-stack (2-channel) with SPDIF
3stack-6ch 3-stack (6-channel)
3stack-6ch-dig 3-stack (6-channel) with SPDIF
6stack-dig 6-stack with SPDIF
lenovo-101e Lenovo laptop
eeepc-p701 ASUS Eeepc P701
eeepc-ep20 ASUS Eeepc EP20
ecs ECS/Foxconn mobo
m51va ASUS M51VA
g71v ASUS G71V
h13 ASUS H13
g50v ASUS G50V
asus-mode1 ASUS
asus-mode2 ASUS
asus-mode3 ASUS
asus-mode4 ASUS
asus-mode5 ASUS
asus-mode6 ASUS
auto auto-config reading BIOS (default)

Typed this command: sudo nano /etc/modprobe.d/alsa-base.conf
And at the end of the file added "options snd-hda-intel model=3stack-6ch"

I guess I did everything ok, but ir still doesn't play anything, Pleas help me, I don't want to take the pc to a tech guy :/

---

