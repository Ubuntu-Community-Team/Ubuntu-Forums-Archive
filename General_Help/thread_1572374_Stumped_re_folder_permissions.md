---
title: "Stumped re folder permissions"
date: 2010-09-11
forum: General Help
---

### Post by mowglinz on 2010-09-11
System->About Ubuntu reports
> You are using Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 and supported until April 2013.I have a regular user rob who I'd like to make a member of the webdevel group
```
rob@rob-desktop:~$ groups
rob adm dialout cdrom plugdev lpadmin admin sambashare
rob@rob-desktop:~$ sudo usermod -a -G webdevel rob
rob@rob-desktop:~$ groups
rob adm dialout cdrom plugdev lpadmin admin sambashare
rob@rob-desktop:~$ sudo groups rob
rob : rob adm dialout cdrom plugdev lpadmin admin sambashare webdevel
rob@rob-desktop:~$ sudo su rob
rob@rob-desktop:~$ groups
rob adm dialout cdrom plugdev lpadmin admin sambashare webdevel
rob@rob-desktop:~$ 
```Rob starts out without webdevel membership. 
Root (via sudo) adds webdevel to rob's groups
Rob checks his group memberships but alas no webdevel
So root (via sudo) checks  with 'sudo groups rob' - it's there!!
Root switches to user rob and checks rob's groups - and here!!
Sadly plain rob isn't a member of webdevel - but not here :(

/etc/groups reflects that rob is a member of the group webdevel. I've tried killing all terminals. It's not listed in the known issues for Lucid. The exact same sequence on a Lucid Server over ssh worked as expected. Google has failed me. I'm stumped.

---

### Post by dcstar on 2010-09-11
> **mowglinz said:**
> System->About Ubuntu reports
I have a regular user rob who I'd like to make a member of the webdevel group
```
rob@rob-desktop:~$ groups
rob adm dialout cdrom plugdev lpadmin admin sambashare
rob@rob-desktop:~$ sudo usermod -a -G webdevel rob
rob@rob-desktop:~$ groups
rob adm dialout cdrom plugdev lpadmin admin sambashare
rob@rob-desktop:~$ sudo groups rob
rob : rob adm dialout cdrom plugdev lpadmin admin sambashare webdevel
rob@rob-desktop:~$ sudo su rob
rob@rob-desktop:~$ groups
rob adm dialout cdrom plugdev lpadmin admin sambashare webdevel
rob@rob-desktop:~$ 
```Rob starts out without webdevel membership. 
Root (via sudo) adds webdevel to rob's groups
Rob checks his group memberships but alas no webdevel
So root (via sudo) checks  with 'sudo groups rob' - it's there!!
Root switches to user rob and checks rob's groups - and here!!
Sadly plain rob isn't a member of webdevel - but not here :(

/etc/groups reflects that rob is a member of the group webdevel. I've tried killing all terminals. It's not listed in the known issues for Lucid. The exact same sequence on a Lucid Server over ssh worked as expected. Google has failed me. I'm stumped.

And if you logged out of the current session and logged back in again the new group would be there.

---

### Post by mowglinz on 2010-09-11
> **dcstar said:**
> And if you logged out of the current session and logged back in again the new group would be there.

Thanks, and that's exactly what fixed it. It kinda grates me though. Almost like that other OS and its love affair with rebooting.

There must be a way of refreshing group permissions in a running session....

---

