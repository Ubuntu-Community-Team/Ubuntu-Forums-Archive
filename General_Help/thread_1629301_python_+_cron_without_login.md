---
title: "python + cron without login?"
date: 2010-11-23
forum: General Help
---

### Post by violinuxer on 2010-11-23
I have a python script that i would like to run every hour regardless of whether I am logged in. I have tried putting a link to the script in cron.hourly, however, it does not run. Any ideas?

Should I post the script as well?

Thanks

violinuxer

---

### Post by Cheesehead on 2010-11-23
Common oversights:

1) Forgot to make the script executable.

2) Forgot to put the shebang (#!/usr/bin/python) on the first line, so the system knows it's a python script.

3) Used user-specific shortcuts or application names (~/Desktop or cron) instead of full paths (/home/USER/Desktop or /usr/sbin/cron)

If your script is clean of those common issues, then yes, show us the script.

---

### Post by violinuxer on 2010-11-23
Thanks so much for your quick response :D The python script is attached.

Anyhow, my script retrieves my external IP address from a server and then compares it to one stored on file. If the two are different, it emails me.

For future refrerence, is it better to quote or attach? My code is ~ 220 lines.

Thanks!

violinuxer

---

### Post by DaithiF on 2010-11-23
Files put into the cron.{hourly,daily,weekly,monthly} directories are run by cron using a mechanism called run-parts.  run-parts is a bit choosy about what it will execute, so its good practice to test if the script you place in one of these directories will actually be executed.  Run this command -- it will list the scripts that run-parts will actually run.
```
run-parts --test /etc/cron.hourly

```

hint: in your case your script won't show up in the list of what will be executed, because it has a file extension (.py), and these won't be executed on debian/ubuntu systems because of a (in my opinion), rather draconian convention on file names.  

man run-parts if you want to see what characters are supported.

so your quick fix is either (a) rename your script to remove the .py extension, or (b) move your script somewhere else and create a link to it, with that link named appropriately.

---

### Post by violinuxer on 2010-11-23
Wow guys.... this is such a great help! I redid the link in bash instead of nautlius (nautilus really messes things up!) and everything checks out. Check one more step on my path to world domination :D (actually a cool webmin setup)

Anyways thanks SOOOOO much for your help!

violinuxer

PS Feel free to use the script if you wish :)

---

### Post by violinuxer on 2010-11-23
Another problem arose- It seems like its not working when I'm logged out. Should i be putting my script somewhere else?

violinuxer

---

### Post by violinuxer on 2010-11-23
Okay. I've narrowed the problem down. It seems as though there are some issues with the code itself. In my code, I am trying to work in /root, however, the hardlink uses /etc/cron.hourly as its working directory. This creates all sorts of problems. I am thinking i might add an entry to /etc/crontab. Would this run similar to cron.hourly? I could then explicitly point to the actual file in /root.

Thanks

violinuxer

---

### Post by nl4m on 2010-11-23
This maybe stupid, but try adding this to you "/etc/bashrc" file:
```
While true
do
/home/username/name-of-python-program
sleep 3600
done
```It should execute your program every 3600 seconds (1 hour).

---

### Post by efflandt on 2010-11-24
> **violinuxer said:**
> Okay. I've narrowed the problem down. It seems as though there are some issues with the code itself. In my code, I am trying to work in /root, however, the hardlink uses /etc/cron.hourly as its working directory. This creates all sorts of problems. I am thinking i might add an entry to /etc/crontab. Would this run similar to cron.hourly? I could then explicitly point to the actual file in /root.

That would sort of be 3) Basically you should assume "nothing" in the environment when running from cron.  Your script should set anything it uses directly, or export anything that a subprocess needs, or cd to the directory you want.

See **man 5 crontab** in a terminal.

---

### Post by violinuxer on 2010-11-24
It looks like I got things working. I should note that this script, to make it more user-friendly, gets configuration data from the user (dynamic). It is stored in a file in the working directory. When I configured my script using --config, i did so using sudo from _my_ home directory. The config file was then put in my home directory instead of /root. When cron tried to run the script as root from /root, it would run, but would exit with an error indicating that it couldn't find the config file. I had caught all these exceptions beforehand and didn't have any indication of them. After configuring as root using su, the script works like a charm.

Moral of the story: sudo != su. I guess sudo doesn't change the user totally:p

Anyways, you guys have been such a great help! It is really cool that there is this kind of community out there!:guitar:

Best of luck in all your work!

violinuxer

---

