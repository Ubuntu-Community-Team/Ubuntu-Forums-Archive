---
title: "Setting Up Suexec :: Reasons, How Does it Work, and How Do I Configure It?"
date: 2011-08-05
forum: General Help
---

### Post by own3mall on 2011-08-05
My web server does not currently run Suexec.  All files within the /var/www directory are owned by vsftpd and belong to nogroup.  Apparently, this setup causes issues with some scripts that attempt to upload files and change files, such as the SMF Forum package.

Here's some background information that goes into further details regarding the issues I'm having:

[http://www.simplemachines.org/community/index.php?topic=444665.0](http://www.simplemachines.org/community/index.php?topic=444665.0)

Why would uploading a file using PHP in SMF not work with the owner being vsftpd belonging to the nogroup when the folder has been chmod to 777?  I tested my own simple PHP upload script, and it was able to upload a file without issues.  Yet, I've been told that my server is improperly configured if I'm not using Suexec.  Why is this?

Also, if I did use Suexec, what creates the users?  Would I have to add them manually, or would they be created automatically as users based on their FTP login and added as subusers to the vsftpd group?

Why should I use Suexec?  I don't understand what's wrong with my current setup.  How does it work in terms of users?  Are users created and just added to a subgroup, or are they created like normal user accounts on the actual server?  Do they get their own /home/username directory as well?  I'm so confused about Suexec.  What I've read about it doesn't make sense.

Should I install SUexec or not?  Is this a good guide to follow?  [http://www.server-world.info/en/note?os=Ubuntu_10.04&p=httpd&f=8](http://www.server-world.info/en/note?os=Ubuntu_10.04&p=httpd&f=8)

Any help would be greatly appreciated.  :KS

---

### Post by own3mall on 2011-08-06
Anyone?

---

