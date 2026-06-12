---
title: "Crontab with SSH Keys?"
date: 2010-03-12
forum: General Help
---

### Post by NertSkull on 2010-03-12
So I was under the impression that when you make a crontab as a user, that it runs as that user.  But that must not quite be the case.

I have a script that runs rsync to backup some of my data remotely.  I log in to the remote machine with SSH-keys (no passwords allowed).

When I run the script from the terminal, it runs fine.  But when I run the script from cron nothing happens.

If cron runs as the user who owns the crontab(which I thought it did), why isn't it finding my ssh private key?

Anyway, doing some searching I found a few sites that suggest doing something like the following. 

```
rsync -av --delete -e "ssh -i /home/user/.ssh/id_rsa" mydir user@remotehost:/home/user/backupDir
```

So if I put that into my rsync file, And then run that file from my crontab, will it work?

I'm not at home so I can't test it right now.

But more importantly, is there any security issues with doing that?  I can't forsee one?

---

### Post by bodhi.zazen on 2010-03-12
By far and away the most common reason why cron (crontab) fails is that cron uses a minimal shell, so you need to use the full path to everything, commands and the location of ssh keys.

If the key has an empty password you should be fine. If the key requires a password you will need to pass the passphrase in some way (expect).

---

### Post by gmargo on 2010-03-12
> **NertSkull said:**
> If cron runs as the user who owns the crontab(which I thought it did), why isn't it finding my ssh private key?
Your authenticated _ssh_ key is held by a process named _ssh-agent_.  When _ssh-agent_ was started, it gave you some environment variables, which you can see from the command line with "env | grep SSH".  These environment variables tell _ssh_ how to contact _ssh-agent_.  When you run _ssh_ from _cron_, it does not have the SSH environment variables to tell it how to find _ssh-agent_.  And when you log off, _ssh-agent_ exits.  When you log back on, you get a new _ssh-agent_ and different environment variables.

The bottom line is that you cannot do what you want from cron, unless you could arrange for an always-on, always-authenticated _ssh-agent_.  But there's no way to do that without prompting the user for a passphrase.  What if you created a key with no passphrase?  I'm not sure if that would work but it's probably not a good idea.

---

### Post by NertSkull on 2010-03-12
So I'm home now and tried what I put above and I still have no success.

I didn't say before, but I do have my SSH keys set up with NO password.  I can ssh into the remote machine without typing any password, just using keys.

I don't know if this means anything, but I ran my rsync script from a terminal logged in as root (assuming thats what cron kind of does) and I got the following error.

```
Permission denied (publickey,keyboard-interactive).
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(600) [sender=3.0.6]
```So I changed my rsync to be really verbose when running (again as root) and this is the output I get

```
cmd=ssh machine=***DOMAIN*** user=**USER*** path=///cygdrive/h/Backup/Documents/weekly/
cmd[0]=ssh cmd[1]=-l cmd[2]=**USER*** cmd[3]=***DOMAIN*** cmd[4]=rsync cmd[5]=--server cmd[6]=-vvvvlogDtpre.iLs cmd[7]=--log-format=%i cmd[8]=--delete-after cmd[9]=. cmd[10]=///cygdrive/h/Backup/Dan/Documents/weekly/ 
opening connection using: ssh -l **USER*** ***DOMAIN*** rsync --server -vvvvlogDtpre.iLs "--log-format=%i" --delete-after . ///cygdrive/h/Backup/Documents/weekly/ 
note: iconv_open("UTF-8", "UTF-8") succeeded.
_exit_cleanup(code=12, file=io.c, line=600): entered
_exit_cleanup(code=12, file=io.c, line=600): about to call exit(255)
```I don't really understand environment variables as well as I probably should.  But I did the "env | grep SSH" as suggested and got these variables

```
SSH_AGENT_PID=2921
SSH_AUTH_SOCK=/tmp/keyring-uVu2Tn/socket.ssh
```So I was wondering.  What if I define the SSH_AUTH_SOCK in my script, and that didn't do anything (I assumed I couldn't really define the SSH_AGENT_PID since that probably changes)

Any thoughts on what to do next?  I'm sure I just don't fully understand cron.  But the script works just GREAT when I run from a terminal as myself as user.

---

### Post by baddnady23 on 2010-03-12
Refer to this thread as it may be of some help:

[http://ubuntuforums.org/showthread.php?t=238672]("http://ubuntuforums.org/showthread.php?t=238672")

---

### Post by NertSkull on 2010-03-12
SUCCESS.

It appears I had forgotten to get the full path to SSH as well.  You need to have full paths to SSH, rsync, and the key file location.

So if you get full paths to all parts it works well.

Thanks all.

---

