---
title: "Updating from 5.10 to Dapper"
date: 2006-05-23
forum: General Help
---

### Post by jonah1980 on 2006-05-23
Hi guys, i just placed my shipit cd order for Dapper.

I'm new to linux and running Ubuntu Breezy at the mo.

I was hoping that when the new cds arrive i can boot the installation cd and simply choose to update my current system to Dapper?

Is this possible like it is with Suse etc?

I hope so as it took a techie ages in the forums to get my wireless card working etc and I don't want to do a clean install if i can help it.

Thanks for any feedback.

---

### Post by bluenova on 2006-05-23
I don't know about updating from the CD, but when Dapper Stable is released, synaptic will ask you if you want to upgrade over the internet.

---

### Post by confused57 on 2006-05-23
aysiu describes how in this thread, may have to hunt a little for it:

[http://ubuntuforums.org/showthread.php?t=179477](http://ubuntuforums.org/showthread.php?t=179477)

---

### Post by aysiu on 2006-05-23
Download the Dapper installer CD--do not use the live/desktop CD. Get the Text-Mode Installer CD.

Burn it. Pop it into your Ubuntu box.

Go to System > Administration > Synaptic Package Manager

Go to Edit > Add CD-ROM
Add it as a source.

Go to Settings > Repositories
Uncheck every box except the one you just added

Click Reload

Mark all upgrades

Apply Changes.

If you're not familiar with Synaptic, go here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

Adept may have a similar feature, but I'm not sure. You can also do it from the command-line ```
apt-cdrom add
```

---

