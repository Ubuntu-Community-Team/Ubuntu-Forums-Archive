---
title: "Help with cron (setting a very simple script to run)"
date: 2011-02-18
forum: General Help
---

### Post by Gaba_p on 2011-02-18
I'm trying to get to run every x hours a very simple script (the script works fine, I checked by running it manually) and I can't seem to get Crond to work.
I've followed so many different guides I'm not sure what to do anymore...

First, a few outputs:

[I]$ ps aux | grep crond
<user>  14017  0.0  0.0   3340   832 pts/1    S+   20:29   0:00 grep --color=auto crond

$crontab -l
*/5 * * * * <user> /home/<user>/check-dropbox.sh

$service cron status
cron start/running, process 971

$cron
cron: can't open or create /var/run/crond.pid: Permission denied

$sudo cron
cron: can't lock /var/run/crond.pid, otherpid may be 971: Resource temporarily unavailable[/I]


I'm guessing the last sentence is the key, but I have NO idea how to fix it.

Any help will be very much appreciated.

---

### Post by gzarkadas on 2011-02-19
Cron is running by default; you should never need to type `cron' or `sudo cron' to create a cron job. The problem is your crontab, if - as I assume - you type crontab -e as user to edit it. In user crontabs one **must not** put the <user> entry before the command. Only in the system crontab, /etc/crontab , one needs to specify the user.  Delete this. Also if your .sh script is not executable, place an `sh -c' in front of the script's filename

---

### Post by Gaba_p on 2011-02-19
Thanks or your reply gzarkadas, I did what you told me and deleted the <user> from the user crontab.
Now it looks like this:

$ crontab -l
*/5 * * * * /home/<user>/check-dropbox.sh


(there's a new line at the end of that file because I read somewhere that it was necessary)

It still won't run though.

************************************
Edit

It script IS running, the icon just wasn't showing in the system tray so I thought it wasn't but I checked the system manager and there it was. Now I have to see why it doesn't show in the system tray (the 'Dropbox' icon I mean), but that's another issue.
Anyway, what comes next I would still like to figure out; just so I can understand better the way 'cron' works.

************************************

One thing I don't get is that if I type 'crontab -e', the editor (nano) opens a temp file (/tmp/crontab.Auj8AN/crontab) to edit instead of the file I set up as the user crontab (which is: /home/<user>/crontab) with the command 'crontab -u <user> /home/<user>/crontab'. If I go ahead and edit this file and then save and exit (Ctrl+o, Ctrl+x), what I get when I type 'crontab -l' is the **modified** line **BUT** if I open my 'crontab' file (/home/<user>/crontab) I see that it is **NOT** modified, meaning that it only modified the temp file (??)
If I 'crontab -e' once again the editor shows ANOTHER temp file (/tmp/crontab.ZIQH5v/crontab) to edit and so on... The modified settings will be reflected each time I 'crontab -l' but they will never show in MY crontab file (/home/<user>/crontab)

---

### Post by Dave_L on 2011-02-19
> **Gaba_p said:**
> ...the file I set up as the user crontab (which is: /home/<user>/crontab) with the command 'crontab -u <user> /home/<user>/crontab'...

That form of the crontab command *imports* the specified file as the new crontab.  It does not change the location of the actual crontab file, which is in /var/spool/cron/crontabs/.

---

