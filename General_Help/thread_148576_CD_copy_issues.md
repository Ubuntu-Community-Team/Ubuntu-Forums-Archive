---
title: "CD copy issues"
date: 2006-03-22
forum: General Help
---

### Post by Vladimir_BG on 2006-03-22
I tried to copy an audio disc by right clicking on it in desktop, and then selecting CD Copy and and the destination to be an Image in the home folder.
First issue I came across was the lack of cdrdao witch I installed via synaptic.
After that the making of the image took over 30 min! It usualy takes me 3-4 minutes to make an image of audion disc on this machine in nero.
And during those 30+ minutes progress indicator wasn't working.
When the image was complete I right clicked on it and I got the mesage

The file '/home/vladimir/image.iso' is not a valid disc image.

Can anyone help me with this?
I'd prefer to fix this problem rather than to install another CD burning program.

---

### Post by gnu2tux on 2006-03-22
use graveman if using gnome, it has inbuilt cd audio creation.

if using kde, k3b is pretty much as good as nero.

Regards,

Ali

---

### Post by Vladimir_BG on 2006-03-22
I know, but what I would reallt like it to make the blasted thing work since I realy like the simplicity of just clicking copy disc.
also when I try to copy data disc it just unmounts the the source and gives me mesage how no media is preasent!

---

### Post by Vladimir_BG on 2006-03-22
ok, I put graveman and when I tried to make an image out of an audio disc I got a window with this mesage:


Cannot create image: /usr/bin/readcd: Success. read_g1: scsi sendcmd: no error
CDB:  28 00 00 00 00 00 00 00 40 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 25 00 00 00 00 0A 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (valid) illegal block length 
resid: 131072
cmd finished after 0.010s timeout 40s

What the hell is wrong with my pc?
Note: Win XP burning works ok.

---

