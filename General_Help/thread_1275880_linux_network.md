---
title: "linux network"
date: 2009-09-26
forum: General Help
---

### Post by superluigi1 on 2009-09-26
I am trying to create a all Linux network for my home. I would like to be able to have all user information, and documents on a server, and allow any user to log on with any computer in the house. I am new to Linux and i am open to any suggestions. 


thank you

---

### Post by egalvan on 2009-09-26
One easy way is LTSP (Linux Terminal Server Project), using a server and thin clients... very low cost...

googling "ltsp ubuntu"popped this up..

[http://shibuvarkala.blogspot.com/2009/05/howto-install-ltsp-in-ubuntu-904-jaunty.html](http://shibuvarkala.blogspot.com/2009/05/howto-install-ltsp-in-ubuntu-904-jaunty.html)

which led to this..

[http://brainstorms.in/?p=438](http://brainstorms.in/?p=438)


also, edubuntu (Educational Ubuntu, an official Ubuntu distro) is set up for this...
it's main use is in a school setting, running a server with work-stations/thin-clients for the students...

[http://edubuntu.org/](http://edubuntu.org/)

[https://help.ubuntu.com/community/EdubuntuDocumentation](https://help.ubuntu.com/community/EdubuntuDocumentation)

/EdubuntuCookbook?action=show&redirect=EdubuntuRecipes


Thin clients can be extremely cheap, since they do not need hard drives, or much RAM (256M is plenty),
 or much "horsepower" (P-III/Athlon or low-end P-IV/AthlonXP).
As long as they have PXE-enabled network interface, you are set.

---

### Post by superluigi1 on 2009-09-26
I was looking for something more domain server like, my computers are more powerful then thin client computers.

Is there any setup similar to a windows server and xp machines, but with all Linux?

---

### Post by egalvan on 2009-09-26
> **superluigi1 said:**
> I was looking for something more **domain server** like, my computers are more powerful then thin client computers.

Is there any setup similar to a **windows server** and xp machines, but with all Linux?

First, I have no experience with Windows Server, so I won't comment on that aspect.

Second, wanting something in the 'domain' area implies more than an absolute beginner.

Server Platforms 
Networking & Wireless

are two other sub-forums here that may have more advanced help.


Note, there ARE "beginner's" oriented guides to domain server stuff, and ldap, and authentication, etc.
Hopefully others will chime in on this.

---

