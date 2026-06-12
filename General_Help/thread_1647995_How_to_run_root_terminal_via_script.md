---
title: "How to run root terminal via script"
date: 2010-12-18
forum: General Help
---

### Post by ajack38 on 2010-12-18
Hi, I have been creating a script for about 5 minutes now and I am stuck. I was wondering if anyone knew how to open a root terminal session and make it run a code and when finished close itself.

The script is for Wondershaper.

#!/bin/bash

sudo wondershaper eth0 500 128

I tried it and nothing worked but when I launched it through sudo or through root terminal it worked perfectly. So like I said earlier, Is there a way to make a script that will open root terminal, Activate "sudo wondershaper eth0 500 128" wait for it to finish and then close itself?

---

### Post by sikander3786 on 2010-12-18
Why not invoke the script with sudo?

```
sudo bash whatever
```

---

### Post by ajack38 on 2010-12-18
I know a bit about linux coding but not much. Would that require the user to type their password? Or would it do it without the user noticing? What would I need to change the coding to? :s sorry if this is a pain, I'm not good with scripts.

---

### Post by QLee on 2010-12-18
[QUOTE=ajack38]... Would that require the user to type their password? Or would it do it without the user noticing? What would I need to change the coding to? ....[/QUOTE]

If I understand you correctly, you want help writing a script that does something as root and that is hidden from the user.

---

### Post by ajack38 on 2010-12-18
My son goes through the internet like it is nothing, Since we only get 120 Gbs a month I have found Wondershaper which slows our internet down. I am trying to make sure that he doesn't deplete it again like it already has this month. So, Yes.

---

### Post by lmarmisa on 2010-12-18
Consider to use **cron** and **crontab**:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by ajack38 on 2010-12-18
Right now I'm looking at sentinella, But I don't know if that runs the command through sudo.

---

### Post by lmarmisa on 2010-12-18
If you need to run only once this command at startup with root privileges, then include it in the file **/etc/rc.local**. Do not add any **sudo** prefix because this file is executed with root privileges.

Use this command to edit the file **/etc/rc.local **

```

sudo gedit /etc/rc.local

``````

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**wondershaper eth0 500 128**

exit 0

```

---

### Post by ajack38 on 2011-01-28
This has helped me a lot but I was wondering If there was a way to set times for this to start and Finish?

---

### Post by yetiman64 on 2011-01-28
> **ajack38 said:**
> This has helped me a lot but I was wondering If there was a way to set times for this to start and Finish?

Post #6 cron/crontab. Study up how it works.

To edit your user crontab,
```
crontab -e
```As mentioned earlier, your process needs root privileges so will need to use root's crontab i
```
sudo crontab -e
```You can use a couple of entries, one to start and one to stop the process, you may need more if the start and stop times are to vary.

---

