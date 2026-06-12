---
title: "Firefox is already running, but is not responding..."
date: 2010-07-06
forum: General Help
---

### Post by Xianath on 2010-07-06
Today I tried to start Firefox but, for no apparent reason, I got this message:

```
Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.
```

I deleted the .parentlock file from my profile but it didn't solve the problem. I then looked at ~/.mozilla/profiles.ini and the Path variable was not pointing to my profile folder, instead it had some other profile in there which wasn't present on the filesystem (?!?). So I just changed it back to my profile folder and it working now.

Hope this helps someone who runs in this problem.

---

### Post by jeebustrain on 2010-07-06
can you see firefox-bin if you run top?

try "killall firefox-bin" or "killall firefox" and try again.

---

### Post by Xianath on 2010-07-06
Should have mentioned the obvious, sorry. The error message is quite clear so of course I checked for running instances (of which there were none, I use Chromium) and restarted just in case I missed one. Didn't work, either, which is when I strace'd it and saw what it was trying to do, then went off and fixed it. Still don't know how it got confused about the correct profile since I haven't used in in a few days and haven't ran upgrades, either.

---

### Post by bilkay on 2010-08-21
> **Xianath said:**
> Should have mentioned the obvious, sorry. The error message is quite clear so of course I checked for running instances (of which there were none, I use Chromium) and restarted just in case I missed one. Didn't work, either, which is when I strace'd it and saw what it was trying to do, then went off and fixed it. Still don't know how it got confused about the correct profile since I haven't used in in a few days and haven't ran upgrades, either.
It would be nice if you were more clear about what you did to fix it. This isn't much help to others who encounter the same problem.

---

### Post by fdmille on 2010-08-22
Just delete the profiles.ini file in the folder ~/.mozilla/ and restart Firefox.

---

### Post by Halibutt on 2011-06-13
> **Xianath said:**
> Didn't work, either, which is when I strace'd it and saw what it was trying to do, then went off and fixed it. Thanks for being helpful:confused: That's the kind of solution we all need here: if it doesn't work, the solution is... to fix it. 


> **fdmille said:**
> Just delete the profiles.ini file in the folder ~/.mozilla/ and restart Firefox.Either I'm a complete newbie, or there's no hidden mozilla folder in my root. Searching for the profile .ini file didn't return any files either. Could it be the problem with the fact that I'm trying to use the same profile for my Win7 and Ubuntu firefox instalations?
Cheers

---

### Post by sriny1512 on 2011-12-11
Thanks "geebustrain". [COLOR="Blue"]killall firefox-bin[/COLOR] helped for me :)

---

### Post by SgtT on 2011-12-11
I constantly have the same problem.  The killall firefox-bin worked for me.  Is there a way to create a file on my desktop that I can click on and run without having to open up the terminal and type it in all the time?

Thanks,

T.

---

### Post by isay408 on 2011-12-11
Hi,

This is a glitch in the firefox browser because sometimes not all processes of firefox shutdown at once. And waiting for it will not solve the problem instead you will have to use the Ctrl+Alt+Delete option.

First, hit the "Ctrl+Alt+Delete keys all at once.
Second, open the task manager.
Third, go to the process tab.
Forth, find where it says firefox.exe.
Lastly, select the process and hit end process.

Note:
This might be happen again but not often. If it does, I suggest to update your firefox or reinstall it. You can go to this URL [http://www.techyv.com/questions/firefox-already-running-error-conflict](http://www.techyv.com/questions/firefox-already-running-error-conflict) to get more suggestion about this problem

---

### Post by Cpierce on 2011-12-11
The .mozilla file will be hidden in your home folder, not root. Open your home folder and either ctrl + h or view>show hidden files. You can then delete the profiles file as mentioned before. If you delete the entire .mozilla file, it will be like a brand new install of firefox.

---

