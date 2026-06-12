---
title: "mailutils broken in 10.04?"
date: 2010-05-10
forum: General Help
---

### Post by Altay_H on 2010-05-10
I installed mailutils in Karmic Koala and have a number of scripts which use the following to send emails alerting me of events that require my attention:
```

echo "Body of email." | mail -s "Subject" "username@domain.com"

```

The email conveniently comes from username@computername. In Karmic Koala all I had to do was install mailutils using apt-get and everything worked perfectly. After installing Lucid Lynx I used apt-get to install mailutils, but the previously mentioned line of code doesn't work anymore. There's no error; mail executes the command as if it's working, but the email is never received. Any ideas?

---

### Post by mutrax on 2011-02-07
Sorry for reviving this old thread, but did you manage to fix the issue? I might have encountered the same, but still struggling ( [http://ubuntuforums.org/showthread.php?t=1682127](http://ubuntuforums.org/showthread.php?t=1682127) ).... Some scripts I might add to the sudoers file, but that solution isn't optimal for all my exising scripts.

---

### Post by dcstar on 2011-02-07
> **mutrax said:**
> Sorry for reviving this old thread, but did you manage to fix the issue? I might have encountered the same, but still struggling ( [http://ubuntuforums.org/showthread.php?t=1682127](http://ubuntuforums.org/showthread.php?t=1682127) ).... Some scripts I might add to the sudoers file, but that solution isn't optimal for all my exising scripts.

Install the **bsd-mailx** & **postfix** packages.

---

### Post by mutrax on 2011-02-07
> **dcstar said:**
> Install the **bsd-mailx** & **postfix** packages.

Hi,

Thanks for the reply,

but I have a lot of scripts depending on the mailutils mail synthax, plus I got a fully ( well yeah...) fetchmail / postfix / dovecot mailserver running, don't want to break anything there... I'll give it a try anyhow.

Thanks,

EDIT>
fixed... [http://ubuntuforums.org/showthread.php?t=1682127](http://ubuntuforums.org/showthread.php?t=1682127)

---

