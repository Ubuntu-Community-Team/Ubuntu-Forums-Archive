---
title: "Login"
date: 2009-09-15
forum: General Help
---

### Post by TobiasV on 2009-09-15
Whenever I try to login (provided that my password is correct), Ubuntu briefly shows a screen (which shows that the network manager etc. are loading), then goes back to the login screen. If I provide a false username or password, it tells me so.

I'm running Ubuntu 9.04 on a Virtualbox on top of Windows Vista. 

It's a clean install that has followed these two guides:

   [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
   
  [https://help.ubuntu.com/community/Samba/Kerberos](https://help.ubuntu.com/community/Samba/Kerberos)
  
The same thing happens when I try to login to the terminal (through alt+ctrl+1).

Edit: I fixed the problem, it was happening because I had made a typo in one of my lines in /etc/pam.d/common-auth .

---

