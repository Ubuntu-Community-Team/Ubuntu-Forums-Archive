---
title: "Inhibit Shutdown during Remote Session"
date: 2012-04-03
forum: General Help
---

### Post by seanlano on 2012-04-03
Sorry for the cryptic heading, I couldn't really think of a better way to describe what I'm trying to do.

I will soon be replacing my family's main desktop PC (with another desktop), and want to make the now-obsolete desktop a secondary computer for people to use if the new one is in use. 
I want to make it so that all of the files on the secondary PC are exactly the same as on the primary one, so that users see no difference between computers. So, I need to do the following:
[LIST]
Copy/Remotely access the files (using NFS, or rsync at login and logout)
[/LIST]
[LIST]Prevent the primary PC from shutting down while the secondary PC is on[/LIST]

I think I would prefer to rsync the files locally, so that performance is not dependant on the network (as it would be with NFS). But this should be straightforward enough (although any tips would be appreciated). 

The problem is this: Users will use the primary PC first, so it will always be on when the secondary PC boots. But I don't know how to inhibit shutdown on the primary PC while the secondary one is active. This is critical to the general idea I have. It would be safe to assume that users will only use the gnome panel shutdown button (not any CLI shutdown command). 
I know that if another users is logged in, Ubuntu will inhibit shutdown unless you enter an administrator password. This would be the ideal solution. How can I trigger this warning, without necessarily having a user logged in? And then clear it when the secondary PC is shutdown?

Also, as an added bonus, would it be possible to prevent a user logging into their account on the primary PC while they are logged into the secondary PC? And to prevent logging on the the secondary PC if the account is in use on the primary PC? This would help prevent file change discrepancies. (Although it's not that important really, I can just tell people not to log in on both at the same time.)

---

### Post by seanlano on 2012-04-03
After doing some experiments, I found that if a user is logged in through SSH the computer is inhibited from shutdown - just as it is for an actual login. This is good to know, I can have the users on the secondary PC automatically make an SSH connection to hold the primary PC from shutting down. 


I also have another query: It is easy to run commands at user login, but what about at logout? Is there a similar thing to "Startup Applications" for ending the session? 
If not, is it possible to write a script that would run at login and wait until it is requested to end by the logout process, then run an rsync command? Even if that could work, how long does logout wait before forcibly killing the running processes?

---

