---
title: "pacmd command errors."
date: 2009-11-03
forum: General Help
---

### Post by undecim on 2009-11-03
Hey, all.

I'm looking for a way to change Pulse Audio's output volume (i.e. increase or decrease by X percent, decibels, etc.) in a script (more specifically, with the .fluxbox/keys file)

I've looked at pacmd, but I keep getting errors.```
undecim@caffeine:~$ pacmd set-sink-volume 0 65535
Welcome to PulseAudio! Use "help" for usage information.
>>> Failed to parse volume.
>>> undecim@caffeine:~$ 
```If I could get that command to work, I could write a script to increment the volume by the desired amount, but I've tried all I can think of, and google yields nothing useful.

---

### Post by Giblet5 on 2009-11-03
Same here. Apparently, pacmd doesn't parse the command line (correctly).

```
pacmd << !
set-sink-volume 0 65535
!
```

will do what you want.


Better: ```
#!/bin/bash

if [ -z "$1" ] ; then
    echo "Usage: $0 VOL"
    echo "       where VOL is an integer from 0 thru 65535"
    exit 1
fi

exec pacmd << ! > /dev/null 2>&1
set-sink-volume 0 $1
!
```

---

### Post by undecim on 2009-11-03
> **Giblet5 said:**
> Same here. Apparently, pacmd doesn't parse the command line (correctly).

```
pacmd << !
set-sink-volume 0 65535
!
```will do what you want.


Better: ```
#!/bin/bash

if [ -z "$1" ] ; then
    echo "Usage: $0 VOL"
    echo "       where VOL is an integer from 0 thru 65535"
    exit 1
fi

exec pacmd << ! > /dev/null 2>&1
set-sink-volume 0 $1
!
```

Works like a charm! It's a wonder I didn't think to try the command from pacmd's CLI. (which would likely have led me to this solution).

Thanks a million.

---

