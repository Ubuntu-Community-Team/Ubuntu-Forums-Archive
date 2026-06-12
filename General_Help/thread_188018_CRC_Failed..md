---
title: "CRC Failed."
date: 2006-06-03
forum: General Help
---

### Post by Aurae on 2006-06-03
Ok so I downloaded a torrent iso thats split into 48 part.rar files. Now whenever i try to unrar it using Ark, or the Archive Manager it goes fine, it creates the iso where i want it to however after it gets to the last file, it outputs one error and deletes the file.

Error: CRC Failed

Thats all i get, theres nothing before or after that to indicate why it failed, it just fails. Now ive downloaded several torrents with isos split in this manner and it wont let me do it on any of them. However whenever i unrar a normal file it works perfectly fine. 

Programs ive tried: rar from rarlabs, Ark, Xarchiver, and the Built in Archive Manager.
OS: Ubuntu 6.06 Desktop version.
All Repositires are enabled on Synaptic.

I searched the forum but couldnt find a solution to this problem. Any help would be greatly Appreciated. Thanks ;)

---

### Post by taurus on 2006-06-03
I find running or unraring them from a terminal always works best...
```

unrar -x <first_file>
(and it will unrar and join the rest...)

```

---

### Post by Video Toaster on 2006-06-03
"(Cyclical Redundancy Checking) An error checking technique used to ensure the accuracy of transmitting digital data. The transmitted messages are divided into predetermined lengths which, used as dividends, are divided by a fixed divisor. the remainder of the calculation is appended onto and sent with the message. At the receiving end, the computer recalculates the remainder. If it does not match the transmitted remainder, an error is detected."

[right]--[http://www.wetstonetech.com/page/page/1972572.htm](http://www.wetstonetech.com/page/page/1972572.htm)[/right]

I think one of your RAR files might be corrupt.

---

### Post by Aurae on 2006-06-03
It still is giving me the CRC Failed error Taurus

OK Video, That would certaintly pose a problem, yet i have download several torrents that are rar'ed in this fashion, now they all couldnt have a corrupt rar file, surely one of them would work.  but none of them do, always gives me the same error...

---

### Post by PriceChild on 2006-06-03
maybe they've been rar'd in some manner uncompatible with the linux rar?

I know for example that those given a password on windows can't be unlocked on a linux system.

---

### Post by thasheep on 2006-06-03
Which unrar are you using? The one unrar (not unrar-free) in the repos has worked fine for me.

---

### Post by Aurae on 2006-06-03
Im using the "unrar" not the "unrar-free" version.

---

### Post by bjc on 2006-06-03
I second trying it from the terminal. I've also seen CRC errors when the partition I'm extracting to is full, or part of the archive is passworded.

---

### Post by Aurae on 2006-06-03
I tried from the terminal and still says the same thing, also i have 20gigs on the place im extracting to and none of the files are passworded from the info i got from other people i talked to. Its got me stumped, maybe i dont have a file needed?

---

