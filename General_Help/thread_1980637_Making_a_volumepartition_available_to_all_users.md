---
title: "Making a volume/partition available to all users"
date: 2012-05-15
forum: General Help
---

### Post by QwUo173Hy on 2012-05-15
I have an ext4 partition but because I ticked "take ownership of device" when formatting, nobody else can mount it without entering a password.

I'm currently backing up the contents to format the disk again, so I would like to know how I can have it so that the Movies user can have this drive already mounted (so xbmc can run at startup). Is it possible to do this or even better make the drive available to three specific users of my system?

Many thanks,
Jarlath

---

### Post by jerome1232 on 2012-05-15
No need to reformat.

Firstly you need to make an fstab entry for it

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)


Secondly I imagine you would need to create a new group, add the three users to the group, and then recursively modify permissions on the drive to your liking.

Here's a simple write up to help you understand permissions better, and to give you an idea of what you are doing.

[http://wiki.debian.org/Permissions#Case_1:_Family_photos](http://wiki.debian.org/Permissions#Case_1:_Family_photos)

---

### Post by QwUo173Hy on 2012-05-15
Thanks Jerome 1232, that worked! For fstab I used the options: auto, user, ro (to prevent accidents).

I had tried before putting defaults at the start and then 'user' afterwards, thinking that it would have precedence from right to left but it didn't work. Do you know anything about that?

Luckily I didn't have to create any groups, I think that's because of the 'user' option in fstab but I don't know.

Anyway, thanks very much. We now have a Movies account with no password that launches XBMC on startup so we have a happy home indeed.

Kind regards,
Jarlath

---

