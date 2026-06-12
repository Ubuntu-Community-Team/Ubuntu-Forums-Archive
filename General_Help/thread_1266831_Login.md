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

Edit: It was working yesterday, the last session I was logged on, I didn't change anything, I just turned off the computer.

When I turned it on today, this was going on. I've tried with both my local and my Active Directory user.

---

### Post by rocket16 on 2009-09-15
Why don't you install Ubuntu using Wubi or in seperate Partition? I am telling so, because see, that whenever you use VirtualBox, the total RAM of your PC is shared between Ubuntu and Windows, making the performence of both, lesser than actually anticipated! So, install them seperately.

---

### Post by autra on 2009-09-15
Seems that your server X is crashing... ?
Might be related to the trouble I have (cf the thread I posted 10 min ago)

Which packages did you updated recently ? (Synaptic --> file --> history)

---

