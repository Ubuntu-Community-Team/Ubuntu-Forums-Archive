---
title: "Cannot apply display settings"
date: 2012-07-25
forum: General Help
---

### Post by shiftee on 2012-07-25
Hi all,

Yesterday I clicked "Restart to complete updates" but decided to go into windows to try something when the system got the the grub menu.
Since then i've been having problems with unity, mainly:

[LIST]
[*]Cannot reproduce my dual monitor setup, any attempt to apply changes gives "failed to apply configuration: %s"
[*]No window decoration on startup (it is enabled in compiz settings), this can be resolved by doing a "unity --reset" from one of the text consoles
[*]No dock or system menu on startup, also resolved by unity --reset
[/LIST]
None of these issues occur with the other user accounts which leads me to believe that I have some sort of configuration error in my own account.


If I could get my dual monitor setup working again I could get by, and hope that future updates would cause the problems to disappear.


Does anyone have any suggestions??


Thanks,


Mark

---

### Post by clappboard on 2012-07-25
Have you tried going into a terminal (Ctrl+Alt+t) and typing
```
sudo apt-get update
```and once it finishes updating the package lists
```
sudo apt-get upgrade
``` then rebooting?
It's a long shot, but it might accomplish something.  If that doesn't work, try switching to a TTY console (Ctrl+Alt+F1) and logging in.  Then type
```
unity --reset
``` and hit enter.  After that just hit Ctrl+Alt+F7 to switch back to unity.

---

### Post by shiftee on 2012-07-25
> **clappboard said:**
> Have you tried going into a terminal (Ctrl+Alt+t) and typing
```
sudo apt-get update
```and once it finishes updating the package lists
```
sudo apt-get upgrade
``` then rebooting?
It's a long shot, but it might accomplish something.  If that doesn't work, try switching to a TTY console (Ctrl+Alt+F1) and logging in.  Then type
```
unity --reset
``` and hit enter.  After that just hit Ctrl+Alt+F7 to switch back to unity.


Yep, i've also tried reinstalling most of the packages involved, updating the kernel, copying some of the config files from another account. I don't know too much about unity and the window managers etc. so I could be missing something simple. I have however fruitlessly googled the error messages and tried numerous suggested solutions.

The "unity --reset" command will start unity and the window decoration however I still cannot set the display options.

Thanks

---

### Post by clappboard on 2012-07-25
It could be display-manager related (in this case GDM).  Could you post the result of ```
dmesg
``` after you've just booted up and logged in?

---

### Post by shiftee on 2012-07-26
Fixed!!

I played around with 
```
sudo dpkg-reconfigure gdm
```and deleted my .profile file (advice from another thread)

I think it was due to my adding some commands to my .profile (start skype and a text editor).
I then didn't restart the machine for 3 days, making the problem harder to detect.

This problem took me a full day and a half to resolve. I'm glad my boss is on holiday:):)

Thanks for your suggestions

---

