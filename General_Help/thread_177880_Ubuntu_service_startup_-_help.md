---
title: "Ubuntu service startup - help?"
date: 2006-05-17
forum: General Help
---

### Post by DevSolar on 2006-05-17
Hi there,

I am currently giving Ubuntu a try after using Gentoo for quite some time. First impression is good, but I've got some problems regarding the way Ubuntu starts its services.

I use a local Subversion repository for development. I'd like to have "svnserve -d -r /var/svn" executed on bootup. On Gentoo, I would have said "rc-update add svnserve default", or added the svnserve call to /etc/init.d/local.start, but it seems to be a bit more difficult with Ubuntu. You have to know what each runlevel is for (something I never figured out), and in which order the scripts are to be executed... confusing.

Is there a good resource / tutorial / how-to on the Ubuntu way of service starting? I don't like going trial-and-error with Linux internals...

---

### Post by DevSolar on 2006-05-18
*bump*

---

### Post by fbg111 on 2006-05-19
Looking for same info, just found this thread, which might help you:

[http://www.ubuntuforums.org/showthread.php?t=89491]("http://www.ubuntuforums.org/showthread.php?t=89491")

---

### Post by fbg111 on 2006-05-19
I just discovered something else, the services admin gui (sudo services-admin, or from the System->Administration->Services menu), is supposed to be a lot more capable than it is.  According to the Ubuntu system docs (System->Help->System Documentation-->Search 'services-admin'), this tool should provide the ability to select which services start at boot, in what order, and under what runlevel(s).  But it has apparently been seriously neutered (in Dapper F7 at least), and can only start/stop services immediately.  For example, I want to disable GDM from auto-starting, so in the Services Admin gui I uncheck the GDM option.  But that shuts down GDM immediately, then automatically restarts it.  WTH?  Ubuntu's runlevels are a bit complicated for noobs, isn't there at least a command-line option for doing this stuff?

---

### Post by Jason_25 on 2006-05-19
Make a simble bash script, make it executable and place it in init.d. Then
```

sudo update-rc.d nameofscript defaults

```
To make it run at boot.

---

