---
title: "can get to log in but when i log in i get errors"
date: 2010-10-26
forum: General Help
---

### Post by hopeless8009 on 2010-10-26
before the problem happand i did 3 things removed thunderbird, removed Vuze bit torrent and made it where you didn't have to inter a password to log into my account. I rebooted my computer and to log in screen. when I tried to log in i got theses errors

- could not update ICEauthority file /home/john/.ICEauthority
-there is a problem with the configuration server (/usr/lib/libconf2-4/conf-sanity-check 2 exited with status 256)
-Nautilus could not create the following required folders /home/john/desktop, /home/john/.nautilus
before running nautilus, please create these folders, or set premissions such as that nautilus can create them



What is my best cores of action to fix this problem. time is important i was suposed to shop it to dell today

---

### Post by requeth on 2010-10-26
I'm going to take a shot in the dark here and say your no longer the owner of your user profile. I'd recommend going into command line (if you can't get that far then when booting into grub hold down CTRL and choose command line).

type cd /home

type ls -al

look at the directory  named after your username, it should see on the 2nd and 3rd column that it's owned by your user. If they say root then:

type sudo chown username /home/username

You may also what to sudo 700 /home/username

Hopefully this will solve your problem. If not post back, I'm watching.

---

