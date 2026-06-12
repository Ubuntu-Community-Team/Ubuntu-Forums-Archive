---
title: "fsck &amp; subsequent problems that now detects my home folder as a text file"
date: 2010-04-11
forum: General Help
---

### Post by amachu.techie on 2010-04-11
When it happened to reboot my Ubuntu NBR yesterday, the /home partition
(/dev/sda6) had fsck issues. Then I issued "fsck -y" command to rectify it.

But When I rebooted again, I found my home directory 'amachu' under /home
to be a text file owned by root.

I changed the ownership to amachu:amachu & gave read and execute
permissions to group & others.

But there is no directory attribute listed when I issue a "ls -lh" command
on /home

I have another user 'ramadas', I do not have any problem of logging into
the system as that user.

When I try to login as amachu, ICEauthority file error popup, but when my
home folder itself is shown as a text file, how do I get into it to check?

Any help would be appreciated.

---

