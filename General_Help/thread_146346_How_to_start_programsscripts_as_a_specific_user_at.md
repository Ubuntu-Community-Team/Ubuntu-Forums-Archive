---
title: "How to start programs/scripts as a specific user at startup, without logging in?"
date: 2006-03-18
forum: General Help
---

### Post by Grimmy on 2006-03-18
I usually run my irc client (irssi) from a screen, so I can access it from SSH anywhere...   What i'd like to do is get this to automatically start everytime the computer boots.

i.e.  Automatically run the command "screen irssi" as my user, without having to log in.  (I know how to make it run automatically on log-in to gnome).

---

### Post by Xian on 2006-03-18
Set up a cron job under your user name.

1. Issue the command below to add a new cron job:
```
$ crontab -e
```

2. Input the desired command to be run at boot:
```
@reboot /usr/bin/screen irssi
```

I'm guessing at the proper command '/usr/bin/screen'.
You may need to alter that if necessary.

3. To view your current cron jobs:
```
$ crontab -l
```

---

### Post by Treebeard on 2006-03-18
You can also create a shell script in /etc/init.d, lets say you call it [I]foo.
[/I]And then create an init script link. This will make it start once when you boot and stop the process when you shutdown.```
Create and edit the script in your favourite editor e.g. *vim *:
$ sudo vim /etc/init.d/foo 

After editing make the script executable :
$ sudo chmod +x /etc/init.d/foo

Now add it to the startup process, debian style :
$ sudo update-rc.d foo defaults

The script will start in runlevel 2 3 4 and 5, and stop in runlevel 0 1 6.
See **man update-rc.d** for more information.

```

---

### Post by Xian on 2006-03-18
[QUOTE=Treebeard]You can also create a shell script in /etc/init.d, lets say you call it ...[/quote]

That method will work, but only for users that have sudo privileges.

---

