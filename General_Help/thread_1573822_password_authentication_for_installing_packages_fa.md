---
title: "password authentication for installing packages fails!!"
date: 2010-09-13
forum: General Help
---

### Post by rockager on 2010-09-13
i am unable to install any packages from kpackagekit using my admin password it says that password authentication failed.
i am able to log into my account with the same password
i am also able to use 'sudo' commands with the same password
in fact i am able to do all admin tasks except installing packages from kpackagekit
I've tried changing my password but it does not work.

---

### Post by gzarkadas on 2010-09-13
If using `sudo apt-get install <package>' works, and it is not  something that you have overlooked (such as having the wrong language  active when entering the password, or capslock pressed) then it is  either a misconfiguration in the front-end you use or a bug.

If it does not work, the message should have to do with the distribution's repository key. You then most probably missed that key - perhaps you deleted the keyring (a file) or deleted the key from inside, or changed something in the configuration files. In that case:

-- Use apt-key (type `man apt-key' to read about the options) to see what keys you have installed. Check also your (System|Administration|)Software Sources that they are correct. You may apart from the gui tool want to look at the configuration files. They are located in /etc/apt.

-- Look at the related ubuntu documentation links, they are  very detailed.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by rockager on 2010-09-23
thanks a lot!!
it worked!

---

### Post by gzarkadas on 2010-09-23
Glad to hear that; happy installations :smile:.

---

