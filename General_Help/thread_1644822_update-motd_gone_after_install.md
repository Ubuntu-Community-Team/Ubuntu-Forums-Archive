---
title: "update-motd gone after install"
date: 2010-12-13
forum: General Help
---

### Post by booeyOH on 2010-12-13
I am not sure what happened here. I have 10.04.1 and was able to run a command "update-motd". I wasn't able to get it to dynamically create a new motd. My hope was to have it recreate it once a day and email me the MOTD from the server. 
 
In trying to get it to do this, I did a "apt-get install update-motd" in which it proceeded to do this, but then after the installation, I get:
 
"update-motd: command not found".
 
What did I do, how can I manually update/create the /var/run/motd file?
 
Thanks,
Bryan

---

### Post by abriening on 2011-03-18
Just had a similar issue on a server upgraded to 10.04.2.

The motd would fail to show anything other than the "Last login" message. Seems that they've changed update-motd a bit the last few releases. It now uses PAM and should rebuild on each login. Some parts of the motd are cached, though.

So here are the steps I used to correct it:

Update sshd config:
```

# /etc/ssh/sshd_config
# update to UsePAM
UsePAM yes
# disable motd or it will show twice
PrintMotd no

```

Force rebuilding the cached apt available updates, this was empty and not updating for some reason:
```
sudo /usr/lib/update-notifier/update-motd-updates-available --force
```

Install the landscape-common package, this shows the system info and was missing:
```
sudo apt-get install landscape-common
```

Remove any old motd:
```
sudo rm -f /etc/motd
```

Link the generated motd to /etc:
```
sudo ln -s /var/run/motd /etc/motd
```

You can test it with:
```
run-parts /etc/update-motd.d/
```

Or just logout then login.

---

### Post by abriening on 2011-03-18
Just re-read the orignal post. Once that is working you could use the "run-parts /etc/update-motd.d/" to send an email with cron? maybe?

---

