---
title: "Juniper's installNC.sh and my root password..."
date: 2009-11-12
forum: General Help
---

### Post by samuraitor on 2009-11-12
Hi there,

I have been struggling to install juniper's installNC.sh to use my uni's wireless network. When I have to install the installNC.sh , I need to authorise this by typing me root password. After typing my root password, it says that it is incorrect and keeps asking me again and again.

How do I go about fixing this?

---

### Post by beastrace91 on 2009-11-12
Enter the correct root password (by default this will be the same as your user password)?

Does the password you are entering work when you try to run something else as super user? Also are you running the install file with sudo or as your normal user?

Regards,
~Jeff

---

### Post by samuraitor on 2009-11-12
> **beastrace91 said:**
> Enter the correct root password (by default this will be the same as your user password)?

Does the password you are entering work when you try to run something else as super user? Also are you running the install file with sudo or as your normal user?

Regards,
~Jeff

ok, I tried logging in as "su" in terminal however  the authentication failed.


What package should I download to fix this_?

EDIT: I changed my password from X to Y. I was able to login as su in terminal. I also tried installing the crappy Juniper installNC.sh with the new root password, IT WORKED:d

---

