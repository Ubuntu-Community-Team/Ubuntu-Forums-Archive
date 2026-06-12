---
title: "Cronjob + update = 12"
date: 2010-10-09
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-10-09
not really, 

i have a peculiar problem, since the update manager is unreliable to up date the system i have resorted to a shell script and a cron job. there are a few questions i have. the first is the most important.

1) the script enclosed here does not seem to work when run through a cron job, although when executed through a shell manually it works fine, the cron job itself is working fine, i made a shellscript that creates a random directory, it worked no problem. The cron logs also show the job running the script. i have no idea why it will not run the update script included.

#NOTE
 i require to use gksudo and also notify-send as it is not my computer i am setting this up on. ( the user i am setting this up for is not that great on computers, so i am trying to make it as brainless as possible)




2) can i still run cronjobs as root even though the root account is disabled?

3) is there any way to send a notification to the currently logged in user other than the method i am using? will the method is use work when run under root? ie will it send notifications to normal users?


```
#!/bin/bash
#/bin/mkdir /home/<name>/Desktop/new

GUI_user="$( who | grep ' tty' | grep ' (:0' | cut -d ' ' -f 1 )"
/usr/bin/gksudo -u $GUI_user /usr/bin/notify-send "Updating system, do not power off!"
/usr/bin/gksudo '/usr/bin/apt-get update'
/usr/bin/gksudo '/usr/bin/apt-get upgrade -y'
/usr/bin/gksudo '/usr/bin/apt-get autoremove -y'
/usr/bin/gksudo '/usr/bin/apt-get check -y'
/usr/bin/gksudo '/usr/bin/apt-get clean -y'
/usr/bin/gksudo -u $GUI_user /usr/bin/notify-send "Update complete, safe to power off!"

```


ty

---

### Post by dcstar on 2010-10-09
> **NiGhtMarEs0nWax said:**
> not really, 

i have a peculiar problem, since the update manager is unreliable to up date the system i have resorted to a shell script and a cron job. there are a few questions i have. the first is the most important.

1) the script enclosed here does not seem to work when run through a cron job, although when executed through a shell manually it works fine
.........

[LIST=1]
[*]Update Manager seems to work fine for the majority of users - including me.
[*]There are already many posts explaining how to set up cron jobs with GUI apps - search them out for details.
[/LIST]

---

### Post by john newbuntu on 2010-10-10
1.  I have a feeling you might be missing the DISPLAY variable in your environment. Check this: [https://help.ubuntu.com/community/CronHowto#GUI%20Applications](https://help.ubuntu.com/community/CronHowto#GUI%20Applications)
or just add this as the first line to your script after the shebang line:
export DISPLAY=:0.0

2. Yes you can run jobs using sudo/gksu in crontab with root account disabled.

3. Zenity is probably more popular or try xmessage.

But my update manager seems to work just fine.
Also, 'whoami' directly gives you the username.

---

### Post by chrisbay90 on 2010-10-10
2. Yes. sudo crontab -e
3. seconding John's point, try zenity works very nicely, if you  search the forums there is lots of help using it.

---

### Post by NiGhtMarEs0nWax on 2010-10-10
Hi guys, thanks for the tips. The script works fine when run through a shell, but i am having one issue when running it through a cron job. I also have 2 other quick questions if you have time. :)

1) running this script through a cronjob give me this error message.

> Failed to run apt-get update as user root.

Unable to copy the user's Xauthorization file.


2) --no-cancel parameter for zenity --progress does not exist for the ubuntu package, it does however on arch. is there a workaround?
3) i have noticed that apt-get upgrade does not upgrade the kernel. it lists it and the kernel headers as 'packages' not upgraded. when i used ubuntu before, i had to use the update manager for that purpose. is there a workaround? or am i completely wrong?

thanks.

```

#!/bin/bash
export DISPLAY=:0.0
PATH=$PATH:/usr/bin

zenity --question --text="Would you like to update your system now?" --ok-label="Yes" --cancel-label="No"

if [ $? == 0 ]; then
    (gksudo 'apt-get update' && gksudo 'apt-get upgrade -y' \
    && gksudo 'apt-get autoremove -y' && gksudo 'apt-get check -y' \
    && gksudo 'apt-get clean -y') | (zenity --progress --pulsate --auto-close)
else
    exit 0;
fi

```

---

### Post by john newbuntu on 2010-10-10
1. "touch .Xauthority" on the users home directory might help.
2. It exists on version 2.32.0-0ubuntu1. Don't know of a workaround.
3. update and upgrade merely retrieve the index files and packages.  dist-upgrade does the install I think.  Would you rather run /usr/bin/update-manager instead of all those commands if the user chooses yes and follow it up with autoremove in the end.

---

### Post by NiGhtMarEs0nWax on 2010-10-13
touch .Xauthority done the trick.

i will open a new thread if i have any further problems.

---

