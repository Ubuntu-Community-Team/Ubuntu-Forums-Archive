---
title: "printing to file tweaks"
date: 2010-09-03
forum: General Help
---

### Post by ant2ne on 2010-09-03
I'm doing a lot of print to file and selecting pdf. It is an awesome feature. But I'd like to add a location to the "Save in folder" drop down menu. What would be better is to add a location, and then make it the default location. It would also be awesome to change the default from .ps to .pdf. This would greatly speed up my save to file process. Any ideas on how to make these tweaks?

---

### Post by gzarkadas on 2010-09-03
I don't know if what you ask is configurable, but there is another alternative, as described [here,]("http://embraceubuntu.com/2006/03/23/print-to-pdf-using-cups-pdf/") in post no. 27 specifically. I have test it on my system and selecting this printer results in a pdf document created inside ~/PDF. Now, if this is not the desired default location, then you could try to:

1. Make ~/PDF a symbolic link to the desired location and see if the printer remains functional. If yes, then you are done.

2. If (1) is not available, setup a cron job to rsync ~/PDF and the default location, say every 5 minutes. A possible crontab entry is the following:

```

0-55/5 * * * * rsync -vaXA /home/<your-account>/PDF/ <your-desired-default-location>/

```

---

### Post by SoFl W on 2010-09-03
> **ant2ne said:**
> It would also be awesome to change the default from .ps to .pdf. 
That would be a great idea.

---

