---
title: "Can't remove this icon"
date: 2011-01-21
forum: General Help
---

### Post by audiomick on 2011-01-21
Hallo.
The computer is a laptop belonging to a friend of mine. I fresh-installed Ubuntu 10.04 on it a few weeks back, retaining the exsisting /home partition. There is an icon on the desktop that has been there for a while, since before the fresh install and since my friend's daughter plugged a Samsung phone into the computer.

The screenshot show the "properties" of the icon.

"Ort" is location. As can be seen, the location is something quite odd:
x-nautilus-desktop:///

"Typ" is, as it looks like, "Type", i.e. "application/octet stream"

This is reflected in the error message when I try to open, move or erase it. The message says, in effect "can't deal with that location"

Does anyone have any idea what this is, and how it can be made to go away?

Thanks in advance.

---

### Post by corncob on 2011-01-21
Does it show up in your /Home/Desktop/ directory?  Try typing 
```
rm -f
``` 
plus a space into the terminal and drag the icon there.

---

### Post by audiomick on 2011-01-21
That's a cute idea.
I don't have constant access to the computer, it belongs to a friend, but I will try that next time I get  chance.

To anyone else who reads this, all suggestions are welcome. ;)

---

