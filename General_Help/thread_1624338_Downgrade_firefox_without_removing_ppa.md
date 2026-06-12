---
title: "Downgrade firefox without removing ppa"
date: 2010-11-17
forum: General Help
---

### Post by io5cml4z on 2010-11-17
I need to downgrade my firefox 3.6.9 to 3.6.8, because it was upgrade when I added the ubuntu-mozilla-daily ppa, and I have been having some issues with firefox 3.6.9 (firefox-bin runs as uninterruptible, and firefox lags like crazy), so I need to downgrade firefox *without* removing the ubuntu-mozilla-daily ppa. Oh, and also if anyone knows how to get icedtea java plugin working on Chromium, I would be very grateful (It's the only thing that's preventing me from making it my default browser). :)

---

### Post by io5cml4z on 2010-11-17
Bump. Anyone?

---

### Post by TeoBigusGeekus on 2010-11-17
Why don't you try the latest version from the mozilla site?

---

### Post by Frogs Hair on 2010-11-17
Namoroka is currently at 3.6.13 and regular release is 3.6.12 . If you keep the ppa it will continue to up date . You could search to see if there is an archive for the release you want remove the ppa and lock it there.

---

### Post by io5cml4z on 2010-11-17
Thanks guys. I guess I'll just install from the website. Not too much of a difference right (I'll still get updates?)?
Edit: Oh, and you guys wouldn't happen to know anything about the Chromium-icedtea thing right?

---

### Post by Frogs Hair on 2010-11-17
I haven't used Chromium , but you may want open a thread with that title if you get no results here.

---

### Post by io5cml4z on 2010-11-18
I removed the ppa and downgraded, but it's still lagging! I'm using the latest standard firefox browser from the default repositories. firefox-bin is still taking only about 5% cpu, but it lags like crazy and the process is uninterruptible, and I tried starting it with the terminal, it displays no errors at all. Help again?

---

### Post by io5cml4z on 2010-11-18
Bump.

---

### Post by io5cml4z on 2010-11-18
Double bump.

---

### Post by TeoBigusGeekus on 2010-11-19
Export your bookmarks and delete the ~/.mozilla/firefox folder.
If the lag is caused by some bad cache and/or setting, this should fix it.

---

### Post by io5cml4z on 2010-11-19
Thanks! That did the trick. I didn't even have to export my bookmarks, it somehow automatically did that for me. The only thing is I now have to reinstall my extensions, but oh well. And since it's only a plugin/extension/cache problem, I figure I'll just re-add the repository. Thanks again guys!

---

