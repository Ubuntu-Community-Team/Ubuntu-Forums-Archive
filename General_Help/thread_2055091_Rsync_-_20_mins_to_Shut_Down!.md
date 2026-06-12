---
title: "Rsync - 20 mins to Shut Down!"
date: 2012-09-08
forum: General Help
---

### Post by Quarkrad on 2012-09-08
Newbie running 12.04.   For some years I have been auto running a scirpt that backs up a number of folders to a local backup disc.  I obtained the script/help from a post on this forum.  Everything has been OK - I have never timed it but generally the PC shuts down within a few minutes as rsync does the backup.  However, something has happened and the now the pc takes about 20 minutes (!!!!!!) to shut down.  I have checked the two disc in my pc and they report to be find.  Is there a log or something somewhere where I can see what is going on why it takes so long to shut down.  Reminds me of my old Windoze days!  Thanks for any help.

---

### Post by dargaud on 2012-09-08
How do you know it is that script that causes the delay in the shutdown ?

---

### Post by Quarkrad on 2012-09-08
I don't - it could be anything.  I will delete the rsync set up and set it up again - that will eliminate rsync from the cause.

---

### Post by dargaud on 2012-09-09
Normally running scripts don't block or delay shutdowns because they don't reply to system events. Only programs written specifically for your window manager (Gnome/KDE/whatever) can do that.

---

### Post by malleeblue on 2012-09-09
Hi. I'm going to chime in here, but I'm not sure it'll be particularly useful.

I too am experiencing shutdown problems, and they've only started since I started to run rsyncs. Occasionally I'll have an rsync in my Processes list that's uninterruptible. Then, when I try to shutdown the PC just hangs. Ctrl+Alt+Del doesn't even restart it, I have to use the power button (trying to 'kill' that uninterruptible process prior to shutdown doesn't work either).

As with the OP, I can't guarantee that rsync is to blame, but this problem only happened since I started using rsync.

So maybe not so useful info, but thought it might be a good idea to add a voice to the thread in case it helps support the theory.

---

### Post by Quarkrad on 2012-09-10
I took the rsync out of etc/init.d and also (probably over the top) deleted the scrpit from Gadmin/scripts.  The pc shut down normally so for some reason something has happened to rsync.  The two foldeder I backup is my ubuntu Home folder and quite a large user data folder that is located on a separate partition. I will experiement with rsync to see what is causing this delay in shutdown.  It does eventually shutdown - although last time after 3 hours it still had not shut down so I had to manually switch off.  I suspect it was not backing up but hanging.

---

