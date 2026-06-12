---
title: "ddrescue: unwanted multiple read attempts of bad sectors"
date: 2010-01-26
forum: General Help
---

### Post by scotty64 on 2010-01-26
I am trying to create an image of a damaged harddisk by using ddrescue. I notice that although the ddrescue docs say the program only makes one attempt to read a sector, the harddisk gets stuck for a long long time when the recovery meets a bad sector and the repeating harddisk sounds let me guess that it tries at least 14 times before moving on to the next block.
I tried the --direct option of ddrescue to bypass caching, but that did not help at all.
Is there any way to tell whoever is responsible for these repeated read attempts to do one and only one attempt ?
These read attempts do not only slow down the whole copy process terribly, they put dangerous additional stress on the already damaged disk mechanics.

---

### Post by ibuclaw on 2010-01-26
```

-n, --no-split
              do not try to split or retry failed blocks

```
Could be the answer you are looking for.

source: [http://manpages.ubuntu.com/manpages/karmic/en/man1/ddrescue.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/ddrescue.1.html)

Regards
Iain

---

### Post by scotty64 on 2010-01-26
> **tinivole said:**
> ```

-n, --no-split
              do not try to split or retry failed blocks

```
Could be the answer you are looking for.

source: [http://manpages.ubuntu.com/manpages/karmic/en/man1/ddrescue.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/ddrescue.1.html)

Regards
Iain

Yes, I am running ddrescue with the -n / --no-split option and it still does multiple read attempts. I wonder if the problem is actually ddrescue or if another part of the chain ddrescue -- harddisk hardware causes this.
dmesg comes up with this:
[29092.123451] sd 8:0:0:0: [sdc] Unhandled sense code
[29092.123458] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[29092.123466] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current]
[29092.123475] sd 8:0:0:0: [sdc] Add. Sense: No additional sense information
[29092.123485] end_request: I/O error, dev sdc, sector 37803664
[29092.123494] Buffer I/O error on device sdc, logical block 4725458
[29115.527036] sd 8:0:0:0: [sdc] Unhandled sense code
[29115.527044] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[29115.527052] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current]
[29115.527061] sd 8:0:0:0: [sdc] Add. Sense: No additional sense information
[29115.527071] end_request: I/O error, dev sdc, sector 37803664
[29115.527080] Buffer I/O error on device sdc, logical block 4725458

It looks like two attempts here, but I can here more. Maybe both Kernel and HD-Firmware both add their bit ?

---

