---
title: "Pidgin issue.  I load pidgin, and my yahoo account is not working."
date: 2009-07-01
forum: General Help
---

### Post by Mashuteichou on 2009-07-01
This is different from others I believe.  I tried changing the page server to an IP number as one solved post said to do, but that made it not work at all.  When I hit reconnect, it just loads for a second and it pops back up.  So I switched the page server back.

When I click pidgin to load, it pops up and says "connecting" at the bottom.  Then, its like it connected.  It says available, and it shows connected in the task bar.  But nothing shows up, no friends, no messages, nothing.  I can't add or delete anything, I can start a new conversation, just like it wasn't connected.  It just shows a blank screen on the pidgin window.

I have deleted and reinstalled.  I did a full delete in package manager, and deleted the .purple folder and everything I could find and delete that had to do with pidgin.  Reinstalled again, same problem.  

So how do I fix this?  Its like its working, but its not.  When I open it in terminal, nothing show up.  Pidgin just pops up in the task bar and does the same thing.  No errors or anything.  

Any suggestions would be appreciated.  I'm at a stand still again.  ^_^  Thanks

---

### Post by jerome1232 on 2009-07-01
Update to the latest version using their ppa, it will fix the yahoo issue.

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by colau on 2009-07-01
> **Mashuteichou said:**
> This is different from others I believe.  I tried changing the page server to an IP number as one solved post said to do, but that made it not work at all.  When I hit reconnect, it just loads for a second and it pops back up.  So I switched the page server back.

When I click pidgin to load, it pops up and says "connecting" at the bottom.  Then, its like it connected.  It says available, and it shows connected in the task bar.  But nothing shows up, no friends, no messages, nothing.  I can't add or delete anything, I can start a new conversation, just like it wasn't connected.  It just shows a blank screen on the pidgin window.

I have deleted and reinstalled.  I did a full delete in package manager, and deleted the .purple folder and everything I could find and delete that had to do with pidgin.  Reinstalled again, same problem.  

So how do I fix this?  Its like its working, but its not.  When I open it in terminal, nothing show up.  Pidgin just pops up in the task bar and does the same thing.  No errors or anything.  

Any suggestions would be appreciated.  I'm at a stand still again.  ^_^  Thanks
From pidgin>Manage Accounts>Modify>Advanced
assign page server
```

scsa.msg.yahoo.com

```

---

### Post by abhi_69 on 2009-07-01
ya, upgrade to latest version of pidgin (2.5.7 or later) from ppa. it must solve your problem. i had the same issue with version 2.5.6....now it solved by using version 2.5.7 from ppa.
change pager server to scsa.msg.yahoo.com will work also.
try it & enjoy chat with pidgin......

---

