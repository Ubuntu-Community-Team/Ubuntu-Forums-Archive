---
title: "Linux not seeing windows 7."
date: 2010-01-10
forum: General Help
---

### Post by benjaminatx on 2010-01-10
Windows 7 machine sees my kunbuntu 9.10 box but the linux box doesn't see the windows 7 machine. I am happy to admit I am very noob and hopefully this is something simple. I searched the forums and didn't see anything. My vista laptop sees the linux box.

TIA,
Ben

---

### Post by sigixv on 2010-01-10
i used to have problems accessing win7 machines but usually i could see them. Have you enabled samba and rebooted the linux machine?

---

### Post by benjaminatx on 2010-01-10
Samba share is enabled and it can view my vista machine fine. This is more likely a settings in windows 7.

---

### Post by sigixv on 2010-01-10
with xp machines ive seen similar things, perhaps try searching on the issue win7 not seeing xp in networks on win forums. They'll be more familiar with figuring out wich settings to tamper with in win7

good luck

---

### Post by benjaminatx on 2010-01-10
Yeah, the windows 7 machine is also visible to my vista laptop.

---

### Post by sigixv on 2010-01-10
[http://www.howtogeek.com/howto/windows-7/share-files-and-printers-between-windows-7-and-xp/](http://www.howtogeek.com/howto/windows-7/share-files-and-printers-between-windows-7-and-xp/)
[http://www.sevenforums.com/network-sharing/5369-networking-file-share-between-windows-7-windows-xp.html](http://www.sevenforums.com/network-sharing/5369-networking-file-share-between-windows-7-windows-xp.html)

vista is still updated, ms is somewhat neglecting xp and letting it die out slowly. Try fixes mentioned in above links...

*EDIT: i mean here, try the settings for win7 box which are needed to make an xp able to connect to a win7 machine. If an xp box with standard settings should be able to connect, samba should be also

---

### Post by sigixv on 2010-01-10
also, make sure you have the correct share-group on all computers (WORKGROUP, HOME, ...)
that also might be a thing...

---

### Post by benjaminatx on 2010-01-10
Work group is matched up and I have visibility on the other machines.

I ran through sigixv's suggestions with no luck 

Windows 7 machine sees the vista and kunbuntu boxes

Vista laptop sees the kunbuntu and windows 7 machine.

kunbuntu box only sees the vista machine.

---

### Post by HuaiDan on 2010-01-10
If you're trying to see the computers on the network by name, sounds like it could be a WINS problem. If you try to connect by IP and it still doesn't work, then depending on who you ask, you either lower win7 security by editing the security policy for network authentication to lower than NTML2, or you allow samba to authenticate with NTML2. I'm not sure how to pull off that last one.


Edit: here's how. Put this in your /etc/samba/smb.conf

[global]

encrypt passwords = yes
lanman auth = No
ntlm auth = No
client ntlmv2 auth = Yes
client ntlm auth = No
client lanman auth = No
client plaintext auth = No



And make sure these parameters don't appear elsewhere in smb.conf.

---

