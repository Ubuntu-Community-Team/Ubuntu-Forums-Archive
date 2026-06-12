---
title: "FTP User login"
date: 2009-11-11
forum: General Help
---

### Post by mchilders on 2009-11-11
All,
  I setup a ftp server on my box and created a user "ftpuser" for others to use to ftp files to and from my box.  However, I don't want this user to be able to login, via SSH or the GUI.  I changed the shell for ftpuser to /bin/false, but ftpuser is still allowed to login to GNOME.  Is there anyway I can prevent this account from logging into the GUI as well as remove it's name from the user list when logging on?

I'm wondering if I need to modify the user id number to something below 1000, since there are lots of other accounts with uid's below 1000 that don't show up in the userlist.

Thanks for any help,
Matt

---

### Post by lswb on 2009-11-11
Your correct about using a UID of less than 1000. 

Many ftp servers can be configured when installed to allow anonymous login for file up/download without having to manually create new groups. You may want to check the docs for the ftp server you are using and see what they say about this.

---

