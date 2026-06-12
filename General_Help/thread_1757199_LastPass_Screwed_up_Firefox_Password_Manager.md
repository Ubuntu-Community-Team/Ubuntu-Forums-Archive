---
title: "LastPass Screwed up Firefox Password Manager"
date: 2011-05-13
forum: General Help
---

### Post by rez182 on 2011-05-13
i use the default firefox password manager and sync. after i installed lastpass password manager, and later uninstalled it, the default firefox pass manager is not working. all the passwords are saved but not auto filling. i tried sudo apt-get remove firefox, and then reinstalled it, but all my previous passwords and setting are already stored as if it was never deleted. 

the reason for this to happen is, while installing lastpass, there was an option which disabled the default password manager with lastpass. how can i re-activate it? or atleast do a fresh installation where everything will be deleted in firefox and reinstall firefox 4 and use the sync to get my pass and bookmarks back.

thanks

---

### Post by rez182 on 2011-05-13
okay weird, for some reason, its working now. hasn't been working for few past hours. although i would still like to know, in future if i come across a problem like this, how can i completely remove firefox from my ubuntu, including all the setting.

thanks...

---

### Post by col48 on 2011-05-13
I've seen other posts (not for Firefox but other packages) which comment on the difference between the 'remove' and 'purge' keywords.

Remove leaves config files in place (would this include password lists in this case? I don't know).  I think this is so that a reinstall restores the status quo rather than setting up a default environment.

Purge removes the config files so that it is as if the package had never been installed.

Perhaps this is what you would need.

```
apt-get --help

```or
```
man apt-get

```

---

### Post by rez182 on 2011-05-13
thanks, i think its exactly what i was looking for...

---

### Post by lovinglinux on 2011-05-13
> **col48 said:**
> I've seen other posts (not for Firefox but other packages) which comment on the difference between the 'remove' and 'purge' keywords.

Remove leaves config files in place (would this include password lists in this case? I don't know).  I think this is so that a reinstall restores the status quo rather than setting up a default environment.

Purge removes the config files so that it is as if the package had never been installed.

Perhaps this is what you would need.

```
apt-get --help

```or
```
man apt-get

```

Purge doesn't do anything related to config files when removing Firefox, it only affects applications that store configuration files in system folders, like /etc. Firefox settings, bookmarks, extensions and passwords are stored in the user home directory, under ~/.mozilla/firefox/<profilename>.

Most likely that you would be able to restore your password manager behavior by deleting the file *prefs.js* from your Firefox profile. This would reset all Firefox settings, but wouldn't delete any password, bookmark or extensions.

---

### Post by rez182 on 2011-05-13
so how is it one can completely delete everything from ubuntu. like a complete uninstall...

---

### Post by lovinglinux on 2011-05-13
> **rez182 said:**
> so how is it one can completely delete everything from ubuntu. like a complete uninstall...

Everything?

If you delete everything starting with a dot from your home directory, you will basically start from fresh, without actually re-installing anything.

But if you want a complete re-install then simply re-install Ubuntu.

---

