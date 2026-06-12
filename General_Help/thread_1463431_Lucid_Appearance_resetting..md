---
title: "Lucid Appearance resetting."
date: 2010-04-26
forum: General Help
---

### Post by Zintha on 2010-04-26
Everytime I boot into Lucid I have to go into System>Preferences>Appearance>Visual Effects and click Extra, as it resets itself to "None" each time.
When I do click extra it says 
> Searching for available driversthen it all goes through and I confirm changes.

How can I make it so its -always- on Extra (like in Karmic it stuck, didn't have to redo it each bootup).

I wouldn't have an issue but I duel boot with Windows for a handful of games, still at the amateur point that I don't want to abandon windows yet.

---

### Post by Zintha on 2010-05-12
Just to add, I still have this problem but its no longer a problem for me. I'm using none as a default now because of desktop sharing.

If a fix is here though that would be good.

---

### Post by bville09 on 2010-05-12
Yeah, it's a video driver error. If you use integrated graphics (like if you plug your monitor into a blue plug next to your usb ports), then there's no way you can enable desktop effects (installing the proper intel drivers - which no longer exsist in the packages - doesn't do anything to help this).

If you use an actual nvidia or ati (or even an old 3dfx) card, you can enable desktop effects, after you install the proper hardware drivers for your card.

---

### Post by maedox on 2010-05-12
If you are able to use Desktop Effects, and they just don't stick on reboot/logout-login, then add an entry to 'System > Preferences > Startup applications' and add this as command:
```
compiz --replace
```

---

