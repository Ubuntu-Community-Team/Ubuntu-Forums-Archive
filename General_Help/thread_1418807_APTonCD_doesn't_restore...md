---
title: "APTonCD doesn't restore.."
date: 2010-03-01
forum: General Help
---

### Post by mishathegoat on 2010-03-01
Ubuntu Desktop (Karmic) 9.10

1. I install/run the latest version of aptoncd
2. I click RESTORE > LOAD and choose the iso and it loads just fine
3. I click the RESTORE button and it says "Preparing to copy files"
4. It says "please wait files are restored" for a few seconds and then nothing happens. It doesn't freeze or anything.. It just still shows the files that are to be restored

Output from terminal:

```

mobile@mobile-flashdrive:~$ aptoncd
/usr/lib/python2.6/dist-packages/APTonCD/restore/restoreFromDialog.py:81: GtkWarning: gtk_tree_model_get_iter: assertion `path != NULL' failed
  result = self.window.run()
/usr/lib/python2.6/dist-packages/APTonCD/restore/restoreFromDialog.py:81: GtkWarning: gtk_list_store_set_valist: assertion `VALID_ITER (iter, list_store)' failed
  result = self.window.run()
mount point =  /tmp/aptoncd-mnt-image/
iso image =  /media/ACTIVE BOOT/aptoncd-20100228-CD1.iso
[Errno 30] Read-only file system: '/tmp/aptoncd-mnt-image/.disk/info'
True 
/usr/lib/python2.6/dist-packages/APTonCD/widgets/PackageList.py:604: DeprecationWarning: Accessed deprecated property Package.installedVersion, please see the Version class for alternatives.
  self.installed[pkgi.name] = pkgi.installedVersion
[Errno 1] Operation not permitted: '/tmp/aptoncd-mnt-image/'
mount point =  /tmp/aptoncd-mnt-image/
iso image =  /media/ACTIVE BOOT/aptoncd-20100228-CD1.iso
[Errno 1] Operation not permitted: '/tmp/aptoncd-mnt-image/'
umount: /media/ACTIVE BOOT/aptoncd-20100228-CD1.iso: not mounted[Errno 30] Read-only file system: '/tmp/aptoncd-mnt-image/.disk/info'


```


EDIT:
Instead of restoring through the aptoncd program, i mounted the iso myself and navigated to the "packages" directory where I ran:

```
sudo dpkg --install *deb
```

and everything installed fine

---

### Post by Barriehie on 2010-03-07
Perhaps mark the thread solved for the next user! 8)

---

