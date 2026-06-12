---
title: "Do NOT mount OS without password"
date: 2012-02-09
forum: General Help
---

### Post by Dailey on 2012-02-09
Wanted to give Ubuntu another go so I downloaded and installed 11.10.  Enjoying the playing with the interface & getting to know the system, but I do not like that it auto-mounts my Win. 7 partition without a password.
I have tried to change permissions on the 'OS' (Win 7) partition, but obviously that hasn't been met with much success.  So my question:  Is there a way to require a password before mounting 'OS'?  I want it to auto-mount (and not require a password) my USB/DVD/CD's, but NOT my other partition.  Any ideas?
I appreciate your help & continue to appreciate the community that is Ubuntu.

---

### Post by WorMzy on 2012-02-09
Not sure whether or not this will still work, but give this a go:

[http://ubuntuforums.org/showpost.php?p=9207234&postcount=4]("http://ubuntuforums.org/showpost.php?p=9207234&postcount=4")

---

### Post by Dailey on 2012-02-09
> **WorMzy said:**
> Not sure whether or not this will still work, but give this a go:

[http://ubuntuforums.org/showpost.php?p=9207234&postcount=4]("http://ubuntuforums.org/showpost.php?p=9207234&postcount=4")

Thanks for the thought, but that method requires a password for USB mounting as well.
I'd be willing to hide the partition, but again I've been unsuccessful at that as well.

---

### Post by brpylko on 2012-02-09
Why do you need it to not be mounted? You could create a script (for this example called umountwin) that will do this on startup.

```

#!/bin/bash
#For this example the windows partition is /dev/sda2, you may need to change this.
umount /dev/sda2

```now run in the terminal

```

sudo chown root umountwin
sudo chmod u+x umountwin
sudo chmod a+s umountwin

```add umountwin to startup applications and you should be good to go.

---

### Post by Dailey on 2012-02-09
> **brpylko said:**
> Why do you need it to not be mounted? You could create a script (for this example called umountwin) that will do this on startup.


Here is my problem.  I would like to set-up a *nix based OS on a computer for a computer illiterate user to use so I don't have to play the "Scrub windows game" every 3 months.  Ubuntu seemed reasonable as Unity is fairly intuitive & Ubuntu works out of the box.
My concern is, without some sort of precautionary measure, someone could wipe out (or delete a necessary file) the Win7 partition.  Thus, the catalyst for my question.

The two options I see:  
 - Hide access to mount the Win7 partition. (Don't make it point & click.)
 - Require a password (which they will not have) to mount the Win7 partition.

Is there another option that I'm missing?

---

