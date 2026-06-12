---
title: "Default file permissions in Gnome"
date: 2006-05-15
forum: General Help
---

### Post by jleino on 2006-05-15
Hi All!

I have setup an NFS server where multiple users store files and work
with them (belong to the same group). The default file permission
with Gnome causes some headache to me.

I have set chmod g+s bit for the folder, thus all new subfolders are ok.
However the file permissions are not ok. I would like the new files to
have group wr bits set so that other people in the same group could also
access/edit the files. Of course the permissions could be set manually for,
eacj file but that is not very easy to explain and would be easily forgotten.

I surft the web a little bit and found out at least the following tips that
didn't help:

* Install pam_umask and add
session    optional     pam_umask.so umask=002
to /etc/pam.d/common-session

* remove umask settings from /etc/login.defs and /etc/profile

* add umask setting to /etc/gdm/Xsession

* remove # USERGROUPS_ENAB yes

* remove umask settings in ~/.bash*

Isn't this something that should be easily configurable or otherwise obvious
or am I perhaps missing something? Sometime this Linux/Gnome thing gets
irritating, I think this kind of shared directory setup should be basic and easy
stuff to implement!

All help is highly appreciated!

-- Juha

---

