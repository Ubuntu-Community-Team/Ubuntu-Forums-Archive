---
title: "Two CD installation in WINE."
date: 2009-10-17
forum: General Help
---

### Post by Penguinlord on 2009-10-17
Hello, I have a game - Stronghold 2. It comes in two discs, both of which are needed for installation. I am attempting to run it through wine, however once I get towards the end of the installation it asks for me to insert the second disk. How do I force ubuntu to eject the first one so I may insert the second?

---

### Post by Bachstelze on 2009-10-17
Unmount the CD if it's mounted, and

```
sudo eject /dev/cdrom
```

---

### Post by falconindy on 2009-10-17
eject can also be used as a regular user without arguments. If you've only got one cd drive, there's not much else to eject.

And in case you're curious, you can use `eject -t` to close the drive.

---

### Post by mc4man on 2009-10-17
2 ways
in terminal
```
wine eject
```

Or if that doesn't work ( wine doesn't locate the 2nd+ disk and assumming the drive is D in winecfg ( could be E

Starting the  install like this it works more like in windows, the drive won't be locked, when prompted just push the eject button on your drive and insert next disk. (plus this maintains proper path for 2nd disk

Replace the blue if needed, browse the cd for  installer file name

```
wine D:\[COLOR="Blue"]setup.exe[/COLOR]
```

---

