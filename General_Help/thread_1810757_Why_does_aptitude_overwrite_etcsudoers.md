---
title: "Why does aptitude overwrite /etc/sudoers ?"
date: 2011-07-23
forum: General Help
---

### Post by pclausen on 2011-07-23
Hi

I've been trying for a long while to figure out why aptitude overwrites /etc/sudoers ? Each time I run 

[FONT=Courier New]$ sudo aptitude safe-upgrade

[FONT=Arial]my /etc/sudoers is reset. This is really annoying because I have it setup so that mythtv can shutdown and restart automatically. The line in /etc/sudoers that gets deleted is:

 [/FONT]%mythtv ALL = NOPASSWD: /usr/bin/mythshutdown, /bin/sh, /usr/bin/setwakeup.sh, /
sbin/reboot, /sbin/shutdown

[FONT=Arial]When the line is missing my Ubuntu 10.04 does not shut down at all because of missing rights to do so. Does anyone have a clue why this is happening? I thought /etc-files were sacred for others than root, but it seems I'm wrong. Of course I have edited sudoers with visudo.

If I'm posting in wrong forum, please correct me - I usually find help in old treads except for this issue.

/Peter
[/FONT]
[/FONT]

---

### Post by bapoumba on 2011-07-23
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/761689](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/761689)
This is the closest thing I could find related to this very curious problem ;)

Which ubuntu version are you using ?

Currently on Natty I have the correct sudo package:
```
Architecture: i386
Version: 1.7.4p4-5ubuntu7.1
```

---

### Post by pclausen on 2011-07-26
> **bapoumba said:**
> 
Which ubuntu version are you using ?


I'm using up2date lucid 10.04 64-bit:
Linux pmc-server1 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux

and:
Sudo version 1.7.2p1

---

### Post by pclausen on 2011-07-28
It happened again... With sudo aptitude safe-upgrade I got following packages:

  dbus dbus-x11 libdbus-1-3 libpng12-0 libsndfile1 

and a new /etc/sudoers ...  :-(

Must not somewhere be a logging entry that sudoers has changed ? I cant find it (except for my own entry from now, once again changing it back manually).

---

### Post by mc4man on 2011-07-28
I don't use aptitude so no comment there
On natty i do make one entry but instead of using /etc/sudoers I use /etc/sudoers.d/<a file I create>

**If** you can use this in lucid it would likely be protected from whatever aptitude is doing

As Ex. I create a file like this and then add my entry in the same way as in sudoers

```
sudo visudo -f /etc/sudoers.d/01_file
```

From the readme in /etc/sudoers.d/
> #
# As of Debian version 1.7.2p1-1, the default /etc/sudoers file created on
# installation of the package now includes the directive:
# 
# 	#includedir /etc/sudoers.d
# 
# This will cause sudo to read and parse any files in the /etc/sudoers.d 
# directory that do not end in '~' or contain a '.' character.
# 
# Note that there must be at least one file in the sudoers.d directory (this
# one will do), and all files in this directory should be mode 0440.
# 
# Note also, that because the sudoers file is not a 'conffile' in the Debian 
# sense, and sudoers contents can vary widely, no attempt is made to add this 
# directive to existing sudoers files on upgrade.  Feel free to add the above 
# directive to the end of your /etc/sudoers file to enable this functionality 
# for existing installations if you wish!
#



Edit: as an aside on natty and 11.10 I use sudo 1.7.2p7 because it allows the timeout timestamp on all instances which I prefer and using sudoers.d works fine..

---

### Post by pclausen on 2011-08-06
> **mc4man said:**
> I don't use aptitude so no comment there
On natty i do make one entry but instead of using /etc/sudoers I use /etc/sudoers.d/<a file I create>


tnx mc4man; that "solved" it, that is that /etc/sudoers is still overwritten, but adding my extra lines in a file  /etc/sudoers.d/myth did work. 

**CAUTION**: I had some trouble because files in /etc/sudoers.d/. **must** have file permissions 0440 before next sudo-command. Solution: Start a root-shell (sudo bash) do your changes and test sudo in another terminal - then you do not have to reboot a couple of times like I had to....  :-/

Setting this thread to [Solved]

---

