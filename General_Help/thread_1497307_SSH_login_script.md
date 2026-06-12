---
title: "SSH login script"
date: 2010-05-30
forum: General Help
---

### Post by hopugop on 2010-05-30
I'd like to automatize a task which needs to be done every time an user logs on my system through SSH.

I think there's a way to run a script EVERY TIME someone logs on through SSH and SSH-only, but I was not able to figure it out by myself or with Google/Forum help. :confused:

I tried to add the command at the cron jobs that creates the MOTD for the logon process but the command is processes only by the system and not the SSH user itself.

One of the commands I'd like to run for every SSH user is the famous "export DISPLAY=:0.0" which permits Windows Putty users to start tasks and manipulate it through VNC.

---

### Post by geirha on 2010-05-30
When you log in with ssh, some SSH_* variables will be set, so you can do something like this in .profile

```

if [ -n "$SSH_CLIENT" ]; then
  echo "ssh specific stuff"
fi

```

---

### Post by hopugop on 2010-05-30
Works like a charm, thanks a **lot**! I'll rename this post to Solved!

---

