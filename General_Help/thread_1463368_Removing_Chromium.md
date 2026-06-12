---
title: "Removing Chromium"
date: 2010-04-26
forum: General Help
---

### Post by holadebob on 2010-04-26
I uninstalled Chromium including config files through synaptic, but then after doing a file search, I found lots of Chromium and Chrome files laying around. So then I used that search list to delete them, but I believe there are still Chromium/Chrome files somewhere on my Ubuntu 9.10.

To regress a bit and for a little background on this problem, I wanted to uninstall Chromium because I want to see if I can correct this problem that I have with the browsing history file. I want the browse history feature to work and it doesn't - the archive has all of the activity from only one day in history, 8 Apr 2010, and when I try to delete that day of history, it says that is has been deleted, but it is still there, and it won't record any of my browse history.

So I thought if I could do a clean install from scratch, maybe I could get the history feature back.

Anybody know where I can find the file containing the history files and/or tell me how to clean reinstall of Chromium? 

Thank you
Bob

---

### Post by geirha on 2010-04-26
That's user settings, and they are stored somewhere in your homedir; in a hidden dir. Uninstalling a package, even purging, will never delete anything in your homedir, so reinstalling an app like chromium will not have any effect.

Most likely the configuration is stored in ~/.config/chromium/ or ~/.chromium/. If you remove/rename that dir, then start the browser, it should be like the first time you started it again.

---

