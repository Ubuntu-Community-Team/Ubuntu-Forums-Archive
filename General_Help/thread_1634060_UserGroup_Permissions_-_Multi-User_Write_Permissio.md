---
title: "User/Group Permissions - Multi-User Write Permission in one /home Directory"
date: 2010-11-30
forum: General Help
---

### Post by dbsoundman on 2010-11-30
I'm sort of confused here...

I've set up an Ubuntu Server 10.04.1 machine as an HTTP/FTP server. I made one FTP account which I plan on sharing with others, mainly for read access only. So, I created a local user account, called "signaltraffic", and added my username "dan" to the "signaltraffic" group. I also changed the permissions on /home/signaltraffic to be 775 so that I can create files and folders. However, I'm finding that even with these measures in place I cannot directly create files or folders in that directory without sudo. HOWEVER, if I connect as "dan" via SFTP, I can create folders and files in the signaltraffic HOME directory with no issues. What exactly is going on here, and how do I straighten it out?

Thanks,
Dan

EDIT: apparently I also removed myself from the sudo group too?! I had to add myself to the sudoers file to get that back. What did I do?

---

