---
title: "Schedule automatic updates and shutdown AFTERWARDS."
date: 2010-02-18
forum: General Help
---

### Post by hariks0 on 2010-02-18
Hi all, Can somebody tell me how I can schedule automatic update and automatic shutdown AFTER the update completion. Please tell me if the following will be sufficient.
```
#!/bin/bash
sudo apt-get -y update
sudo apt-get -y upgrade
sudo shutdown now
```

My requirements are :-

1. Wake PC from sleep/hibernate [If possible]
2. Run the download of update/upgrade
3. COMPLETE INSTALLATION OF the updates
4. Shutdown the PC.

Should I add this cron job as root?

Thanks in advance.

---

### Post by cariboo on 2010-02-18
IF you system is asleep/hibernating, it is affectively turned off, so nothing is running. You would have to wake the system up before the script would run. I would suggest running the script as root in a cron job so you don't need to run sudo for each command.

Your script would look something like this:

```
apt-get update && apt-get -y upgrade && shutdown -h now
```

---

### Post by hariks0 on 2010-02-19
Is it not possible for cron to wake the hibernating/asleep PC? I thought there was such an option in windoze [ And hence of course in Ubuntu much way back:p]

---

### Post by wrose51106 on 2010-02-19
Set the PC to wake in the BIOS at set time. Set crown job to check for updates, I guess make a script and try.

-Bill

---

### Post by hariks0 on 2010-02-19
Hurrah, [This link]("http://ubuntuforums.org/showthread.php?t=313884&highlight=power+saving") describes how to boot a PC - even if it is switched off. Adding a crontab job to root does the magic.

I thought moving a bit further and doing shutdown if no download [like torrents] is in progress. How can I do that?

Or should I mark the thread as solved?

Thank you all.

---

