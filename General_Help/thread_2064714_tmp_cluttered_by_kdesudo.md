---
title: "/tmp cluttered by kdesudo?"
date: 2012-09-30
forum: General Help
---

### Post by Stonecold1995 on 2012-09-30
I've been using kdesudo a lot today, and I've noticed its cluttering /tmp quite a lot.  Is kdesudo suppose to be leaving all these files behind, and would it be safe to remove them ("*sudo rm /tmp/kdesudo*xauth*")?

[[IMG]http://www.pictureshack.us/thumbs/82924_screenshot.png[/IMG]](http://www.pictureshack.us/images/82924_screenshot.png)

---

### Post by 2F4U on 2012-09-30
The /tmp folder should be cleaned automatically by the system upon a reboot. Isn't that the case on your system? Unless you are running kdesudo at the moment of removal, it should be safe to delete those files.

---

### Post by Stonecold1995 on 2012-09-30
It is cleaned up at reboot.  I have /tmp mounted as tmpfs so even if it weren't the case it'd still clear when the power is cut.  It's just that I don't often reboot because I'm running KTorrent and Folding@home 24/7.  The problem is that I often use /tmp myself, either for compiling software (tmpfs allows for * ridiculous* fast compile times) or for doing anything that requires a lot of copying large files.  It gets frustrating when so many files start accumulating.

Would it be safe to use a startup script like this?  Or maybe set up a cron job instead?
```
#!/bin/bash

if [ $(id -u) -ne 0 ]; then
    echo "Error, this script must be run as root."
    exit 1
fi
while [ $(pgrep -c kdesudo) -eq 0 ]; do
    rm /tmp/kdesudo-*-xauth
    sleep 60
done
```

Also, just out of curiosity what is contained *within* these files?  I found the string "MIT-MAGIC-COOKIE" in it but I have no idea what that is.  The .Xauthority file also contains the line "MIT-MAGIC-COOKIE", so I'm guessing the two are somehow related.

---

