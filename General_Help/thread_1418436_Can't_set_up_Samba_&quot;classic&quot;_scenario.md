---
title: "Can't set up Samba &quot;classic&quot; scenario"
date: 2010-02-28
forum: General Help
---

### Post by Shinkan on 2010-02-28
Hi there,

I've got a small Ubuntu 9.10 server on my LAN to backup files and share folders with Windows users.

I want to set up a basic Samba server scenario, but I'm not succeeding. I've tried s many combinations, with so many different results, that I don't understand anything now.

What I've got :
[LIST]
[*]Ubuntu 9.10 with Samba 3.4 on group WORKGROUP
[*]1 Windows Vista client, user User1, pass Pass1
[*]1 Windows 7 client, user User2, pass Pass2
[/LIST]

Users are local to Windows devices.

Shares I want :
[LIST]
[*]/share_one so that User1 and User2 can read/write being logged, and anybody (not logged, anonymous) can read
[*]/share_two so that User1 can read/write and User2 can read being logged, and no anonymous access
[*]/share_three so that User1 can read/write, and no other access
[/LIST]

I don't now how to set up that.
I tried with creating 2 Unix users with same name that User1 and User2, and same passwords than Windows one, because I though that having same Unix/Samba login/pass than Windows will make Windows users to access share without entering password, but I'm not sure this is supposed to work ?

Many thanks in advance.

---

