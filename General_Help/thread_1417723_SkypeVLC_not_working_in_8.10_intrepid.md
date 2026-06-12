---
title: "Skype/VLC not working in 8.10 intrepid"
date: 2010-02-27
forum: General Help
---

### Post by decrease789 on 2010-02-27
Hi,

I'm having trouble with some qt-based apps that did work previously but now do not. So far I've seen this with Skype, VLC and umbrello. Applications appear to execute but GUI never seems to initialise. CPU remains around 90%. I'm using an eeepc 1000H running ubuntu intrepid 8.10 with adam's kernel 2.6.27-8-eeepc. Any ideas on how I can debug this? As I mentioned these applications worked fine in the past, I'm guessing an update broke them.

thanks :D

---

### Post by decrease789 on 2010-03-09
bump

---

### Post by decrease789 on 2010-03-13
bumpty bump bump bump :popcorn:

---

### Post by Paddy Landau on 2010-03-13
The only thing that I can suggest is to completely uninstall the application (in Synaptic Package Manager, mark for complete removal); delete the application's data directory (for Skype, that would be [FONT=Courier New].Skype[/FONT] in your home directory), then reinstall.

If that doesn't help, then sorry, I don't know.

---

### Post by MichealH on 2010-03-13
Or you may need to get the libs of Skype/VLC ect. ect.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Then use

```
getlibs /usr/bin/skype
```

---

