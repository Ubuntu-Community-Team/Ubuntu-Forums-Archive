---
title: "Incorrect Sudo"
date: 2006-05-27
forum: General Help
---

### Post by Dark Elitist on 2006-05-27
I was helping a friend get Shattered Galaxy working on Wine.

When installing it, I accidently told him to type

```
sudo wine installer.exe
```

and as a result there are permission problems.

We are trying to delete the folder via terminal by typing

```
sudo rm -r /home/fox/.wine/drive_c/Program Files/KRU/
```

but we are being told no such directory exists when it clearly does. We are both Linux newbies.

I came up with a theory that maybe the terminal is like Dos in the way that it doesn't understand Program Files but progra~1 or something similar. Please help delete the above folder!

Thank you so much!

---

### Post by jazzmuzik on 2006-05-28
The problem is the space character between "Program" and "Files". Try this instead:

sudo rm -r "/home/fox/.wine/drive_c/Program Files/KRU/"

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=jazzmuzik]The problem is the space character between "Program" and "Files". Try this instead:

sudo rm -r "/home/fox/.wine/drive_c/Program Files/KRU/"[/QUOTE]

Thank you, I'll have him try that.

Do you happen to also know of a guide to help get Shattered Galaxy working with the latest Wine on Breezy with a NVIDIA card that is fully setup and working with Doom 3, etc.?

---

### Post by jazzmuzik on 2006-05-28
I'm not familiar with gaming via wine. I've only used wine for really simple things.

---

### Post by Dark Elitist on 2006-05-28
[QUOTE=jazzmuzik]I'm not familiar with gaming via wine. I've only used wine for really simple things.[/QUOTE]

Thank you anyway. Your help has been most appreciated.

Ubuntu is very amazing and I heard Dapper will be even better than Breezy. Native Linux games, like Doom 3, perform amazingly well compared to their Windows counterparts. Getting non-native games working, however, is another story but that's not at all unexpected.

This community is also awesome! Thanks everyone!

---

