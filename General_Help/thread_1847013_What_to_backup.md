---
title: "What to backup?"
date: 2011-09-20
forum: General Help
---

### Post by polardude1983 on 2011-09-20
Ok so I am going to explain on what I backup and then try to see what I need to still backup.

Story: I have my /home on its own partition sdb3. I also backup my /home to an external drive.

Well one day I reinstalled my OS sda1 and pointed the /home to my sdb3 partition.

So when I started the OS all my files were there, but then it seemed like none of my apps were installed. So i asked and somebody said I have to reinstall the apps again. Found out that the hard way. So now I am trying to backup my installed apps with this

```
dpkg --get-selections > /backup/installed-software.log
```

I backup this log to my external drive. So hopefully that will fix that problem of having to reinstall apps

But then when I reinstalled my OS it seemed that part of my wallpaper theme was missing. What do i have to backup so that will all be there next time?

---

### Post by dcstar on 2011-09-20
> **polardude1983 said:**
> Ok so I am going to explain on what I backup and then try to see what I need to still backup.

Story: I have my /home on its own partition sdb3. I also backup my /home to an external drive.

Well one day I reinstalled my OS sda1 and pointed the /home to my sdb3 partition.

So when I started the OS all my files were there, but then it seemed like none of my apps were installed. So i asked and somebody said I have to reinstall the apps again. Found out that the hard way. So now I am trying to backup my installed apps with this

```
dpkg --get-selections > /backup/installed-software.log
```

I backup this log to my external drive. So hopefully that will fix that problem of having to reinstall apps

But then when I reinstalled my OS it seemed that part of my wallpaper theme was missing. What do i have to backup so that will all be there next time?

There is no need to use the command line to save the installed program list, Synaptic has this built in and you can use the saved file to restore the list for subsequent package installation.

If you are reinstalling the same version then just about everything should be there as before, if you are installing a newer release then some things may not be exactly as before because of differences that did not get processed in an upgrade process.

If you have made changes to /etc configuration files on the old system then you may want to back them up as well and use them in the new system (but make sure you keep the original new files).

---

### Post by polardude1983 on 2011-09-20
What about backing up thmemes, sources? and all that other fun stuff?

---

