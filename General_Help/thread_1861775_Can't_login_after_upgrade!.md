---
title: "Can't login after upgrade!"
date: 2011-10-16
forum: General Help
---

### Post by Fraoch on 2011-10-16
Hello:

I just updated from 11.04 to 11.10 and I'm now presented with a new login screen.

Only problem is, when I select my name and hit the "Login" button, the screen blinks and I get the same screen right back - the login screen with my name and the "Login" button.  Nowhere does it allow me to enter my password and I cannot login anymore.

I also cannot login as root (it doesn't recognize the password anymore?), nor can I start a terminal prompt (I just get a cursor).  I can only login as a Guest.

So - I can't access my old data and programs, I can no longer login as root and I cannot get a terminal to fix anything either!

What the heck do I do now?

Thanks in advance for any help, this is really a show-stopper.

Info: this may be related to something I did in previous versions- I altered a setting so that I wouldn't be presented with a login screen (I think this was in "Sessions").  Now I am presented with a login screen, but it seems I can't use it.

---

### Post by Fraoch on 2011-10-16
Aha - I entered in "ubuntu 11.10 login problem" into Google and got this:

[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/)

[quote=knulp79 on linuxquestions.org]There was a .Xauthority file in my home folder owned by root and that prevented me from logging in.
Logging in a text console (Alt+Ctrl+F1 at the login screen) and issuing:
sudo rm ~/.Xauthority
solved the issue.
I hope it helps.[/quote]

I got into the recovery console through GRUB and deleted the .Xauthority file in my home folder resolved the issue.  On reboot, I login automatically as normal.

Well, everything's still not normal as I'm not getting the Unity bar to popup so I can't actually do anything :roll: but at least my data is still there.  That's a topic for another thread...

---

### Post by effenberg0x0 on 2011-10-16
Try this:

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart
```

Back to lightdm, try again to login with your user account login / password.

Report back.

Effenberg

---

### Post by hansdown on 2011-10-16
Hi, Fraoch.

Does your login screen look like this?

[http://www.youtube.com/watch?v=umkfltIQgiM](http://www.youtube.com/watch?v=umkfltIQgiM)

The new login does not require clicking, before password.

Just enter your password, and hit enter.

I know, it's strange, but hey....

---

### Post by Fraoch on 2011-10-16
Hi guys - thanks for the replies, but as you see, I did fix that issue by removing the .Xauthority file.  effenberg0x0's method of renaming it to a backup file would have been better, but hey...

Anyway my issues are now:

- the Unity bar doesn't "slide out" or even appear at all from the left side, or anywhere for that matter.  I'm forced to CTRL+ALT+t to get a terminal and issue unity --reset, which hangs partway through but brings up the Unity bar eventually.

- I seem to have lost all Internet access, the Network app says "Wired" is unmanaged and "Configure..." is greyed out.

- my root password seems to be reset, although oddly sudo from my local account still works fine.

For these issues I'll either search the forums or the Internet at large and possibly start a new thread, but I'm marking this thread "solved" now.  Perhaps I should get some sleep first!

At any rate, thanks again.

---

### Post by SquiddyGeiger on 2011-10-16
> **effenberg0x0 said:**
> Try this:

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart
```Back to lightdm, try again to login with your user account login / password.

Report back.

Effenberg

I had the same issue, did this and can now log in - thanks!

---

### Post by cives on 2011-10-17
I have the same issue, as described in this thread ( [http://ubuntuforums.org/showthread.php?p=11359040&posted=1#post11359040](http://ubuntuforums.org/showthread.php?p=11359040&posted=1#post11359040)), but removing the .Xauthority file did not help. 
Can you help me, please?
Thank you in advance.

---

### Post by cives on 2011-10-18
effenberg0x0 solved my problem with this post:
[http://ubuntuforums.org/showpost.php?p=11359168&postcount=11](http://ubuntuforums.org/showpost.php?p=11359168&postcount=11)

---

