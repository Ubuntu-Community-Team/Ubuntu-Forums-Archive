---
title: "missing hdd space prob. rsync problem"
date: 2010-10-10
forum: General Help
---

### Post by robert76 on 2010-10-10
So to do a long story short i did an update from 9.04 to 10.0 it went. Before the update i did an rsync on the vidoe libary i put the backup in /backup. when i was ready with the update i deleted the folder /backup(stupied i now) the problem is that the files seems to be gone but the space they occupied is still there. I did a scan of all the folders and had a total of 129 gb(320 gb disk) so somewhere in the / i have lost abotut 190 gb. 
[http://pastebin.com/qghfN4Vg](http://pastebin.com/qghfN4Vg)
this is a ls -all

---

### Post by dcstar on 2010-10-10
> **robert76 said:**
> So to do a long story short i did an update from 9.04 to 10.0 it went. Before the update i did an rsync on the vidoe libary i put the backup in /backup. when i was ready with the update i deleted the folder /backup(stupied i now) the problem is that the files seems to be gone but the space they occupied is still there. I did a scan of all the folders and had a total of 129 gb(320 gb disk) so somewhere in the / i have lost abotut 190 gb. 
[http://pastebin.com/qghfN4Vg](http://pastebin.com/qghfN4Vg)
this is a ls -all

They may be in the root Trash folder:
```

/.Trash-0/files
```

If you are lucky, you may be able to access them with:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

### Post by robert76 on 2010-10-10
thx a lot david u solved my problem i looked in the roots trash folder and there everything was. thx a lot again. 
it was to easy ;)

---

