---
title: "cron and scripts help"
date: 2011-08-20
forum: General Help
---

### Post by polardude1983 on 2011-08-20
So i have a script that runs all scripts in a certain directory (scripts are different over time)
and then it moves the scripts to another directory.

So lets say I call it startscripts.sh and here is the code

```
#!/bin/bash
scripts_to_run_dir=/home/christoph/commands
scripts_archive_dir=/home/christoph/old
shopt -s nullglob
for script in "$scripts_to_run_dir"/*
do
    if [[ -x "$script" ]]; then
        "$script"
        mv "$script" "$scripts_archive_dir"/
    fi
done
```

Now when I right click on the startscripts.sh and hit run it runs all the scripts in the commands folder and moves them to the old.

but when I create a scheduled task (in the Scheduled Task app) and put sh startscripts.sh in the command box it doesn't run any scripts in the commands folder. why? How can i correct this?

---

### Post by papibe on 2011-08-20
To make sure your script is on the crontab try this:
```
$ crontab -l
```
Make sure you have the full path to your script, e.g.:
```
0 0 * * * /path/to/startscripts.sh
```
Hope it helps,
Regards.

---

### Post by kerry_s on 2011-08-20
Drop the "sh", make sure the script is executable.

---

### Post by polardude1983 on 2011-08-20
If i have the startscripts.sh in the scheduled tasks

While it doesn't run the scripts in the /commands/ folder, it does move them to /old/ though which is strange.

---

### Post by papibe on 2011-08-20
Could you post one of those scripts? (They have to be non-interactive scripts).

Regards.

---

### Post by polardude1983 on 2011-08-20
Just a very simple script to see if it works. This is an example script I would have in the commands folder.

```

#!/bin/bash
transmission

```

If i do startscripts.sh through cron it won't activate the transmission script, it just moves it to the old folder without executing it.

---

### Post by papibe on 2011-08-20
Well, that's is a graphical application. It's beyond the basic scope of cron. It doesn't mean you can't do it, but you need to do a few tricks.

Check the section 'GUI applications' on this [tutorial]("https://help.ubuntu.com/community/CronHowto").

Regards.

---

### Post by polardude1983 on 2011-08-20
So maybe i need to add the startscripts to the root cronjob? instead of normal user cron?

---

### Post by papibe on 2011-08-20
In this case isn't a matter of privileges. Cron runs on a very limited environment. In order to run graphical applications you need to widen the limitations by defining the DISPLAY variable (the xhost part shouldn't be necessary).

I hope that clears things a little bit,
Regards.

---

### Post by kerry_s on 2011-08-20
It's "transmission-gtk" not just "transmission"
Perhaps you should try your commands in terminal first.

---

### Post by polardude1983 on 2011-08-20
> **kerry_s said:**
> It's "transmission-gtk" not just "transmission"
Perhaps you should try your commands in terminal first.

I have and "transmission" works

---

### Post by polardude1983 on 2011-08-20
> **papibe said:**
> In this case isn't a matter of privileges. Cron runs on a very limited environment. In order to run graphical applications you need to widen the limitations by defining the DISPLAY variable (the xhost part shouldn't be necessary).

I hope that clears things a little bit,
Regards.

OMG that was so frickin simple lol

---

### Post by papibe on 2011-08-20
> **kerry_s said:**
> It's "transmission-gtk" not just "transmission"
Perhaps you should try your commands in terminal first.
I believe that's the name of package, and the executable is just the shortname:
```
$ apt-cache policy transmission-gtk 
transmission-gtk:
  Installed: 1.93-0ubuntu0.10.04.1
  Candidate: 1.93-0ubuntu0.10.04.1
  Version table:
 *** 1.93-0ubuntu0.10.04.1 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Packages
        100 /var/lib/dpkg/status
     1.92-0ubuntu2 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages


$ whereis transmission-gtk
transmission-gtk:


$ whereis transmission
transmission: /usr/bin/transmission /usr/share/transmission /usr/share/man/man1/transmission.1.gz

```
Regards.

---

### Post by polardude1983 on 2011-08-20
Though question so as long as the graphic program is running is there no way for it to move the script to the old folder while the graphic program is running?

Meaning like I don't want it to open like 20 instances of the same program.

---

### Post by kerry_s on 2011-08-20
i'm using lubuntu 11.04, transmission is "command not found" on mine. see pic

---

### Post by papibe on 2011-08-20
> **kerry_s said:**
> i'm using lubuntu 11.04, transmission is "command not found" on mine. see pic
Interesting! I wasn't aware of that difference. Good to know :P

---

### Post by polardude1983 on 2011-08-20
Yeah I'm using 10.04 and the opposite is true for me :D

Transmission found
transmission-gtk not found

---

### Post by papibe on 2011-08-20
> **polardude1983 said:**
> Though question so as long as the graphic program is running is there no way for it to move the script to the old folder while the graphic program is running?

Meaning like I don't want it to open like 20 instances of the same program.
Without making any observation on the purpose and design of your script, you can easily solve that issue by sending transmission to the background:
```
#!/bin/bash
transmission &
```
This is more of like a patch solution. Now that you understand the basics, you may rethink your strategy.

Regards.

---

### Post by kerry_s on 2011-08-20
> Yeah I'm using 10.04 and the opposite is true for me 

Transmission found
transmission-gtk not found

i'll remember that for next time, i should ask what version first, i always assume people would be running the latest.

i'm thinking to make sure there's no other transmission:
```

#!/bin/sh
killall tranmission
transmission &
exit 0

```

---

### Post by polardude1983 on 2011-08-21
I would be running the latest but, 11.04 freezes too much and yes I know a kernel update can fix it, which I had updated to 3.0 kernel but then there were more problems. I tried looking for 2.9 kernel but couldn't find it. Anyways, gonna stick with the LTS releases plus I like gnome 2.x, And yes i know that 11.04 you can select classic desktop.

But these and probably more are my reasons for sticking to LTS.

Now I don't want to derail my own thread :D hehe.

---

