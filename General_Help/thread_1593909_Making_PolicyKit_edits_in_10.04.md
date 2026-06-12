---
title: "Making PolicyKit edits in 10.04"
date: 2010-10-11
forum: General Help
---

### Post by beastrace91 on 2010-10-11
I am trying to make the edit referenced on [this page]("http://code.google.com/p/e17mods/wiki/Places"). But obviously it is for an older Ubuntu version because the /etc/PolicyKit/PolicyKit.conf file does not exist on my 10.04 system.

How do I go about making this edit for however 10.04 handles PolicyKit calls now?

It details I should be replacing a line that looks like ```
<match action="org.freedesktop.hal.storage.mount-removable">
```

With 

```
<match action="org.freedesktop.hal.storage.*">
```

Any ideas where I would find such a line?

Regards,
~Jeff Hoogland

---

### Post by sisco311 on 2010-10-11
The polikit documentation is very good:
[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)
[http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html](http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html)

But, if memory serves, in 10.04, by default, you should be able to mount internal volumes without password authentication.

I may be wrong; check the /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla file.

---

### Post by Johnny B on 2010-10-11
"policies are stored as xml files in /usr/share/polkit-1/actions."

  [http://ubuntuforums.org/showpost.php?p=8219205&postcount=5]("http://ubuntuforums.org/showpost.php?p=8219205&postcount=5")

---

### Post by sisco311 on 2010-10-11
> **Johnny B said:**
> "policies are stored as xml files in /usr/share/polkit-1/actions."

  [http://ubuntuforums.org/showpost.php?p=8219205&postcount=5]("http://ubuntuforums.org/showpost.php?p=8219205&postcount=5")

True, but if you want to overwrite system wide policies, in a proper way, you have to create .pkla file(s) in /var/lib/polkit-1/localauthority/50-local.d/

---

### Post by beastrace91 on 2010-10-11
> **sisco311 said:**
>  if memory serves, in 10.04, by default, you should be able to mount internal volumes without password authentication.


No it cannot. I will check that file and starting reading through those links, thank you.

Anyone have any ideas if there is a quick way to do exactly what I am looking to do before I spend 3 hours shifting through manuals?

EDIT/Update: There is no **/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla** file on my system and running a find command did not yield anything. Should this be there by default?

~Jeff

---

### Post by beastrace91 on 2010-10-11
Ok, so I installed the **policykit-desktop-privileges** package and it created the missing file - however I cannot get it configured so it will let my default user mount the internal partitions! Here is what my entry looks like at the moment

```
[Mounting, checking, etc. of internal drives]
Identity=unix-user:*;unix-user:jeff
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*;org.freedesktop.hal.storage.*
ResultActive=yes
```

I tried unix-user:* and unix-user:jeff (my user name) and neither work. Any ideas what I am doing wrong here still?

~Jeff Hoogland

---

