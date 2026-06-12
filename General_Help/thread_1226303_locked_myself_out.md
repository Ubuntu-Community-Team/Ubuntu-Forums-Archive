---
title: "locked myself out"
date: 2009-07-29
forum: General Help
---

### Post by uge on 2009-07-29
Hi guys,

I looked around in the forum and I couldn't find the answer I needed.

So I installed Ubuntu 8.04 LTS.

It bothered me that there was a group with my username.

So I issued those command
sudo usermod -g localusersgroup myusername
sudo usermod -G localusersgroup myusername
to change my primary group

then
sudo groupdel theGroupWithMyUsername

then rebooted to see what's up with that

well, getent group showed me that I got rid of the group, hurray !

but now I can't sudo no more :(
username is not in the sudoers file.  This incident will be reported.


and of course, issuing "su" with my password doesn't work either...
nor does sudo -i

any suggestion ??

---

### Post by Yannick Le Saint kyncani on 2009-07-29
> **uge said:**
> sudo usermod -G localusersgroup myusername

You've removed yourself from all groups. So you'll have to boot a livecd and edit /etc/group from there.

There are a bunch of groups you want to be part of.
Issueing "id" from the livecd should tell you most of them.
"man group" to know what this file contains.

---

### Post by michy99 on 2009-07-29
To have sudo priviledges you must be a member of the admin group. It looks like you removed yourself from every group except localusersgroup. To see what groups you belong to enter```
groups
```In my case I get```
mike adm dialout cdrom plugdev lpadmin admin sambashare
```You will have to boot into recovery mode and use the adduser command to add yourself to the admin group.

You need to be in other groups also, including the one with your name. You should use the addgroup command to restore it.

---

### Post by uge on 2009-08-05
> **michy99 said:**
> To have sudo priviledges you must be a member of the admin group. It looks like you removed yourself from every group except localusersgroup. To see what groups you belong to enter```
groups
```In my case I get```
mike adm dialout cdrom plugdev lpadmin admin sambashare
```You will have to boot into recovery mode and use the adduser command to add yourself to the admin group.

You need to be in other groups also, including the one with your name. You should use the addgroup command to restore it.


Thanks !

That's exactly what I did : boot in recovery mode and added myself to the groups I deleted by mistake

while at it, I added my user specifically in the sudoers

---

