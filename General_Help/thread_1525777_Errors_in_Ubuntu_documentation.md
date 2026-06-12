---
title: "Errors in Ubuntu documentation"
date: 2010-07-07
forum: General Help
---

### Post by Leppie on 2010-07-07
i was browsing through the documention, and found the following section:
>                        Finally, restart the **samba**  services to enable the new configuration:                       ```
sudo /etc/init.d/samba restart
```however, afaik samba is now an upstart job and can no longer be controlled through init.d (at least i don't have the samba script in my /etc/init.d/). the correct command should be:
```
sudo service smbd restart
```

---

### Post by plucky on 2010-07-07
Please post a link for the documentation you refer to.

Does it still not apply for earlier versions that are still supported?

Not everyone has upgraded to Lucid.

---

### Post by Leppie on 2010-07-07
sorry, i forgot to specify that this is the Lucid documentation.
[https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html)
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html)
[https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ad-integration.html)
[https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)

---

### Post by plucky on 2010-07-07
Documentation bug reported [Here](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/575540)

---

