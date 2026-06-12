---
title: "Scripting Alert Message"
date: 2011-08-29
forum: General Help
---

### Post by CorpusWolf on 2011-08-29
I'm looking to script for a message to appear to the user at a set time with or without a current terminal session running.

I have crontab jobs configured to run at a specific time and there is alot for them to do. I have found that when users try to run programs whilst these jobs are trying to run the desktop gets locked up or the jobs do not finish before the next script starts.

Is there a way to have a message pop-up to say not to run any new programs and then ill create one to say that it is now ok to run programs.

Unless anyone can think of a better way to do this.

---

### Post by Habitual on 2011-08-29
```
notify-send "Please do not run any programs for x minutes - Thank you"

```

You could write a cron to run that just before the other cron, or stick that command inside the bash script (or other) so that the user gets notified first (it gets executed first inside the script) then the rest of the script goes on it's merry way.
Or inside the shell script that calls the job and at the end of the script you could use 
```
notify-send "Thank you - you may return to work/play/whatever"

```

Edit:
New cron script:
```

#!/bin/bash
notify-send "Please do not run any programs for x minutes - Thank you"
path/to/your/original/script.sh
notify-send "Thank you - you may return to work/play/whatever"

```

and then crontab new cron script as a replacement for the original.

Other more creative solutions may exist.

---

### Post by CorpusWolf on 2011-08-31
thank you so much. I'll give that a try.

---

### Post by Habitual on 2011-08-31
You are very welcome.

NOTE: if notify-send is not installed, you will be prompted to install the correct package for it with explicit instructions on the terminal.

---

### Post by CorpusWolf on 2011-08-31
Worked perfectly Thankyou

---

