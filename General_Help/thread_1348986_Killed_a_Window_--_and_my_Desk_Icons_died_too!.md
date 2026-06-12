---
title: "Killed a Window -- and my Desk Icons died too!"
date: 2009-12-07
forum: General Help
---

### Post by Call My Function on 2009-12-07
I've encountered this problem a few times so far. Sometimes, when I'm working with a file window (such as my music folder, or whatever), it might freeze or otherwise misbehave, so I use the force-quit thinger, click on it, and it closes. But then my desktop icons disappear! (I can still access windows via the toolbar at the top -- i.e. Places, Applications, etc.)

From my experience with Windows, I figured that I had killed whatever process that manages the desktop and folder windows. (In Windows this would be explorer.exe.) The only way I can get the icons to reappear is to restart my computer.

I did some Googling and found some things, but they seemed to refer to worse problems than what I'm dealing with. I found one suggestion that I tried; in the terminal I typed:
[php]nautilus &[/php]It appeared to start up and my icons appeared, but it displayed the following errors:
[php][1] 4741 
(nautilus:4741): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:4741): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4741): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4741): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.[/php]However, as soon as I close the terminal, everything disappears again.

Any ideas?

---

### Post by pqwoerituytrueiwoq on 2009-12-07
logout/in or restart should do it

---

### Post by gradinaruvasile on 2009-12-07
Of course it dissapears. Because processes launched from terminals are bound to that terminal. If its closed the programs are closed too.

Press alt+f2 and type nautilus then press enter. Close the opening nautilus window, its not necessary. You will get back your desktop icons'n'stuff.

---

