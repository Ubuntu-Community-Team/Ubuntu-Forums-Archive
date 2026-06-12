---
title: "auto update does not work"
date: 2010-06-01
forum: General Help
---

### Post by B3rt on 2010-06-01
Hi,

I am using lucid 64bit ubuntu and it seems my auto update function does not work.

Since install (on day of release, a clean fresh install) I did not have 1 update, when I check updates manually there are updates.

If I look in /var/lib/apt/periodic there are 2 files on root and 0kb in size:
totaal 8,0K
drwxr-xr-x 2 root root 4,0K 2010-05-01 11:26 .
drwxr-xr-x 6 root root 4,0K 2010-06-01 13:40 ..
-rw-r--r-- 1 root root    0 2010-06-01 11:55 update-stamp
-rw-r--r-- 1 root root    0 2010-06-01 13:41 update-success-stamp

Is this normal?

Is there a fix to get auto update to work?

---

### Post by rnerwein on 2010-06-01
hi
i guess you have configured your updates "silent". that means don't ask but do an update.
i get the same system and i was ask for updates 3 times since installation.
ciao

---

### Post by dino99 on 2010-06-01
it should work if update-notifier is installed and "automatic download" chosen into synaptic config

---

### Post by pricetech on 2010-06-01
I have the same problem with both 64 and 32 bit Lucid.  Someone suggested I file a bug report, which I attempted, but since I don't use my ISP based email and mail clients don't work well with web based, I wasn't successful.

Sorry, I don't have a solution or even a workaround except to keep an eye on it, which is what I'm doing.

---

### Post by B3rt on 2010-06-01
> **dino99 said:**
> it should work if update-notifier is installed and "automatic download" chosen into synaptic config

It is but it does not update.
When I check manually updates are available and can be installed.

@rnerwein
no silent install is not activated.

---

### Post by dino99 on 2010-06-01
> **B3rt said:**
> It is but it does not update.
When I check manually updates are available and can be installed.

@rnerwein
no silent install is not activated.

remove/purge then reinstall update-notifier

and into a console: metacity --replace

you can clean the system too using gconf-cleaner (yes to all)

---

