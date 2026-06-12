---
title: "Help! Persistant content of /tmp folder returns after deleting or rebooting"
date: 2010-04-06
forum: General Help
---

### Post by 4ll41 on 2010-04-06
Hi all,

After checking my tmp folder I found out some strange hidden and unhidden folders of programs that I have not used or downloaded. After removing each one using *sudo rm -rf *some folders insist on re-appearing, and after a reboot all folders are back.

Moreover, trying *netstat -l*, found that many of these files are in listening state.


How can I permanently erase them? Should I worry? :confused: A lot?

---

### Post by gmargo on 2010-04-06
It would be a lot easier to tell if you provided a directory listing. :P

A lot of programs put sockets and temp files in /tmp.  Nothing to worry about.  On my old Hardy system here it looks like I've got about 10 listening sockets under /tmp.

---

### Post by 4ll41 on 2010-04-07
Thank you for the quick response gmargo.

The directories in /tmp are the following:

```
.esd-1000
.esd-112
.winbindd
hsperfdata_[user]
kde-root
kde-[user]
keyring-x0nvEe
ksocket-[root]
ksocket-[user]
libgksu-bSyxt6
orbit-gdm
orbit-root
orbit-[user]
        >> bonobo.activation.server files
plugtmp
pulse-fxad1djoujax
pulse-pkdhtxmmr18n
ssh-aedeva3620         (????)
virtual-[user].3aftfn
virtual-[user].fcbdda
```

The thing that bothers me is that I can not explain the existence of some folders there as I have not used any of the relative programs... I have clamscaned them all and seem ok. But still I am a bit worried. Is it just me?

Any advice?

---

### Post by sandyd on 2010-04-07
> **4ll41 said:**
> Thank you for the quick response gmargo.

The directories in /tmp are the following:

```
.esd-1000
.esd-112
.winbindd
hsperfdata_[user]
kde-root
kde-[user]
keyring-x0nvEe
ksocket-[root]
ksocket-[user]
libgksu-bSyxt6
orbit-gdm
orbit-root
orbit-[user]
        >> bonobo.activation.server files
plugtmp
pulse-fxad1djoujax
pulse-pkdhtxmmr18n
ssh-aedeva3620         (????)
virtual-[user].3aftfn
virtual-[user].fcbdda
```

The thing that bothers me is that I can not explain the existence of some folders there as I have not used any of the relative programs... I have clamscaned them all and seem ok. But still I am a bit worried. Is it just me?

Any advice?

youve used all of them likely... the first three are the esound daemon, second is winbind daemon, used for binding windows addresses on a network. those programs run in the background as daemons (sort of like windows services) and provide stiff for your computer...and yes. the stuff in there looks normal. but im too lazy to translate each of the directories to an application.

---

