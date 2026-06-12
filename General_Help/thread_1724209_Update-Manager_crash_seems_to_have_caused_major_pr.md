---
title: "Update-Manager crash seems to have caused major problems"
date: 2011-04-08
forum: General Help
---

### Post by davepoth on 2011-04-08
This is a Natty system, but I don't know whether it's related or whether enough people read there to find an answer.
 
I ran update manager to update to the latest releases for Natty, and it crashed. I ran it again and it told me it could only do a partial upgrade, and that I should do apt-get install -f. I did that, but apt-get told me the system was locked by another program. Not to worry I thought, I'll just reboot.
 
So I did that, and I think Update-Manager got a lot further through the process than I thought, because my system is borked. It'll boot into Gnome, but when booting up the Boot Screen no longer shows the pretty Ubuntu Logo, but rather a line of text that says "Ubuntu 11.04". When it gets into Gnome the keyboard and mouse more or less don't work (although the keyboard based Fn+9 and Fn+10 brightness controll still works) and there is no desktop background. After about 30 seconds something crashes but I can't click on it to find out what.
 
Going into the recovery console doesn't help either. The latest Kernel (2.6.38-7) stops moving forwards after "Begin:Running /scripts/init-bottom...done". has occurred for the second time.
 
Luckily I still have the previous kernel (
 
which gets to the same spot and then tells me "init: udevtrigger main process (390) terminated with status 1" and then "init: udevtrigger post-stop process (394) terminated with status 1".
 
I then get the message "The disc drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery". S goes back to "Begin:Running /scripts/init-bottom...done" a second time, M brings up the message
 
"Root filesystem check failed
A maintenance shell will now be started"
and then it asks for the root password and gives me a terminal.
 
Everything seems to be there, but apt-get and dpkg both can't do anything as the filesystem is read only. 
 
I'm really a bit stuck and this is a bit beyond my skills. Any ideas?

---

### Post by jacobmh on 2011-04-12
I need this answered. There have been a lot of people dodging around this issue, but from the forums and the bug report filed for it, it's actually a pretty big issue.

---

### Post by stevepowell99 on 2011-04-12
exactly the same thing happened to me. Having no luck. Disk and filesystem are OK.

---

### Post by stevepowell99 on 2011-04-12
Fixed it! after pressing m to manually fix the problem, I did a 
```
mount -o remount, rw /
```
and that remounted the partitions as in the /etc/fstab. If you want to (re-)mount differently, look at man mount.
So that gave me a mounted, read-write filesystem.
So then I was able to do sudo apt-get update -f, which told me I needed to reconfigure dpkg, which I did by following the instruction (can't remember exactly what).
Now it works! :popcorn:

---

### Post by sam.crowther on 2011-04-28
thanks Stevepowell99,

sudo apt-get update -f was the missing step, issues with winbind, but i'm sure i can suss that out now i have a desktop again.

---

### Post by rungss on 2011-04-30
> **stevepowell99 said:**
> Fixed it! after pressing m to manually fix the problem, I did a 
```
mount -o remount, rw /
```

I was able to Configure and run Ubuntu after following the above steps

But Now I don't see all my Panel Items, nor can I add the most necessary items.
When I click on Add to Panel, I don't see Notification Applet, Information Applet etc in the list..

Any idea?

I can't connect to Internet either..

Edit:
I got it to Work.
Here is the steps I followed.

I ran ```
sudo apt-get upgrade
```
It asked me to run ```
sudo apt-get -f install
``` as there was dependency Problem

I did that.
When done I ran ```
sudo apt-get upgrade
```
Then again I ran ```
sudo apt-get dist-upgrade
```

And Rebooted, All is well now..

---

### Post by JimPBarber on 2011-04-30
Same issue here.  However, I tried the fixes here and I got another error stating that there were too many errors and then it stopped.

  After a reboot I am in the same spot of S to skip or M to manually fix.

---

### Post by dakota34 on 2011-04-30
thanks stevepowell99, worked like a charm

---

### Post by Chris Agg on 2011-05-01
After 
```
mount -o remount, rw /
```I try to run
```
sudo apt-get update -f
```but get:
```
"E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?"
```I am root. Was running the upgrade to 11.04 from an up-to-date system on 10.10.
Please anybody help me!!

---

### Post by AreEK on 2011-05-01
> **Chris Agg said:**
> After 
```
mount -o remount, rw /
```I try to run
```
sudo apt-get update -f
```but get:
```
"E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?"
```I am root. Was running the upgrade to 11.04 from an up-to-date system on 10.10.
Please anybody help me!!
Maybe ```
/var
``` is on a different device? You could try ```
mount -o remount, rw /var
```

---

### Post by Chris Agg on 2011-05-02
I tried 
```
mount -o remount, rw /var
```[FONT=monospace]
[/FONT]
[FONT=monospace]with the result
[/FONT]```
mount: you must specify the filesystem type
```[FONT=monospace]
???

then I tried
[/FONT]```
sudo mount -a
```
and get
```
mount: unknown filesystem type 'xfs'
```
???
[FONT=monospace] [/FONT]

---

### Post by AreEK on 2011-05-03
can you post the contents of your /etc/fstab file?

---

### Post by krige on 2011-05-05
I am stuck with the same problem. I left the system upgrading from 10.10 to 11.04 last night, and when I checked this morning I found the following message:

```
udevd[290]: can not read '/etc/udev/rules.d/z80_user.rules'

init: udevtrigger main process (377) terminated with status 1
init: udevtrigger post-stop process (388) terminated with status 1
init: udevmonitor main process (376) killed by TERM signal
The disc drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery
```

Unfortunately I am not able to enter the manual mode because the system is frozen: it does not do anything, no matter what key I press.

---

### Post by krige on 2011-05-07
I fixed it by following these instructions:
[http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation/](http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation/)

---

