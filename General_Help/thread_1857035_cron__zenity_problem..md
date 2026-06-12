---
title: "cron / zenity problem."
date: 2011-10-09
forum: General Help
---

### Post by histamineblkr on 2011-10-09
I want to have a cron job call a shell script that pops up a zenity information dialogue box.

What I have done so far:

I edited my crontab with: **crontab -e**

my entry in crontab is: *** * * * * ~/bin/scripts/bash/payday.sh**
(I purposely made it a cron job every min for easy testing)

my shell script is a very simple one liner (beside the hash bang):
**#! /bin/bash**
**zenity --info --title="Pay Day" --text="Today is pay day."**

I ran the script first and it has no problem running and does exactly as expected. I have googled many things on zenity but nothing seems close to the problem I am having, but maybe I just didn't search the right criteria.

I did redirect the output of the error to a file and ended up with this:
**(zenity:18966): Gtk-WARNING **: cannot open display:**

The number 18966 changes every time the cron job runs so I thought it was the process id of zenity but I'm not sure if process ids change. I tried to google this warning and didn't come up with much. Other people theorised at a possible permissions problem but I don't think that's the case but to rule it out I just chmod 777 the script to make sure .

So if anyone has any idea why zenity can not display and how to fix it that would be great.

Thanks for any help.

---

### Post by matt_symes on 2011-10-09
Hi

You need to export the display variable. Add this to your script or to your crontab

```
export DISPLAY=:0
```

Use the full paths to executables.

```
/usr/bin/zenity
```

Kind regards
[COLOR=#000000][FONT=Times New Roman][LEFT][FONT=verdana] [/FONT][/LEFT][/FONT][/COLOR]

---

### Post by histamineblkr on 2011-10-10
Hey Matt,

Thanks for the response. Who would of thought it was something so simple as to export the display variable, worked like a charm.

Now for this part **/usr/bin/zenity**, since I'm having cron call a shell script named payday.sh isn't me having **/bin/bash** the correct path for cron?

Thank you for your help.

---

### Post by matt_symes on 2011-10-10
Hi
> 
Now for this part **/usr/bin/zenity**, since I'm having cron call a shell script named payday.sh isn't me having **/bin/bash** the correct path for cron?
If it understand you correctly then, yes, use /bin/bash.

I always use the full path to any exe, script i use in cron as it may have a different $PATH variable than your user account. It's a good habit to get into.

$PATH is part of your environment. So is $DISPLAY. cron can have a different environment and that is why you needed to export DISPLAY as it did not have DISPLAY. It is also the reason why you should use full paths as it may not have your $PATH. It can have a different PATH.

Kind regards

---

### Post by histamineblkr on 2011-10-10
Oh you are talking about the path to my script because I had it:
[B]* * * * * ~/bin/scripts/bash/payday.sh
[/B]right?

I see what you mean now.

---

