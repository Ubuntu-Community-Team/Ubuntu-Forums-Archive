---
title: "Assigning a new keyboard shortcut"
date: 2012-01-28
forum: General Help
---

### Post by TurtleKing on 2012-01-28
Trying to assign the following to a keyboard shortcut:
```
Name: Eject
Command: eject sr0
```

The key is the eject key on my Microsoft Reclusa Gaming Keyboard.

However, there seems to be no response from the optical drive (doesn't open).

When I try the command in the terminal it works.

Edit: Found this interesting:
```
username@computer:~$ eject -t
eject: unable to find or open device for: `cdrom'
username@computer:~$
```

Any clue what might be wrong?

Extra information:
Ubuntu 11.10 64bit
Keyboard: Microsoft Reclusa Gaming Keyboard

---

### Post by Rebelli0us on 2012-01-28
I have a keyboard shortcut

```
eject -T /dev/sr0
```

assigned to Winkey+Backspace and it works fine.

---

### Post by TurtleKing on 2012-01-29
> **Rebelli0us said:**
> I have a keyboard shortcut

```
eject -T /dev/sr0
```

assigned to Winkey+Backspace and it works fine.

Thanks it fixed it for me. :)

---

