---
title: "Script to set volume levels on startup?"
date: 2010-01-05
forum: General Help
---

### Post by Arkitekt on 2010-01-05
I am using UNR 9.04 with Alsa 1.0.22.1

For some reason everytime I reboot my volume levels reset to headphone & speaker muted and headphone/speaker/PCM levels all set to 0%. 

Does anyone know if there something I can that will allow my levels to be the same after I reboot? or if there is a script out there that will set my levels on startup?

If there isn't a script what would I do to create my own? also what would I do to have it auto run at startup?

---

### Post by davidmohammed on 2010-01-05
... try the following that worked for me in jaunty... haven't needed this though in karmic.

```
#!/bin/sh 

sleep 5

/usr/bin/amixer -c 0 sset Master,0 unmute > /dev/null

/usr/bin/amixer -c 0 sset Master,0 95% > /dev/null
```

---

### Post by Arkitekt on 2010-01-06
will try that, but my master is set to 100% after reboot, it is my headphone & speakers that are muted and headphones/speakers/& PCM set to 0% after reboot

---

### Post by Nedabiah on 2010-05-28
> **davidmohammed said:**
> ... try the following that worked for me in jaunty... haven't needed this though in karmic.

```
#!/bin/sh 

sleep 5

/usr/bin/amixer -c 0 sset Master,0 unmute > /dev/null

/usr/bin/amixer -c 0 sset Master,0 95% > /dev/null
```

Thanks davidmohammed! I couldn't figure out what was wrong with my sound after upgrading to Lucid. Then I ran alsamixer and discovered the 'Speaker' volume was set to 0%. I replaced 'Master' with 'Speaker' in the above script and it worked like a charm. In my case it wasn't necessary to unmute, just to set the volume to a higher level. 

For other newbies like me, you must save the above text into a text editor and name it with the .sh extension (e.g. yourfilename.sh) in your home directory.
Next, start a terminal and run the command 'chmod +x yourfilename.sh' 
Now add a new startup application (System menu>>Preferences>>Startup Applications, then click Add)
Enter the following into the command blank: './yourfilename.sh'
Then the script should run on startup.

---

