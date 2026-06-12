---
title: "startup applications not saving after reboot"
date: 2011-05-11
forum: General Help
---

### Post by xaphan88 on 2011-05-11
using ubuntu 10.4, have set a custom command to open my browser to a page using the following in System -> Preferences -> Startup Applications
```
chromuim-browser -kiosk http://wallboard
```
this works, but only for the next restart, any subsequent restart, and this 'application' has vanished from the list...
how do i add this 'application' as a persistent entry, not just for the next restart.

---

### Post by xaphan88 on 2011-05-13
> **xaphan88 said:**
> using ubuntu 10.4, have set a custom command to open my browser to a page using the following in System -> Preferences -> Startup Applications
```
chromuim-browser -kiosk http://wallboard
```
this works, but only for the next restart, any subsequent restart, and this 'application' has vanished from the list...
how do i add this 'application' as a persistent entry, not just for the next restart.

BUMP.

kinda getting desperate now, i dont want to keep adding this every time it loads (every day). going to go back to windoze if ubuntu cant even do a simple custom startup application...

---

### Post by varunendra on 2011-05-14
> **xaphan88 said:**
> going to go back to windoze if ubuntu cant even do a simple custom startup application...
:D
you see, freedom is our motto here ;)....

Anyway, firstly your command contains spelling error (chrom[COLOR=Red]**ui**[/COLOR]m??), which I'm sure is a typo in your post (since you say it works at least once). Secondly, I couldn't manage to run it even once using even corrected spelling in startup command, unless I modified it to:
```
/usr/bin/chromium-browser -kiosk <any url>
```(where <any url> is [http://wallboard.com](http://wallboard.com) in your case)
It allowed it to startup everytime I restart.

However, once it worked, changing back to chromium-browser -kiosk <any url> did not bring the problem back. So I guess adding the /usr/bin part in the command is all you need. The final command for you would be:
```
/usr/bin/chromium-browser -kiosk http://wallboard.com
```If this doesn't help, post back the output of the following command:
```
cat ~/.config/autostart/chromium-browser.desktop
```

---

### Post by shashanksingh on 2011-05-14
I got a similar problem.

System->Preferences->Startup Applications

I added the following command

google-chrome

which starts chrome from my terminal.

But the entry vanishes after a restart.
When I made a manual entry in my .profile with google-chrome &, it works

---

### Post by sur4die on 2011-05-23
I had this same problem, what I discovered was that some how the autostart folder was owned by root...

```
sudo chown <USERNAME>:<USERGROUP> ~/.config/autostart
```

---

### Post by kaaloo on 2011-06-26
Good call!  That was the issue for me too.

---

