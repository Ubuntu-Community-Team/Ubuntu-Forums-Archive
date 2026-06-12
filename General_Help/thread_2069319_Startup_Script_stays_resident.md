---
title: "Startup Script stays resident"
date: 2012-10-10
forum: General Help
---

### Post by Bobhuber on 2012-10-10
Hey All
I added a startup script to load Skype and a couple of screenlets with a slight delay (sleep 1). All works as it should except if I look in the system monitor it shows the sh script as resident (running). I can kill the process manually but cant seem to get it to exit gracefully from the script itself. 
It shows sh as the process running with me as the user  etc.
```
#!/bin/bash
python -u /usr/share/screenlets/screenlets-pack-basic/Output/OutputScreenlet.py 
sleep 1
python -u /usr/share/screenlets/screenlets-pack-basic/Meter/MeterScreenlet.py
sleep 1
skype
exit 0
```

---

### Post by Lars Noodén on 2012-10-10
You probably want to run skype in the background and let the script progress to its end.

```

skype &

```

If the python scripts are also holding up the script, do the same for them, too.

---

