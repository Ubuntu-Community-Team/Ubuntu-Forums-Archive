---
title: "Firefox unable to create folders"
date: 2011-06-23
forum: General Help
---

### Post by akwatve on 2011-06-23
Hi,

I am facing a weird problem. When I try to create a folder from firefox (while downloading stuff), it says "unable to create folder. permission denied." But when I create it using terminal (i.e. 'mkdir foo') it works.

Firefox is running as the same user as the terminal, so shouldn't the two programs have the same permissions ?

I am not sure why is firefox making my OS unhappy :-(

Any help will be greatly appreciated.

Thanks,

---

### Post by akwatve on 2011-06-23
UPDATE :

I changed folder permissions to 777 but still no use :-(

---

### Post by lovinglinux on 2011-06-24
If you are trying to create a folder on a separate hard drive, it might be the AppArmor profile limiting permissions. See [AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906") tutorial. Put Firefox in complain mode and try again.

---

### Post by akwatve on 2011-06-24
Thanks for the tip. This definitely looks like an apparmor issue.
When I shutdown apparmor daemon, I was able to create the folders.
I haven't been able to configure apparmor to allow my download folder.

---

### Post by akwatve on 2011-06-24
Thanks lovinglinux
Finally reconfigured apparmor to allow access to certain folders.
It's a pretty neat application.

Just for documentation purpose :

I inserted following line in /etc/apparmor.d/usr.bin.firefox, in the section where it configures user's personal files:
```
/foo/bar/MyDownloads/** rw
```

---

### Post by lovinglinux on 2011-06-24
> **akwatve said:**
> Thanks lovinglinux
Finally reconfigured apparmor to allow access to certain folders.
It's a pretty neat application.

Just for documentation purpose :

I inserted following line in /etc/apparmor.d/usr.bin.firefox, in the section where it configures user's personal files:
```
/foo/bar/MyDownloads/** rw
```

You are welcome.

---

