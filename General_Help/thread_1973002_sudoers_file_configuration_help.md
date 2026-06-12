---
title: "sudoers file configuration help"
date: 2012-05-04
forum: General Help
---

### Post by bergamot on 2012-05-04
I'm trying to configure the /etc/sudoers file to allow a non-administrative user access to certain applications, namely the Update Manager and Ubuntu Software Centre.

I configure the file as follows. The host's name is 'ubuntu', 'luser' is the administrative user and 'mark' is the one I want to grant the necessary privileges to.

```
Defaults	env_reset
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
root	ALL=(ALL:ALL) ALL
mark ubuntu=(ALL)NOPASSWD:/usr/bin/software-center,/usr/bin/update-manager
%admin ALL=(ALL) ALL
%sudo	ALL=(ALL:ALL) ALL
```

As you can see, the file contains the default config plus my 1 extra line. 

If you log in as user 'mark' and run ```
sudo update-manager
``` or ```
sudo software-center
```, I am able to run these with the expected privileges. However, if I run the applications from the Unity menus or dash, it doesn't run with elevated privilege and asks for authentication. It won't accept the password for the 'mark' user but it will accept the password for 'luser' which is the one I used when I installed Ubuntu. 

I can't figure out what else I need to do, to make sudo work for the graphical interface. Can anyone help me out?

Thanks

---

### Post by SuaSwe on 2012-05-04
Hi bergamot,

To clarify, are you logged onto the graphical interface (e.g. at startup or by selecting "switch user") as 'mark' when testing this? If you are logged on as luser it will only accept those details (far as I know anyway!). 

Cheers!

Emma

---

### Post by bergamot on 2012-05-04
Hi Emma

Yes, logged in as 'mark' from lightdm, using Unity. Direct login, not from Switch User Account.

I should mention also that 'mark' is an LDAP user. 

But I had this kind of thing working in Ubuntu 10.04, so I don't think that should make a difference.

Thanks,
Mark

---

### Post by bergamot on 2012-05-15
I've tried 10.04 again, and the same thing happens as with 12.04.

I can run 'sudo update-manager' from the command line and it gets the root privilege, but when I run update manager from the menus it asks for a password, and it's not the password of the currently logged in user, but the one that originally installed the machine.

I'm wondering how Ubuntu's security is set up so that it works in this way. I haven't been able to work it out for myself.

It's been a week since my last post, so I'm losing hope of getting any help with this, but if someone does wish to offer any assistance, I'd be grateful.

---

### Post by matt_symes on 2012-05-15
Hi

This really is a total stab in the dark but have you checked out policy kit policies ? Maybe that will help. 

I have never attempted what you are trying to do so, like i said, a total stab in the dark. It may not even be possible.

Kind regards

---

### Post by bergamot on 2012-05-15
Thanks for the suggestion. I don't know anything about policy kit but I'll have an RTFM and see if it's relevant..

---

