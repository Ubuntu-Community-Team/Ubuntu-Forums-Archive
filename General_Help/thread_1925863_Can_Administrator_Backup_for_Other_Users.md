---
title: "Can Administrator Backup for Other Users?"
date: 2012-02-15
forum: General Help
---

### Post by 2CV67 on 2012-02-15
I have been using Grsync to backup my home folder.
Since adding another user (family) Grsync now throws up a bunch of errors for that other user like:
```
rsync: opendir "/home/family/.cache" failed: Permission denied (13)
```

Sure enough, I don't have permission to access all the files concerned.

I don't want to get used to living with Grsync error messages, so I suppose I could just not backup the family files, but if I wanted to, is it possible?

---

### Post by Azdour on 2012-02-15
Hi,

I'm assuming you are running sudo rsync?

While I do not use rsync, I use tar and have seen similar permission issues. In my case it was due to files that where still opened by an application. The .gvfs directory is also a common example if a user was logged in at the time of the backup.

Maybe something is using that users .cache directory at the time or does this happen all the time?

---

### Post by aeiah on 2012-02-15
you should be fine if you run grsync under sudo. sudo doesn't just do admin, by the way.. you could launch grsync using your family username. better still, you could add yourself to your family group and then run things as normal from your user account.

---

### Post by 2CV67 on 2012-02-15
Thanks for the comments & suggestions so far!

I don't know how to run Grsync as sudo - I am 100% GUI & don't see any options for that.
I don't think anything is using all the files which throw up errors.
Family is a new account which has only just been created, has nothing in it yet, and has not been visited since the last reboot.

I added myself to Family group (& added family to my group...) but still get the errors.

These are the errors I get every time I try now:

```
rsync: opendir "/home/family/.cache" failed: Permission denied (13)
rsync: opendir "/home/family/.config" failed: Permission denied (13)
rsync: opendir "/home/family/.dbus" failed: Permission denied (13)
rsync: opendir "/home/family/.gconf" failed: Permission denied (13)
rsync: opendir "/home/family/.gnome2" failed: Permission denied (13)
rsync: opendir "/home/family/.gvfs" failed: Permission denied (13)
rsync: opendir "/home/family/.mission-control" failed: Permission denied (13)
rsync: opendir "/home/family/.pki" failed: Permission denied (13)
rsync: opendir "/home/family/.pulse" failed: Permission denied (13)
rsync: send_files failed to open "/home/family/.ICEauthority": Permission denied (13)
rsync: send_files failed to open "/home/family/.Xauthority": Permission denied (13)
rsync: send_files failed to open "/home/family/.esd_auth": Permission denied (13)
rsync: send_files failed to open "/home/family/.pulse-cookie": Permission denied (13)
rsync: send_files failed to open "/home/family/.xsession-errors": Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
Rsync process exit status: 23

```

Trying to open any of those folders normally (not as administrator) in Nautilus or PCmanFM results in refusal & they have no permissions for Group, only Owner.

---

### Post by Azdour on 2012-02-15
Hi,

If .gvfs is locked to the family user (e.g. rwx------) then adding yourself to the family group will not help.

Is your user account and the family user the only accounts on the computer? If so hopefully someone else can tell you how to open grsync with gksudo and see if that solves your problem.

---

### Post by 2CV67 on 2012-02-17
OK - I removed my blindfold & saw the light!

Grsync > Extra Options > Run as superuser

:oops:

To iron out the last wrinkles, I needed to specify the full path to my exclusions file when running as root.

---

