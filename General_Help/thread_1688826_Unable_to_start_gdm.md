---
title: "Unable to start gdm"
date: 2011-02-15
forum: General Help
---

### Post by king0 on 2011-02-15
I recently installed meerkat; when I try to start gdm from the terminal window with: ```
start gdm
``` I get the message: > start: Unknown job: gdmAnyone know what I'm doing wrong? Thanks.

---

### Post by mr_luksom on 2011-02-16
You mean from within a gnome session?

If you want to get to gdm from within a gnome session, logout.

If you have booted to the terminal, try startx.

---

### Post by NikoC on 2011-02-16
sudo /etc/init.d/gdm restart

You can also use the options stop or start.

Hope this works,

NikoC

---

### Post by 3rdalbum on 2011-02-16
> **NikoC said:**
> sudo /etc/init.d/gdm restart

You can also use the options stop or start.

Hope this works,

Sorry, it doesn't - not unless you're using an older version of Ubuntu.

Now it is:

```
sudo service gdm start
```

---

### Post by king0 on 2011-02-16
> **3rdalbum said:**
> Sorry, it doesn't - not unless you're using an older version of Ubuntu.

Now it is:

```
sudo service gdm start
```

As clarification, I originally installed 10.10 *server * (on virtualbox) and then installed *ubuntu-desktop* via apt-get. On boot, I'm starting in the terminal window.

I tried: ```
sudo startx
``` but got in turn: >  no such file or directory, aborting I also tried: ```
sudo service gdm start
``` but continue to get: > Since the script you are attempting to invoke has been converted to an upstart job, you may also use the start(8) utility, e.g. start gdm. start: Unknown job: gdm Any other ideas/suggestions? Thanks.

---

### Post by oldos2er on 2011-02-16
Have you tried explicitly installing gdm? ```
sudo apt-get install gdm
```

---

### Post by king0 on 2011-02-17
> **oldos2er said:**
> Have you tried explicitly installing gdm? ```
sudo apt-get install gdm
```

Yes; apt indicates that the software is already installed.

---

