---
title: "start python script at boot"
date: 2010-01-17
forum: General Help
---

### Post by cmadooly on 2010-01-17
Hi Guys,

I know this has been posted on the boards before and I've found several links on google that dance around the same thing but for some reason, I just can't get this to work. Someone please end my misery.

I'm not really new to linux but I have no experience in python or bash scripting. I'm sure this is something very simple.

I am trying to get a python script to start when the pc is booted. I'm running ubuntu server without a GUI... just CLI.

I have a python script called /home/username/bin/dropbox.py that runs perfectly if I do:

```

sudo python /home/username/bin/dropbox.py start

```

All I want to do is invoke the command I wrote up there when the pc boots up without any user logging in.

I added the above command just like that in rc.local but that didn't work.
I tried creating a bash file, where in the bash file I did:
```

#!/bin/bash
cd /home/username/bin/
./dropbox.py start

```

 and then added the bash file to rc.local, but that didn't work (I made sure the bash file was executable).

HELP!! Any assistance is much appreciated.

---

### Post by Barriehie on 2010-01-17
Have you looked at **update-rc.d**?

---

### Post by cmadooly on 2010-01-18
> **Barriehie said:**
> Have you looked at **update-rc.d**?

just ran it, says that it was missing LSB information but the links already exist

```


update-rc.d: warning: /etc/init.d/dropbox missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
System start/stop links for /etc/init.d/dropbox already exist.


```

not sure if that's anything to be concerned about.

---

### Post by Barriehie on 2010-01-18
How about changing your bash script to:
```

bash -c /home/username/bin/dropbox.py start &
exit 0

```

---

### Post by cmadooly on 2010-01-18
> **Barriehie said:**
> How about changing your bash script to:
```

bash -c /home/username/bin/dropbox.py start &
exit 0

```

I made some progress.. getting there but one small hurdle now.

I realized I was using rc.local (a bash file) to call another bash file (dbscipt) to call a python file (dropbox.py).

I decided to remove the middle man and call rc.local directly to dropbox.py like this (thank you Barriehie, got the idea from you):

```

bash -c python /home/username/bin/dropbox.py start &

```

Now, this DOES in fact launch the process, but it's launched as "username" rather than "root". It needs to launch as root in order to work.

I thought everything that rc.local launched was with root privileges?

So now the question is. How do I launch the command 

```

bash -c python /home/username/bin/dropbox.py start &

```

as root during boot (without being asked for a password of course)?

---

### Post by Barriehie on 2010-01-18
I've seen this referenced somewhere before so you might give it a shot.  You can put the command in /etc/crontab and use the @reboot directive to launch at boot/reboot time.  This also enables being able to launch as root.

Never tried it on my system but I've seen multiple references to this syntax.

Go down to operators... [[color="blue"]crontab commands[/color]](http://en.wikipedia.org/wiki/Cron#Operatorsl)

Check out [color="red"]@reboot[/color]

HTH,

---

