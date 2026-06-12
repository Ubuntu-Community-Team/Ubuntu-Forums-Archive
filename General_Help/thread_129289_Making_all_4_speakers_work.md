---
title: "Making all 4 speakers work"
date: 2006-02-13
forum: General Help
---

### Post by Mishal on 2006-02-13
I have a built-in sound card with the MSI KT3V motherboard:
Card: Realtek AC'97
Audio Controller: VIA 3059

I have 2 small creative speakers and 2 speakers of my Sony Hi-Fi connected. Only two are detected by the Linux driver. What do I do?

Thanks in advance:)

---

### Post by Mishal on 2006-02-13
Bump :)

---

### Post by zodder on 2006-02-14
Try going into AlsaMixer and enabling "3D Control" by toggling the switch (press "m" to toggle) and turning them all the way up. After that, enable all the "Surround" options and turn those up. I found that by turning on and up the "Front", "Surround", and "Center" switches, I was able to get 5.1 sound. Hope this helps.

---

### Post by Mishal on 2006-02-15
Didn't work. Any other ideas. Thanks :)

---

### Post by Mishal on 2006-02-15
Didn't work. Any other ideas? Thanks :)

---

### Post by Mishal on 2006-02-15
Apparently both MPlayer and XMMS were using the wrong output plugins. But even now that I have changed the pkugin to ALSA, Mplayer can play through all 4 speakers (though not very loudly :( ) and in XMMS, the rear speaker volume is almost inaudible.

HELP!

---

### Post by Mishal on 2006-02-15
Bump! :)

---

### Post by Garyu on 2006-02-15
I had to check the "Duplicate front" option to get 5.1 to work properly. This is something that obviously is difficult to get right for the ALSA guys, because I have seen a lot of sound issues being discussed on the forums.

Just try checking everything you can find in alsamixergui and rasing/lowering volumes and see if you notice a difference anywhere with different combos. Good luck. :)

---

### Post by Mishal on 2006-02-15
> Just try checking everything you can find in alsamixergui and rasing/lowering volumes and see if you notice a difference anywhere with different combos.
I tried this long before but no luck :(
Don't know what I will do now :( Mooommmyyy....I don't wanna play :(

---

