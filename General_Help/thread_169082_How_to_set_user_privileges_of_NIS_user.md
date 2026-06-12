---
title: "How to set user privileges of NIS user?"
date: 2006-05-01
forum: General Help
---

### Post by BrianK on 2006-05-01
I found the place where you set who can use sound/graphics/admin tools, etc - User privileges under Users and Groups.  But NIS users don't show up in that list, so how can I set the privileges of NIS users?

---

### Post by BrianK on 2006-05-02
Solved.

If anyone else runs into this issue, all the priviledges are set in /etc/group.  Just add the user name to each of the things you want it to access.  You'll see the initial user you created - look at that as a hint where to put NIS users.  user names are separated by commas at the end of each line... for instance:

audio:x:29:init,briank,ivan,other_dude

and you're all set.

---

### Post by arizonagroovejet on 2006-06-06
[QUOTE=BrianK]Solved.

If anyone else runs into this issue, all the priviledges are set in /etc/group.  Just add the user name to each of the things you want it to access.  You'll see the initial user you created - look at that as a hint where to put NIS users.  user names are separated by commas at the end of each line... for instance:

audio:x:29:init,briank,ivan,other_dude

and you're all set.[/QUOTE]

In case you're still monitoring the thread and for anyone else who finds this there's what appears to be a better solution described at

[http://ubuntuforums.org/showthread.php?t=31542](http://ubuntuforums.org/showthread.php?t=31542)
[http://ubuntuforums.org/showthread.php?t=16035](http://ubuntuforums.org/showthread.php?t=16035)

I found those and this thread whilst looking for a solution to this problem.

Manually adding (and removing) the names of NIS users from /etc/group is going to get very tedious and messy if you have a lot of users.

---

### Post by BrianK on 2006-06-06
[QUOTE=arizonagroovejet]In case you're still monitoring the thread and for anyone else who finds this there's what appears to be a better solution described at

[http://ubuntuforums.org/showthread.php?t=31542](http://ubuntuforums.org/showthread.php?t=31542)
[http://ubuntuforums.org/showthread.php?t=16035](http://ubuntuforums.org/showthread.php?t=16035)

I found those and this thread whilst looking for a solution to this problem.

Manually adding (and removing) the names of NIS users from /etc/group is going to get very tedious and messy if you have a lot of users.[/QUOTE]
Those are much better solutions.  Thanks for posting.

---

