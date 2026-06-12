---
title: "User accounts and groups not listed in account admin tool"
date: 2010-05-07
forum: General Help
---

### Post by rmeske on 2010-05-07
I recently ran into a situation where the ftp user account suddenly could not login.  I used the User and Groups system tool to check the user account and reset the password.  I then attempted to use ftp and login with the new password and still could not.  

I then went to check the permissions on the folder and found that the system partition was full, so using gpartd I was able to resize the system partition.  However this still did not fix the ftp login problem.

When I opened the User and Groups tool again, all users,including my main account, except root are no longer displayed and all groups are not showing.  If I try to add the original ftpuser account I get the message that the user already exists.  And my main account works for login still.  If I add a new user, it is not displayed in the list either.

If I do a cat /etc/passwd I see all the users listed including the new one I created and cat /etc/group displays all the groups and everything looks like the users are still associated with the correct groups.  

I can use passwd to change the account password without error and I can use adduser to add another user.  Howerver no users are listed in the User and Groups tool and users still can not login to ftp.

I can reinstall proftp if needed but I would like to be able to use the User and Groups tool to administer users again.

PS:  Forgot that just before encountering the ftp login problem, Update Manager and some updates listed that I attempted to install but got an error and didn't have time to check why.  Now I know that the partition was full.

---

### Post by rmeske on 2010-05-08
After doing some more searching I found a thread about users and groups not displaying.  Though I wasn't doing an update, it appears that when you run out of room on the system partition and you attempt to edit a user or group the login.defs file is corrupted.

> **em3raldxiii said:**
> It appears that something during the update (or some other action) has broken the program that creates entries in your /etc/login.defs file. The Users & Groups application checks this file for the minimum and maximum User ID numbers and then displays accordingly.

The values in mine were set to min and max being 0, which of course is why I could not see any users in my list. It seems a popular minimum number is 999, and a popular max is anywhere from 2000 to 60000. I set mine to be min 999 and max 1200. After saving this file and re-opening Users and Groups, all my users show up again.

Here is a link to the existing bug report (and where I pulled my final answer from):  [http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg374791.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg374791.html)

So in summary:

1.  Close your Users & Groups program.
2.  Open a terminal (Applications > Accessories > Terminal)
3.  Type:  gksu gedit /etc/login.defs
4.  Enter your sudo password.
5.  The file should have two entries only, UID_MIN 0 and UID_MAX 0.  I changed both numbers to 999 and 1200 respectively.
6.  Save the file and close gedit.
7.  Open System > Admin > Users & Groups.  You should now see all your users.

According to the bug report, this problem should not occur in Lucid, therefor it's been marked "Triaged".

Hope that helps!!

This solved my problem.

---

