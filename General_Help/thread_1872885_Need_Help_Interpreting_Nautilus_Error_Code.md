---
title: "Need Help Interpreting Nautilus Error Code"
date: 2011-10-31
forum: General Help
---

### Post by w201 on 2011-10-31
Trying to interpret this nautilus error code if anyone can help me out. Anything with the word critical makes me worry. Thanks in advance.

```

(nautilus:2191): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2191'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


```

---

### Post by hailtothethief on 2011-10-31
Really need some more information:

1. What were you doing to trigger the messages?
2. What did you expect to happen?
3. What actually happened?

---

### Post by hailtothethief on 2011-10-31
After thinking about it a bit more, my guesses follow:

```
(nautilus:2191): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
```
This is an innocuous error about a failed gconf assertion. [http://ubuntuforums.org/showthread.php?t=1592348](http://ubuntuforums.org/showthread.php?t=1592348) may have a way to squelch it for you


```
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2191'

```
My guess is that you were trying to run nautilus as root? Again, no noticeable ramifications when I reproduce this message on my own machine.

```
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```
Nautilus is looking for samba shares, but samba isn't installed (probably)
Run ```
sudo apt-get install samba
``` if you really want to shut it up.

Good luck!

---

### Post by w201 on 2011-10-31
> **hailtothethief said:**
> Really need some more information:

1. What were you doing to trigger the messages?
2. What did you expect to happen?
3. What actually happened?

Hey sorry for the delay in replying back. What I was actually doing is restructuring my filing system and remembered something I read about nautilus just a few days earlier, decided to give it a try, ran it and got the error code. Nautilus ran anyway, but the error code piqued my curiosity.

BTW- thanks a bunch for that solution!

---

