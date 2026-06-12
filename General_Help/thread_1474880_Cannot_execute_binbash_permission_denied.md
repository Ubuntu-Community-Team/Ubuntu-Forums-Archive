---
title: "Cannot execute /bin/bash: permission denied"
date: 2010-05-06
forum: General Help
---

### Post by TristanSt on 2010-05-06
I've been running Lucid Lynx since the beginning of April and all has been going smoothly.

Yesterday morning I was happily working away when my command window (that I wasn't working in - I was browsing the web) disappeared and wouldn't re-open. Upon reboot X failed to start, so going in at the command-line, trying to log in as myself and got "Cannot execute /bin/bash: permission denied".

Rebooted into recovery mode and got a root terminal up, tried to su to my normal user, same message. Obviously I checked the permissions on /bin/bash which are -rwxr-xr-x root:root. I've also checked all of the permissions in /lib, /usr/lib, /usr/bin, /usr/sbin looking for any permissions lacking execute on all. None.

Nothing in auditlog, syslog, authlog.

In desperation I added my user to the root group (yes I know - not wise in normal circumstances) and this allowed me to su to myself, however, bizarely it wouldn't let me use sudo complaining about setuid root.

At my wit's end here - any ideas? I'm loathe to do a reinstall because I've spent the last month reinstalling apps and packages and only just got anywhere near where I was before I put Lucid on.

---

### Post by jbrown96 on 2010-05-06
Grabbing at straws here, but maybe your disk is full. Try getting back into recovery mode and run ```
df -h
```

The more I think about no disk space makes sense. By default, Ubuntu reserves 5% of the space for root for emergencies like this. I'm not totally sure if df will report 5% free if its the emergency 5%, especially since root will run the command. That's why root and your root-ified user were able to load bash, because the 5% emergency space was available to write .bash_history and maybe some other bash files.

---

### Post by TristanSt on 2010-05-06
Whilst it would be tempting to delete my account and never return to these fora in shame, I should come clean...

Turns out /bin was 660 for some strange reason :mad:

Still got some residual problems - sudo still moaning about setuid root, and Gnome panel isn't showing network manager and is showing the speak symbol as <-- (where < is a speaker) - i.e. no sound device detected. Need to get to the bottom of that one, but have only given it approx 20 seconds thought so far.

---

### Post by maatthc on 2010-07-20
The same happened to me yesterday after installing some updates..
I'm running the Ubuntu 10.04 LTS..

---

### Post by mapinho on 2010-09-17
I face the same problem: after an upgrade, some services do not start because permission problems, the cause is the permissions of /bin was changed to 750. Solution is easy: chmod 755 /bin and everything goes fine.

Regards.

---

### Post by falconmfm on 2010-11-03
Hi , I have the same problem... but the updated package change the owner group from adm to root , also if you see the /etc/group file you can see that your user is at the end of the line 

   > adm: x :4:<your_user_name>

Ok , my solution was add at the first line 

   > root: x :1:<my_user_name>,<and_others>

---

