---
title: "run firefox with root permissions"
date: 2010-11-27
forum: General Help
---

### Post by ereallstaff on 2010-11-27
Hi I have the following trouble. 

I use netbeanse as a development suite, but to edit/save file correctly it should run with root permissions.

When I do run file or debug them, it launches firefox, but due netbeans have been opened by root user, it tries to open firefox as root also, and it seems to be something that should not do.

Either I now upgraded to ubuntu 9.10 karmic koala and sudo firefox does not work anymore, giving me no errors even from CLI.

Any help? 

Thanks to everybody!

---

### Post by 3rdalbum on 2010-11-27
Why does Netbeans need to be run as root? You shouldn't be directly editing the files sitting in your /var/www folder - you should edit copies in your home directory as normal user, and then copy them to the privileged location as root.

You should never try to do 'sudo firefox' - it ruins the permissions on your Firefox profile. You may be able to correct these permissions and bring them back to your normal user account; the firefox preferences are in ~/.mozilla/firefox.

---

