---
title: "Nokia N8 music transfer mtp?"
date: 2011-01-07
forum: General Help
---

### Post by gurpal2000 on 2011-01-07
Hi has anyone got the Nokia N8 device working with Rhythmbox or anything else? or maybe some mtpfs thing ?

My N900 seems to work fine, although the N8 is a newer device...

i'm using Meerkat 64-bit

Thanks

---

### Post by 12001 on 2011-01-20
I don't have a solution, but can confirm the MTP feature with the N8 and Rhythmbox isn't working. If connecting the device something shows up in Rhythmbox. Rightclick on it and select 'Properties' will kill Rhythmbox.

Connecting the phone in Mass Storage mode works just fine.

---

### Post by gurpal2000 on 2011-01-20
Agreed - the mass storage works. BUT miraculously Rhythmbox DOES work for me couple days after the OP. It doesn't recognise the device (gives it some other name). I had to create a file ".is_audio_player" in the root of the drive. Contents something like

output_formats=video/x-msvideo, audio/mpeg, audio/mp4, video/mp4 
audio_folders=Sounds/ 
folder_depth=2 
coverartfilename=cover.jpg 
coverartfiletype=jpeg 
coverartsize=200

And things are looking better. Will reveal more later. It's a bit late here!

---

