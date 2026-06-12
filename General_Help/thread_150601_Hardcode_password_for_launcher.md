---
title: "Hardcode password for launcher?"
date: 2006-03-26
forum: General Help
---

### Post by elamericano on 2006-03-26
I would like to run some applications and scripts from the Application Launcher without having to enter my password. It's inconvenient enough that my networking doesn't reconfigure automatically, so I just want a silent button that does what I want without a password dialog pop-up.

No hack will be disregarded due to security concerns, we're looking for convenience here ;)  However, it should have some benefit over simply turning off sudo passwords - which is my next step.

-EA

---

### Post by Xian on 2006-03-26
You could add a similar entry (for each launcher) to your sudoers file:

```
username ALL= NOPASSWD: /path/to/executable
```

You could also set up a group to have these privi's:

```
%groupname        ALL=(ALL)       NOPASSWD: ALL
```

---

### Post by aysiu on 2006-03-26
Follow [this model](http://ubuntuforums.org/showpost.php?p=123242&postcount=13), except use whatever command you want instead of the shutdown helper.

---

### Post by elamericano on 2006-03-26
This works for the command line, but when I run the same script from the gnome application launcher I still get a pop-up (actually, I get prompted for each gksudo instance, once for killall, once for wpa_supplicant, etc.)

If I try gksudo --user my_user_name 'killall....'

then it doesn't do anything. I also tried username ALL= NOPASSWD: ALL to see if that made a difference, and it did not.

---

### Post by Xian on 2006-03-26
If you tick the option to 'Run in Terminal' for the launcher it does not help?

---

### Post by elamericano on 2006-03-26
Nope, I get a terminal and then a password dialog.

In summary:
sudo works for free, but gksudo gets a prompt
gksudo -u works from the command line, but gksudo -u from the launcher does nothing

I added root to sudoers too, in case gksudo runs as root, but that wasn't the answer either. I shall continue experimenting. Thanks for the lead, I'm sure this is the right track.

---

### Post by elamericano on 2006-03-26
Thanks Xian,

Is appears that sudo works fine from the launcher rather than gksudo. If the only difference is that gksudo allows a GUI prompt for a password, then it won't ever be a problem in the case where I've disabled the password.

If anyone reads this thread in the future and knows why our sudoers modification didn't disable the password prompt from gksudo, maybe they can let us know.

-EA

---

### Post by terranz on 2006-03-26
cool, now I can make that ipod eject button for the wife :)

---

