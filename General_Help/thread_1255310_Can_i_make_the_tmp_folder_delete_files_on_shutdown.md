---
title: "Can i make the /tmp folder delete files on shutdown and not on app's closing?"
date: 2009-09-01
forum: General Help
---

### Post by chriskin on 2009-09-01
well. as the title says
Can i make the /tmp folder delete files on shutdown and not on app's closing?
:popcorn:

---

### Post by thinkdez on 2009-09-01
At first I thought you could write an rc script to do this.  While researching I found this: [http://www.howtoforge.com/forums/showthread.php?t=13703]("http://www.howtoforge.com/forums/showthread.php?t=13703") 

Hope it works for you.

---

### Post by chriskin on 2009-09-01
> **thinkdez said:**
> At first I thought you could write an rc script to do this.  While researching I found this: [http://www.howtoforge.com/forums/showthread.php?t=13703]("http://www.howtoforge.com/forums/showthread.php?t=13703") 

Hope it works for you.

thank you, i will check it tonight :)

---

### Post by geirha on 2009-09-01
/tmp is wiped during boot, so I don't quite see the point in also wiping it on shutdown ...

---

### Post by chriskin on 2009-09-01
> **geirha said:**
> /tmp is wiped during boot, so I don't quite see the point in also wiping it on shutdown ...

some parts of /tmp are deleted when the application stops
browsers for example.

---

### Post by geirha on 2009-09-01
> **chriskin said:**
> some parts of /tmp are deleted when the application stops
browsers for example.

Yes, well written programs clean up their temporary files on exit. Do you want to avoid programs cleaning up their temporary files for some reason?

---

### Post by chriskin on 2009-09-01
> **geirha said:**
> Yes, well written programs clean up their temporary files on exit. Do you want to avoid programs cleaning up their temporary files for some reason?

yep :)

---

### Post by geirha on 2009-09-01
> **chriskin said:**
> yep :)

There's no good way to do that. Since you mention browsers, I assume you want to keep files you download (by click open instead of save). If that is the case, there's probably some browser add-on you can install to achieve that. Maybe use an external downloader.

---

### Post by Lampi on 2009-09-01
check out /etc/default/rcS and its manpage (man rcS)

$TMPTIME sets the amount of days to pass for your /tmp to get cleaned - set it to integer 1 and it will clean your /tmp after one day

---

### Post by chriskin on 2009-09-01
> **Lampi said:**
> check out /etc/default/rcS and its manpage (man rcS)

$TMPTIME sets the amount of days to pass for your /tmp to get cleaned - set it to integer 1 and it will clean your /tmp after one day

seems very nice, thank you :)

---

### Post by sedawk on 2009-09-01
What you can try to do is to "backup" /tmp very often using
something like 
```

mkdir ~/tmp_backup
while sleep 5; do
   sudo rsync -r --size-only /tmp/ ~/tmp_backup/
done

```

---

