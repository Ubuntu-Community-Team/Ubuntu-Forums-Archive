---
title: "Assign group access automatically at login to active directory domain admins group"
date: 2009-08-15
forum: General Help
---

### Post by Matty-uk on 2009-08-15
I have been trying to figure out how to assign the domain admins group from active directory automatic group access at user login.

My system is configured as follows.
* Likewise Open5 Installed and domain joined using GUI
        /etc/likewise-open5/lsassd.conf updated to allow single sign on
                 Changed  # assume-default-domain = yes to assume-default-domain = yes
        see more details at http:\\help.ubuntu.com/9.04/serverguide/C/likewise-open.html
* Sudo rights updated using visudo
        Added - %DOMAINNAME.CO.UK\\domain^admins ALL=(ALL) ALL
        Added - DOMAINNAME\\ad^username ALL=(ALL) ALL
* Active Directory Users added to Local Group Automatically
        /etc/security/group.conf updated to asign local groups
                 sudo gedit /etc/security/group.conf
                        Added - *;*;*;Al0000-2400;floppy,video,audio,cdrom,plugdev,users,scanner
	/etc/pam.d/common-auth updated to enable pam to enable above
                 sudo gedit /etc/pam.d/common-auth
                        Added - auth required pam_group.so use_first_pass
        See more details at [http://ubuntuforums.org/showthread.php?t=929940](http://ubuntuforums.org/showthread.php?t=929940)
* Active directory users added to local linux groups individual as needed
        sudo gedit /etc/group updated to include additional users
                 Added - ad^username,otherad^username,etc to the following groups
                              adm, dialout, cdrom, plugdev, lpadmin, admin,	

I understand that all a domain admin needs to do is sudo and update /etc/group and include themselves in the relevant groups and reboot.  The whole point is i want to figure out how to do it automatically.

Can anyone give me any pointers?

Thanks

Matty-uk

---

### Post by bchurchill on 2009-08-15
I'm not quite sure I understand what you're trying to do.  It sounds like you have two groups, A and B, and you want to add every member of group A to group B, but only when members of group A log in.

If you can install a script to run when a user from group A logs in, then you could do something like:

```

$ME=`whoami`
usermod -a -G groupB $ME
[CODE]

but this would need to run at root privileges for usermod to work.  If you wanted to assign all the users of group A to group B that would be easier: just use grep to extract the users from the appropriate line of /etc/group, and then pipe the output into [CODE]xargs -n1 usermod -a -G groupB
```.

---

### Post by Matty-uk on 2009-08-16
Will try and explain it a bit better.

**Standard Active directory Users**
Active Directory UserA logs in to the machine and they are automatically added to the floppy, video, audio, cdrom, plugdev, users, scanner groups.

**Standard Active directory Users with full rights to machine**
Active Directory UserB logs in to the machine and they are automatically added to the floppy, video, audio, cdrom, plugdev, users, scanner groups.  An admin has also manually added this user to these Linux groups; adm, dialout, lpadmin, admin.  The user has also been granted sudo rights.

**Domain Admin Active directory User**
Active Directory UserAdminA logs in to the machine and they are automatically added to the floppy, video, audio, cdrom, plugdev, users, scanner groups.  The user is automattically granted sudo right.  [COLOR="Magenta"]They have to sudo /etc/group and add themself to adm, dialout, lpadmin, admin Linux groups and reboot.[/COLOR]

I'm happy with how Standard Active directory Users and Standard Active directory Users with full rights to machine works.  I would like to automate the part I&#8217;ve highlighted if possible.

---

### Post by pwebster25 on 2010-10-12
I know this is an old thread.  Hopefully someone is still there.  If I edit /etc/group and want to add a domain user, how do I put their username?

Is it DOMAIN\username or just username or DOMAIN\\username (because the first \ cancels out)?

I have put in DOMAIN\username but I don't think it works, as it still gives me warnings about not being in the lpadmin group.

---

### Post by Matty-uk on 2010-10-13
Hi, you don't add any reference to the domain.  

For example;
DOMAIN\username would be just username
DOMAIN\user name would be just user^name

---

