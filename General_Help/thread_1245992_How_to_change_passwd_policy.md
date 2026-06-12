---
title: "How to change passwd policy?"
date: 2009-08-21
forum: General Help
---

### Post by t0p on 2009-08-21
I want to replace my ubuntu password with a blank field <Enter>.  But passwd won't let me - the sorry exchange goes something like this:

```
t0p@machine:~$ passwd
Changing password for t0p.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
No password supplied
Enter new UNIX password: 
Retype new UNIX password: 
No password supplied
Enter new UNIX password: 
Retype new UNIX password: 
No password supplied
passwd: Authentication token manipulation error
passwd: password unchanged
t0p@machine:~$ 

```

I know about the security issues.  But please note: I'm not a n00b.  The computer in question is not connected to a network, nor does it hold important data.  Now, I am aware there is no *technical* reason for preventing me from having a <Enter> password.  This is down to a "good password policy" in the passwd command.  Can someone please tell me where this policy is fixed, so I can go mess with it?

---

### Post by louieb on 2009-08-21
This should work on any account? I've only used it on non-admin users. [HowTo: Create a Passwordless / Guest Login (Simple Method) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=513820")

---

### Post by t0p on 2009-08-21
Thanks louieb, that worked a treat!  On my main (admin) account too!

---

