---
title: "shared home directories"
date: 2006-04-06
forum: General Help
---

### Post by drberg1000 on 2006-04-06
Is there a howto for networking /home?  I expected there to be but haven't been able to find one.

Here's my setup which I'm sure is quite common.  I have a desktop which doubles as my server.  I also have a laptop which is almost always used on the home network over wireless but occasionally hooks up to other networks when traveling.  I may add a few more computer in the future.

Here is what I would like to set up.  /home is mounted from the desktop when ever that system is available.  If the desktop system is unavailable, then the client uses a backup it made the last time it connected.  When the desktop becomes available again the directories are synched.  

My best guess at how to do this is to export /home with NFS securely perhaps tunneled through ssh.  Rsync or similar program is used to keep the local copy and the remote copy in sync.  I don't know enough about any of these tools to start setting this up propperly.  

If no one knows of a howto, perhaps someone could help me out with how to secure NFS, then I can work out rsync and write up the process.

--Dave

---

### Post by wylfing on 2006-04-06
The [FONT="Courier New"]mount[/FONT] command will return 0 on success, and some positive integer on failure, so it's fairly easy to test whether it is possible to mount the server's shared directories. So use crontab to set up a job whereby mounting is tried at boot time and periodically thereafter, and if mount is successful, then run an rsync job.

Come to think of it, it might be possible to hook this into DHCP somehow...that'd probably be optimal.

---

### Post by drberg1000 on 2006-04-06
[QUOTE=wylfing]Come to think of it, it might be possible to hook this into DHCP somehow...that'd probably be optimal.[/QUOTE]

That's a good idea.  My first stumbling block is still exporting the directories securely.  Surely there is a secure way to mount a filesystem over the network.

--Dave

---

