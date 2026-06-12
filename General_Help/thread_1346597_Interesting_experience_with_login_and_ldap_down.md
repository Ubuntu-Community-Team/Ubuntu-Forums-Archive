---
title: "Interesting experience with login and ldap down"
date: 2009-12-05
forum: General Help
---

### Post by lil_elvis2000 on 2009-12-05
I just had a very interesting experience. One that will teach me a lesson.

Last night I scheduled a reboot of one of my servers. This just happened to the main NAS and LDAP server as well. So on the other servers I shutdown all unecessary services that use the NAS for storage and scheduled others (like e-mail) to stop and restart around the reboot.

Came in this morning. There was a problem during the reboot as it decided to do a fsck and there were issues which required a manual fsck. So I did all that and then issued a reboot. It hung up on the NFS Services and Utilities for a very long time. It does that on booting as well...obviously an issue in there somewhere.

Once that server rebooted fine I logged int the e-mail server to check and make sure no mail was lost. I used a local account and got past the authentication ok. the login script seemed to be okay. but I couldn't get a prompt! I tried a ssh from another machine and same thing! I ended up rebooting that machine via a ctrl-alt-del from the keyboard.

Bizarre really. I'm not sure what the issue is. Whether the LDAP had to do with it...I'm gonna take it down one day and test. or whether the e-mail server had locked up a process or a directory.
The local user does belong to some LDAP groups so wonder if that had something..though my nsswitch.conf is standard files ldap. and I double checked all the pam and ldap.conf. all looks good.

NAS server is 9.04 and e-mail server is 8.04 LTS

Anyone had anything similar?

The NFS Services and Utilities part of the boot takes forever. Any ideas how I can debug that. its slow on boot and shutdown on both machines.

Thanks.

---

