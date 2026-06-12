---
title: "Automatically delete files in trash older that 30 days?"
date: 2010-09-26
forum: General Help
---

### Post by Rytron on 2010-09-26
Hi.

How can I automatically delete files in Trash that is older that 30 days? Or is there a simple command that I can put in the terminal to do this manually?

Thanks.

---

### Post by lykeion on 2010-09-26
This maybe:
```
find ~/.local/share/Trash/files ~/.local/share/Trash/info -mtime +30 -exec rm {} \;
```

You could save it as a script and running it daily using cron.
See
[https://help.ubuntu.com/community/Beginners/BashScripting#Scripting](https://help.ubuntu.com/community/Beginners/BashScripting#Scripting)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Rytron on 2010-09-26
> **lykeion said:**
> This maybe:
```
find ~/.local/share/Trash/files ~/.local/share/Trash/info -mtime +30 -exec rm {} \;
```

You could save it as a script and running it daily using cron.
See
[https://help.ubuntu.com/community/Beginners/BashScripting#Scripting](https://help.ubuntu.com/community/Beginners/BashScripting#Scripting)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Hi lykeion.

I get messages such as:
```
rm: cannot remove `/home/rytron/.local/share/Trash/files/firefox-4-for-linux-video-screenshots_files/likebox_data': Is a directory
```

It did however remove some but not all files that were older than 30 days.

---

### Post by lykeion on 2010-09-27
To perform a forceful and recursive remove you could add the -f and -r switches like this:
```
find ~/.local/share/Trash/files ~/.local/share/Trash/info -mtime +30 -exec rm -fr {} \;
```

---

### Post by Rytron on 2010-09-27
Thank you lykeion. It did not delete empty folders (although I think the empty folders were phantoms from the older code you posted). However it does seem to work.

Just to confirm - Does the [COLOR="Red"]+30 [/COLOR] means older than 30 days?

---

### Post by lykeion on 2010-09-27
Yes it does. You could find info on commands using man like this:
```
man find
```
then you can search for mtime by entering
```
/mtime
```
use n and p for jumping to next and prev
use q to quit

---

### Post by Rytron on 2010-09-27
Cheers. I appreciate your help, lykeion. :)

---

