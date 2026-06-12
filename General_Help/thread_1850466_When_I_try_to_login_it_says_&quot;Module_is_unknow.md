---
title: "When I try to login it says &quot;Module is unknown&quot;"
date: 2011-09-26
forum: General Help
---

### Post by HorseBox on 2011-09-26
NOTE: I fixed the problem. Check the bottom of the post for the solution. 

When I booted up my laptop this morning everything went fine until I got to the Ubuntu login screen. When I enter my username and password in then hit enter it just says "Module is unknown". Is this a problem with GNOME? I had a problem a couple of days ago because I added the GNOME3 repository which messed up things for me but I removed that package then reinstalled gnome-panel and after that it was working fine, I logged in at least 3 times without any problem. I have no idea what this "Module is unknown" problem is all about. I don't remember changing anything significant. I'm on a live Ubuntu CD now. I'm able to mount the drive that Ubuntu is installed on. Any idea why I can't log in anymore?

EDIT: I solved the problem. I booted a live Ubuntu CD and mounted the  drive that Ubuntu is installed on. I chrooted to the mounted drive then  edited the file /etc/pam.d/gdm and changed /lib/security/pam_listfile.so  to /lib/i386-linux-gnu/security/pam_listfile.so. That solved the  problem. Heres the post I found this solution in:
[http://ubuntuforums.org/showpost.php?p=10860427&postcount=6](http://ubuntuforums.org/showpost.php?p=10860427&postcount=6)
before that I saw this thread:
[http://ubuntuforums.org/showthread.php?t=1150786](http://ubuntuforums.org/showthread.php?t=1150786)
and tried the pam_tally and pam_auth_update commands but neither worked.  I have no idea why this problem started and why changing the directory  to pam_listfile.so fixed it but it did.

---

