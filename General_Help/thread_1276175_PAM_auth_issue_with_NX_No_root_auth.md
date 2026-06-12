---
title: "PAM auth issue with NX: No root auth"
date: 2009-09-26
forum: General Help
---

### Post by the_squircle on 2009-09-26
Hi everyone,

I'm having a problem with GNOME and PAM over NX. When I am logged in through an NX session, I am unable to authorize as root (i.e. the 'Authorize' button is greyed-out in the Users and Groups dialog box etc.). I had fixed this problem a long time ago; somebody in IRC provided me with an answer, and it had something to do with PAM and I believe it had to do with editing SELinux settings or the gconf settings. If anybody could help, that would be great.

EDIT: If I remember correctly, it was something under the System -> Authorizations menu. It had something to do with PolicyKit.

Thanks in advance!

---

### Post by the_squircle on 2009-09-26
I solved this thanks to somebody helpful in IRC who finally read my question.

For people's reference, logged in **locally[B], go to System -> Authorizations (or remotely, run sudo polkit-gnome-authorizations) and under org > freekdesktop > systemtoolsbackends, press Edit and set Manage System Configuration to [B]Allow Authorization**, and everything will work.

---

