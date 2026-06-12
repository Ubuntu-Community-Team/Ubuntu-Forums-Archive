---
title: "Public Folder advice?"
date: 2010-09-03
forum: General Help
---

### Post by gemorgan on 2010-09-03
Hey all,

I want to set up a public folder that most of the users on the system can access. I want all files there to be read/writeable by the users that have access to that folder. I created a folder in /home to store this stuff since it's a separate partition and persists through upgrades and reinstalls. I created a group with the same name as the folder and added the users to that group and set the group owner and write permissions to that folder to be writeable by that group. Problem is that the files one user creates are not writeable by other users.

How is this kinda thing done normally?

Thanks!

---

### Post by hwttdz on 2010-09-03
If you want new files created by users to be world writable, the users are going to want to change their umask value, you can read a bit about how this sort of thing works here: [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

So the important bit is to have 0 for both the read and write field.  Though this is also going to make their files in their ~'s world writable, which some might not want.  So it seems easier to just change the permissions when they make a new file.  Or make a cronjob by someone with permissions run to chmod all files in that directory to the desired value.

---

### Post by gemorgan on 2010-09-04
Thanks,

That's kinda what I thought. I don't want the permissions altered for the users for any other folders except this one so it looks like a quick cron job is the way to go. I can simply add it to the back up script...

Thanks!

---

