---
title: "USB devices always automount for second user"
date: 2010-01-27
forum: General Help
---

### Post by froff on 2010-01-27
hello
Since I created second user USB devices as PTP camera, flash mass storage automounts always for the new user.
Even the second user is not logged in automount does not work for main user. When I log in as second user (with device plugged in) it is mounted automatically after log in.

What can I do with this problem?
I would like to access devices from each user (not necessarily at the same time).
How can I configure it?
How can I "remount" device to my current user without switching into the second one (it's someones else account)?

reards

---

### Post by shreepads on 2010-01-27
> **froff said:**
> hello
Since I created second user USB devices as PTP camera, flash mass storage automounts always for the new user.
Even the second user is not logged in automount does not work for main user. When I log in as second user (with device plugged in) it is mounted automatically after log in.

What can I do with this problem?
I would like to access devices from each user (not necessarily at the same time).
How can I configure it?
How can I "remount" device to my current user without switching into the second one (it's someones else account)?

reards

Silly question, are both members of the 'plugdev' user group??

---

### Post by froff on 2010-01-27
> **shreepads said:**
> Silly question, are both members of the 'plugdev' user group??

Incredibly the second one is not!
But devices automount to the second.

I realized that sometimes scenario changes. Sometimes devices mount for the first user even the second is logged in. I can't find the rule.

How to "remount" device manually to other user?

---

### Post by shreepads on 2010-01-28
> **froff said:**
> Incredibly the second one is not!
But devices automount to the second.

I realized that sometimes scenario changes. Sometimes devices mount for the first user even the second is logged in. I can't find the rule.

How to "remount" device manually to other user?

Sorry can't help with that! 

Could you do a comparo between the user groups for both users, sync up any differences and try? Or are there reasons why these users should belong to different user groups?

---

### Post by froff on 2010-01-28
> **shreepads said:**
> Sorry can't help with that! 

Could you do a comparo between the user groups for both users, sync up any differences and try? Or are there reasons why these users should belong to different user groups?

Ok, I'll check all groups at evening.

But what is the normal, proper behavior?
Supposing both are logged in - should they both have device automounted with r/w permissions?

---

### Post by shreepads on 2010-01-29
> **froff said:**
> Ok, I'll check all groups at evening.

But what is the normal, proper behavior?
Supposing both are logged in - should they both have device automounted with r/w permissions?

My friend, you are taking me beyond my areas of competence! 

What I have noticed is that if I plug in a USB stick as one user 'a' log off and then login as the second user 'b' I can access the USB stick but cannot unmount as it says the drive was mounted by user 'a'.

Lemme experiment tonight and tell you what I find!

---

### Post by no2498 on 2010-01-29
? have you unplugged it and restarted the computer
an plugged it back in as user 1
you may need to reset auto mount
just asking

---

### Post by froff on 2010-01-30
> **shreepads said:**
> My friend, you are taking me beyond my areas of competence! 

What I have noticed is that if I plug in a USB stick as one user 'a' log off and then login as the second user 'b' I can access the USB stick but cannot unmount as it says the drive was mounted by user 'a'.

Lemme experiment tonight and tell you what I find!

hi
But what happens when  You don't log off, but switch to other user instead?

My users belongs to groups:

1st: admins adm dialout fax cdrom tape audio dip video plugdev scanner fuse lpadmin netdev admin sambashare

2nd: users cdrom audio video scanner fuse netdev

The second one does not belong to plugdev group but automount works for him!

regards

---

