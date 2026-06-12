---
title: "Able to see a file from within terminal but not in terminal?!"
date: 2010-08-20
forum: General Help
---

### Post by cAlpha on 2010-08-20
Downloaded and tried to open a movie file from within the file browser window, but despite knowing I'd Dled it (and seeing it within my bittorrent client) it wasn't showing.  Right click-properties showed nine files present, despite only four showing (multiple files weren't showing) and showing 'hidden files' didn't fix the issue either.

Eventually navigated to file location and started the file via 'totem [file name]', but how could this have happened?

I should mention, the file is located on an external HD, which has worked flawlessly up to this point.  I tried shutting down and restarting to correct the issue to no avail.  Any other ideas?

---

### Post by mattymatt22 on 2010-08-20
Can you explain it a little better?  "but despite knowing I'd Dled it"  What do you mean by that?

---

### Post by darolu on 2010-08-20
Open a terminal and run:
```
$ cd /path/to/your/directory
:your/directory$ ls -la

```
Post your results.

---

### Post by cAlpha on 2010-08-20
> **mattymatt22 said:**
> Can you explain it a little better?  "but despite knowing I'd Dled it"  What do you mean by that?

I downloaded the torrent file, loaded it into my client and specified a location.  I subsequently checked the location specified within the file browser and it wasn't there, though it showed as having fully downloaded within my BT client.  

> **darolu said:**
> Open a terminal and run:
```
$ cd /path/to/your/directory
:your/directory$ ls -la

```
Post your results.

THAT command shows the 'missing' files that file browser doesn't display.  The basic problem is why they show there (in the terminal) when not in the file browser?

---

### Post by dcstar on 2010-08-20
> **calpha said:**
> 
........
That command shows the 'missing' files that file browser doesn't display.  The basic problem is why they show there (in the terminal) when not in the file browser?

As you were **specifically** asked to do, post the results.

---

### Post by Vaphell on 2010-08-20
nautilus sometimes does that, i've seen such behavior in 9.10

[http://ubuntuforums.org/showthread.php?t=1318218](http://ubuntuforums.org/showthread.php?t=1318218)

---

