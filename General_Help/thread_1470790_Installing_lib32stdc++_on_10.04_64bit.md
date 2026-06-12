---
title: "Installing lib32stdc++ on 10.04 64bit"
date: 2010-05-03
forum: General Help
---

### Post by AndrejaKo on 2010-05-03
Hi! 

I have a problem similar to the one the poster in [http://ubuntuforums.org/showthread.php?t=1468820](http://ubuntuforums.org/showthread.php?t=1468820) had. I can't install Skype and some some other programs. The error message says something like this:
lib32stdc++6:
 Depends: gcc-4.4-base (=4.4.2-3ubuntu1) but 4.4.3-4ubuntu5 will be installed
 Depends: lib32gcc1 and will not be installed

Can anyone help me solve this dependency issue? I just installed 10.04 and almost all settings are at their defaults.

---

### Post by ibuclaw on 2010-05-03
Looks like you just need to update your sources.

```
sudo apt-get update
```
Then try again.

---

### Post by AndrejaKo on 2010-05-03
Actually that was the first thing I've done. I just tried it again, just to be safe, and it didn't help. I'm using mirrors at [http://rs.archive.ubuntu.com](http://rs.archive.ubuntu.com), which are default for my location. Could it be that they aren't updated?

---

### Post by ibuclaw on 2010-05-03
Very likely.

Have a look here at list of archives: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

If you find yours is behind, either switching mirrors, or downloading the library manually here should resolve it.
[http://packages.ubuntu.com/lucid/amd64/lib32stdc++6/download](http://packages.ubuntu.com/lucid/amd64/lib32stdc++6/download)

Regards
Iain

---

### Post by AndrejaKo on 2010-05-03
Thank you! 
That solved the problem. I moved to a mirror in Hungary and everything is working fine now. 

The strange thing is that both mirrors in my country are marked as up to date, although they obviously are not.

By  the way, can anyone tell me how to change the title of this topic from [ubuntu] to [SOLVED]?

---

### Post by ibuclaw on 2010-05-03
You'll find that option under "Thread Tools" as "Mark this thread as Solved". But I can do that for you so long as you have nothing more to add. :)

Regards

---

