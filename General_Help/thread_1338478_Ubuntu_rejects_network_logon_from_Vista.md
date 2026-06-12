---
title: "Ubuntu rejects network logon from Vista"
date: 2009-11-26
forum: General Help
---

### Post by jcobban on 2009-11-26
I recently added a laptop running Windows Vista to my network.  When I view the network either from Vista or from my Ubuntu desktop the two systems appear.  On Ubuntu I am running an explicit Samba server, although that was not required to network with my previous Win98 laptop.  From Ubuntu I can mount directories from the Vista system, but when I try to connect to the Ubuntu desktop from the Vista system the logon is rejected.

I believe the problem is actually on the Vista side, which insists upon changing the userid that I enter from "jcobban" to "jcobban-Laptop\jcobban".  I cannot see any relevant solutions in the tutorial information that I find on the web.  Do I have to define a userid of "jcobban-Laptop\jcobban" on the Ubuntu side?

---

### Post by wirelessmonkey on 2009-12-02
I believe you need to set up a samba user/pass, which can be identical to your system user/pass, using smbpasswd.   Make sure and man smbpasswd.

---

### Post by jcobban on 2009-12-03
> **wirelessmonkey said:**
> I believe you need to set up a samba user/pass, which can be identical to your system user/pass, using smbpasswd.   Make sure and man smbpasswd.

Thank you.

Now I am just back to my usual problem which is that the Windows system cannot see the SMB server at all, and the Linux system cannot see the Laptop, and nothing I try can get the two to wake up and talk to each other!  Until they do I cannot see whether invoking smbpasswd has changes anything!

SMB is a piece of odoriferous excrement!!!@

---

