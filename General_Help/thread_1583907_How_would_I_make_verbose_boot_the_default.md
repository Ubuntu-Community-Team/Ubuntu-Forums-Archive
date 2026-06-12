---
title: "How would I make verbose boot the default?"
date: 2010-09-28
forum: General Help
---

### Post by Dustin2128 on 2010-09-28
My laptop's ubuntu partition has been a bit sluggish to boot lately, and I'd like to swap to a verbose boot so I can see if there are any processes I can eliminate to improve speed. E.g. my slackware install was waiting for an 8 second timeout initially, but I was able to stop it.

---

### Post by CharlesA on 2010-09-28
Run this:

```
gksu gedit /etc/default/grub
```

And remove "quiet splash"

---

### Post by drs305 on 2010-09-28
You can [COLOR="Red"]remove[/COLOR] the "quiet splash" entry in the default settings of Grub2:
```
gksudo gedit /etc/default/grub
```
Remove them from this line:
> GRUB_CMDLINE_LINUX_DEFAULT="[COLOR="Red"]quiet splash[/COLOR]"

**Added in response to OP input:**
To:
> GRUB_CMDLINE_LINUX_DEFAULT=""

Save the file, then update grub:```

sudo update-grub
```

The boot messages will scroll by pretty quickly.

You can also inspect the dmesg log file (and others)  via System, Administration, Log File Viewer to see if anything looks odd there.

---

### Post by CharlesA on 2010-09-28
drs305 did a better write up then me. :D

You can also try installing bootchart.

---

### Post by drs305 on 2010-09-28
CharlesA,

I guess it just took me longer to write mine - didn't see your entry before I hit ENTER.  ;-)

Anyway, I agree that bootchart is an interesting way to view the boot process.

---

### Post by Dustin2128 on 2010-09-28
how would I remove the line, completely delete it, delete quiet splash, or just comment it out?

---

### Post by CharlesA on 2010-09-28
Just remove the quiet splash part. Leave the quotes.

---

### Post by Dustin2128 on 2010-09-28
> **CharlesA said:**
> Just remove the quiet splash part. Leave the quotes.
thanks, I finally have my verbose boot!

---

