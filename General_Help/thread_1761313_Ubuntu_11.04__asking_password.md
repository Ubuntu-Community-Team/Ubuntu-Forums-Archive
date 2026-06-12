---
title: "Ubuntu 11.04  asking password"
date: 2011-05-18
forum: General Help
---

### Post by losi on 2011-05-18
Hi, 
I installed the 11.04 and after a while I get a window that asking password; Enter password keyring "Default" to unlock. 
I installed more time and at installation asked only one password. 
I gave it but when I write in the mentioned window the same password it is falsh. 
1. from where can get this password?
2 How can eliminate to come this message? 
Thanks a lot.
losi

---

### Post by scottstensland on 2011-05-18
[http://superuser.com/questions/43132/enter-password-for-default-keyring-to-unlock](http://superuser.com/questions/43132/enter-password-for-default-keyring-to-unlock)

will address the password prompt you mentioned - there are
various other methods to eliminate ALL other password prompts if desired

here is another cut N paste (tho still needs a way to harden across boots)
    ---

    How to prevent system applications (like the Software Center) from asking for password ?

        Edit /usr/share/polkit-1/actions/org.debian.apt.policy,
        search for org.debian.apt.install-or-remove-packages,
        then find for the defaults section,
        replace auth_admin and auth_admin_keep with yes

take care - Scott Stensland

---

### Post by losi on 2011-05-18
Hi scottstensland,
Thanks a lot. 
This solve the problem. (and save me too)
losi

---

