---
title: "trouble running XP in Virtual Box (kernel issue?)"
date: 2010-10-01
forum: General Help
---

### Post by lue42x on 2010-10-01
I'm getting an error message (well .. two) when trying to run XP in Virtual Box.  Has anyone encountered this before?

I"m kind of a newb ... not really sure what to make of this ... any help would be much appreciated

screencap of issue: 

[http://img408.imageshack.us/img408/7418/screenshotui.png](http://img408.imageshack.us/img408/7418/screenshotui.png)

---

### Post by sikander3786 on 2010-10-01
Either reinstall virtual box or if you want to preserve your guest install, every time the kernel is updated, do this.

```
sudo apt-get install linux-headers-$(uname -r)
```

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Warthaug on 2010-10-01
I run into this problem on occasion.  It is caused during the boot of your computer, usually by a delay in your computer recieving an IP address from your network.  Basically, some processes will not start if the computer is waiting for an IP.  CUPS also often fails as a result of this.

What you need to do is manually start the virtualbox service.  This can be done by opening a terminal and running the command:
```
sudo /etc/init.d/vboxdrv start
```

Some more info, from other threads:
[http://ubuntuforums.org/showthread.php?t=1545686](http://ubuntuforums.org/showthread.php?t=1545686)

Bryan

EDIT: after running the above command your virtual machines should start normally.  No need to reboot, etc.  If this problem persists, you can throw the above code into a script and automatically execute it every startup.

---

### Post by snowpine on 2010-10-01
Welcome to Linux, where error messages are actually informative! :)

```
sudo apt-get update
sudo apt-get install dkms
sudo /etc/init.d/vboxdrv setup
```

---

### Post by lue42x on 2010-10-03
guys thanks so much for your help!  I got it working by uninstalling and reinstalling Virtual Box.  I will keep this topic bookmarked in case it happens again, to try the other solutions posted (if it does happen)

---

### Post by Ocxic on 2010-10-03
It will happen again the next time you kernel is updated. if it does just run "sudo /etc/init.d/vboxdrv setup" from a terminal.

---

### Post by lue42x on 2010-10-04
oh I see - thanks!

---

