---
title: "Disable .cache/motd.legal-displayed in Lucid"
date: 2010-06-16
forum: General Help
---

### Post by dbrossard on 2010-06-16
Everytime a user logs in via ssh either interactive or non-interactive (sftp) a directory is created in their home directory called .cache and a file is created in that directory called "motd.legal-displayed". I do not want this, particularly with my chrooted sftp users. I have searched in /etc/defaults/*, /etc/pam.d/* and even all of /etc/* to try and find where this is being created but have come up empty. How do I disable this?
Thanks in Advance.

---

### Post by wojox on 2010-06-16
Look in */etc/update-motd.d*

Also:

```
man update-motd
```

---

### Post by Tobu on 2010-06-22
Here is the offending code:

[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/lucid/pam/lucid-proposed/annotate/head:/debian/patches-applied/pam_motd-legal-notice](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/lucid/pam/lucid-proposed/annotate/head:/debian/patches-applied/pam_motd-legal-notice)

It annoys me, as this creates cruft in some system accounts.

---

### Post by ygoe on 2010-11-06
So how can I disable the creation of that file now? I'd disable the whole MOTD thing alltogether as well if that's necessary, I absolutely don't need it. I've read all the files in the above mentioned directory and the manpage, but it doesn't tell me how the creation of that file in other users' home directory can be prevented.

---

### Post by Tobu on 2010-11-08
This will disable it:

```
sudo sed -ri 's/^session[[:space:]]+optional[[:space:]]+pam_motd\.so$/#\0/' /etc/pam.d/login   

```

---

### Post by ygoe on 2010-11-08
Thank you, I've commented out that line on my system. When will it take effect? Do I have to restart some service or the whole system?

---

### Post by ygoe on 2010-11-14
Thank you not so much... This change has absolutely no effect, even after a system reboot. Are there other working solutions?

---

