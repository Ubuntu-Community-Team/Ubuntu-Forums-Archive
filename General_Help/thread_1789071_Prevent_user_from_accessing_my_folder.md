---
title: "Prevent user from accessing my folder"
date: 2011-06-23
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-23
since apparently there is no way to get a guest session at login i made user called guest
then i deleted the guest folder and made a new folder 
[FONT=Courier New]/tmp/guestUser[/FONT] and symlinked [FONT=Courier New]/home/guest[/FONT] to it
then i [FONT=Courier New]chown guest:guest /tmp/guestUser[/FONT] now there is a permissions issue the guest user can view what is in my [FONT=Courier New]/home/me[/FONT] folder how can i stop that
since [FONT=Courier New]/tmp[/FONT] is cleared at reboot i edited [FONT=Courier New]/etc/gdm/Init/Default[/FONT] with these lines
```
mkdir /tmp/guestUser
chown guest:guest /tmp/guestUser
```

---

### Post by gdonwallace on 2011-06-23
When you create a new user, it becomes a member of the users group.  You can remove it from that group, or create a "guest" group and assign it to that one.  That should keep it from having access to your /home folder.

I would also recommend taking that folder out of /tmp.  By removing guest from the users group, you can put it in /home and you should not have any problems.

---

### Post by jerrrys on 2011-06-23
you have both set to log in automatically (no password required).  if you set your desktop to require password at login, then you will see the guest option at startup.

---

### Post by pqwoerituytrueiwoq on 2011-06-23
found solution other user cant see me stuff now
[FONT=Courier New]sudo chmod 0750 /home/$USER[/FONT]

---

